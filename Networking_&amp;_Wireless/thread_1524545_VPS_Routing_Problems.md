---
title: "VPS Routing Problems"
date: 2010-07-05
forum: Networking &amp; Wireless
---

### Post by raijinsetsu on 2010-07-05
Hey All,
I've been having troubles with a VPS service I purchased and their support is worthless.

I am trying to configure a firewall to allow access to ONLY DNS, HTTP, and SSH. I started with the Firewall functionality in their provided admin console, but it doesn't work (I think it is trying to use iptables functionality that they haven't compiled into the supplied kernel).
So, I attempted to use a simple iptables config:
$IPT = iptables
```
$IPT -F
$IPT -N SERVICES
$IPT -A SERVICES -t tcp --dport ssh -j ACCEPT
$IPT -A SERVICES -t tcp --dport http -j ACCEPT
$IPT -A SERVICES -t udp --dport domain -j ACCEPT
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A INPUT -i venet0 -j SERVICES
$IPT -A INPUT -j LOGNDROP
```

I think this is fairly simple and straight-forward. Please note that many of the iptables modules are not available to me(such as "state", "recent", etc.). Otherwise, I would add:
```
$IPT -A INPUT -i venet0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```
before SERVICES is chained to within the INPUT chain.

This set of rules is correctly limiting incoming connections from ports other than tcp:80, tcp:22, and udp:53. However, it's also somehow preventing OUTGOING connections from being made at all. And I cannot understand why.

I added a lot of additional logging for the dropped packets and this is what I got (just one sample, and edited for security):
```
Jul  5 11:49:18 kernel: Denied UDP: IN=venet0 OUT= MAC= SRC=REMOTEADDR DST=MY_IP LEN=186 TOS=0x00 PREC=0x00 TTL=61 ID=1377 PROTO=UDP SPT=53 DPT=44495 LEN=166

```
What is going on? REMOTEADDR is one of the nameservers supplied by the service provider (in this case, I think it's the VPS container that is supplying the nameservers). Why is that nameserver attempting to contact my DNS server on a random port?

Adding the following to the firewall correctly allows outgoing connections, but I have no idea why:
```
$IPT -I INPUT 2 -s REMOTEADDR -d MY_IP -j ACCEPT
```

The default action for the INPUT and OUTPUT chains is "ACCEPT".

Anyone have any ideas? Is it just me, or is this a security concern: anyone could spoof REMOTEADDR and connect to any port on MY_IP? I have an open ticket with the VPS provider, but they have never been helpful in the past (they want me to purchase their management service, which doubles the cost).

The venet0 device is the only (virtual) physical network adapter in the system. There are two aliases: venet0:0 and venet0:1 - these are assigned my external IP addresses. All of this is configured by the VPS provider.

I'm also going to research compiling the kernel modules for the iptables modules that the VPS provider did not compile into their kernel (I do not think I can recompile a stock kernel, and the OS seems to be deprived of all indications of the current kernel configuration - I cannot even do a modprobe). I really want the "recent" module so that I can maybe damper DoS attacks.

---

### Post by aos101 on 2010-07-05
> **raijinsetsu said:**
> I added a lot of additional logging for the dropped packets and this is what I got (just one sample, and edited for security):
```
Jul  5 11:49:18 kernel: Denied UDP: IN=venet0 OUT= MAC= SRC=REMOTEADDR DST=MY_IP LEN=186 TOS=0x00 PREC=0x00 TTL=61 ID=1377 PROTO=UDP SPT=53 DPT=44495 LEN=166

```
What is going on? REMOTEADDR is one of the nameservers supplied by the service provider (in this case, I think it's the VPS container that is supplying the nameservers). Why is that nameserver attempting to contact my DNS server on a random port?
I think packets like that are replies to requests your system has sent out, in this case probably a DNS request.  Notice the packet has a destination port of 44495, and your iptables rules only allow in UDP packets with a destination port of 53.  Since it doesn't match this rule it ends up matching the LOGNDROP rule, which presumably drops the packet.  

The iptables rules are blocking outgoing connections from being made because they are dropping all the return packets.  IPTables doesn't automatically understand the concept of connections, so when you send everything left over to LOGNDROP, it drops **everything** including packets involved in an outoging connection you made.

---

### Post by raijinsetsu on 2010-07-05
Yes. I've been working on this all day, and I found out the reason:
the VPS host does not have the "ipt_state" module, which is used by every firewall configuration program I've run. This even explains why the control panels firewall configuration tool was failing.
Without this module, I'll need to toggle back and forth between no access to the outside world, and allowing access to all ports.

I've update my support ticket with the company. Hopefully, they have an explanation as to why the state module isn't available.

---

