---
title: "DNS not working."
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by dmitriyap on 2010-11-14
I'am using static IP configuration for my home NAS, running Ubuntu server 9.04 and I'am having trouble with dns resolve. While all configurations seems to be fine, it's fail to resolve any dns name.

Here is my /etc/resolv.conf:
```
nameserver 208.67.222.222
nameserver 208.67.220.220

```
I'am able to ping those IPs:
```
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=58 time=324 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=58 time=241 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=58 time=263 ms
```

But:
```
dima@nas:~$ nslookup www.google.com
;; connection timed out; no servers could be reached
```
Or:
```
dima@nas:~$ ping www.google.com
ping: unknown host www.google.com
```

Any ideas what's wrong?

---

### Post by uncaspi on 2010-11-14
Chose network icon upper right panel and choose Edit connections and tab ipv4... and put in the google nameserver 8.8.8.8

---

### Post by dmitriyap on 2010-11-14
> **uncaspi said:**
> Chose network icon upper right panel and choose Edit connections and tab ipv4... and put in the google nameserver 8.8.8.8

As i've mentioned in my first post i'am using ubuntu sever, so there is no GUI (no upper right panel), just ssh access.
And I've tried Google DNS, they aren't working too.

---

### Post by coffee412 on 2010-11-14
> **dmitriyap said:**
> I'am using static IP configuration for my home NAS, running Ubuntu server 9.04 and I'am having trouble with dns resolve. While all configurations seems to be fine, it's fail to resolve any dns name.

Here is my /etc/resolv.conf:
```
nameserver 208.67.222.222
nameserver 208.67.220.220

```I'am able to ping those IPs:
```
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=58 time=324 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=58 time=241 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=58 time=263 ms
```But:
```
dima@nas:~$ nslookup www.google.com
;; connection timed out; no servers could be reached
```Or:
```
dima@nas:~$ ping www.google.com
ping: unknown host www.google.com
```Any ideas what's wrong?

Before you do anything, List your routing tables. Also check your firewall to see if its blocking DNS.

---

### Post by dmitriyap on 2010-11-15
Here is my netstat -rn:


```
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

Firewall not blocking DNS

---

### Post by endotherm on 2010-11-15
are you sure the firewall is not a problem? remember, dns is stateless so you need a return rule unless you are allowing all ports.

---

### Post by dmitriyap on 2010-11-15
> **endotherm said:**
> are you sure the firewall is not a problem? remember, dns is stateless so you need a return rule unless you are allowing all ports.

Could you give instruction commands to check this for me to be sure.

---

### Post by endotherm on 2010-11-15
check the output of 
```
sudo iptables --list
``` and see if you have rules applied. if you do, then you will need to confirm that you have an allow rule for udp/53 inbound.

---

### Post by dmitriyap on 2010-11-15
> **endotherm said:**
> check the output of 
```
sudo iptables --list
``` and see if you have rules applied. if you do, then you will need to confirm that you have an allow rule for udp/53 inbound.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

All the rules are empty

---

### Post by coffee412 on 2010-11-15
> **dmitriyap said:**
> ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```All the rules are empty

Im assuming that you are behind a router. Your firewall is basically turned off. Its allowing all. Reset your router and modem and then turn on the computer.

---

### Post by dmitriyap on 2010-11-15
> **coffee412 said:**
> Im assuming that you are behind a router. Your firewall is basically turned off. Its allowing all. Reset your router and modem and then turn on the computer.

Yeah, I'am behind router. But my another laptop working pretty fine behind this router.

---

### Post by endotherm on 2010-11-15
> **dmitriyap said:**
> Yeah, I'am behind router. But my another laptop working pretty fine behind this router.
yep, the router is taking care of letting port 53 traffic back in, so you are good there. your issue does not appear to be firewalling.

---

### Post by dmitriyap on 2010-11-15
> **endotherm said:**
> yep, the router is taking care of letting port 53 traffic back in, so you are good there. your issue does not appear to be firewalling.

Solved it by setting resolv.conf to my provider DNS.

---

### Post by coffee412 on 2010-11-15
> **dmitriyap said:**
> Solved it by setting resolv.conf to my provider DNS.

Be sure to backup the resolv.conf file 

> cp resolv.conf resolv.conf.bak

After a reboot it may rewrite the file.

Good job!

---

### Post by jamesjony2 on 2010-11-15
I replaced the motherboard in my home machine and now the DNS to function correctly can not get. I have installed a new motherboard and all existing drivers .. This is usually a hardware or Windows' Internet Connection Sharing feature, as is Internet sharing software after installing the router.

---

### Post by SeijiSensei on 2010-11-16
> **dmitriyap said:**
> Solved it by setting resolv.conf to my provider DNS.

Hmm.  Wonder if they're selling request data to advertisers?  There aren't any plausible technical or security reasons for blocking requests to other DNS servers that I can think of.  Forcing you to use their servers makes me think they're exploiting the data in some way.

---

