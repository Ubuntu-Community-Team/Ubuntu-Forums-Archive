---
title: "Dual nics, one connection?"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by cuddles71 on 2009-08-24
Ok folks, here's an interesting puzzle.

I'm running an ubuntu server (headless, no X) on my lan, but I'm about to get a dedicated DSL line just for it. 

So here's the setup I'd like to have:

eth0: Same as it is now, connected to my lan on DHCP, local lan access only.
eth1: Connected directly to the new DSL for internet access (web server, shoutcast server, etc).

Basically, eth1 should be for the actual internet connection, while eth0 would be for samba file sharing.

Can this be done, and if so, how?

Thanks!

---

### Post by olivesandtrees on 2009-08-24
If you don't want your LAN to have access to the internet just make sure both NICs on the server have the correct settings depending on the network they are connected to.  When setting up server programs make sure they bind to the correct NIC.

If you would like your LAN to have internet access through the server, assuming you have the IP addresses properly set for both NICs, you can make your Ubuntu system a NAT gateway.

1. Enable IP Forwarding

```
gsku gedit /etc/sysctl.conf
```

uncomment or add the following lines to the file:

```
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```

2. Configure NAT

```
gksu gedit /etc/rc.local
```

add the following lines to the file:

```
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE
```

3. Reboot

- or - make the system a proxy [http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html](http://www.ubuntugeek.com/how-to-setup-transparent-squid-proxy-server-in-ubuntu.html)

---

### Post by cuddles71 on 2009-08-24
The systems on my lan already have access to the internet through a hardware firewall. I just want to make sure that this server gets its connection to the internet through eth1 and not eth0.

---

### Post by cuddles71 on 2009-08-24
Maybe a crudely drawn graphic would help:

Primary Internet Connection --> LAN (192.168.0.xx) --> eth0 (192.168.0.9) Server --> eth1 (unknown IP yet) --> New Internet Connection

The rest of the systems on the LAN should/will still be using the primary internet connection, and accessing samba shares on that server through eth0.

That server though, for apache, shoutcast, and whatever else I put on it should be using the new internet connection coming through eth1.

So is there any way to do that?

---

### Post by paulisdead on 2009-08-24
You just need to make sure that DSL modem that's plugged into eth1 is the default route on the server.  I've not used Ubuntu server, since I normally do this sort of thing in Debian, but I'm sure if you google it, you'll find the Ubuntu way of doing it.  Under Debian, you just specify the gateway in the section for the eth1 interface in /etc/network/interfaces, and don't specify a gateway for eth0.

You could lock certain services, such as samba and ssh to only run on eth0, to be on the safe side.  You can either do it in the config files for those services, or go the /etc/hosts.allow /etc/hosts.deny route.  Iptables is another option to control what can get to what services.

---

### Post by cuddles71 on 2009-08-25
Thank you! I do believe you found exactly the answer I needed.

---

### Post by cuddles71 on 2009-08-26
Ok, DSL is installed, and tested fine on a Win XP system.

BUT, when plugged directly into the server (on eth1), I can't get an IP address at all.

```
eth1      Link encap:Ethernet  HWaddr 00:00:e8:12:96:c7
          inet6 addr: fe80::200:e8ff:fe12:96c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:600 (600.0 B)  TX bytes:10947 (10.9 KB)
          Interrupt:18 Base address:0xac00
```
Any ideas?

---

