---
title: "I can't use ethernet on clamshell ibook?"
date: 2006-05-06
forum: Networking &amp; Wireless
---

### Post by n00bWillingToLearn on 2006-05-06
On my clamshell iBook running dapper beta2, I have, according to network-admin, successfully configured eth0 useing DHCP and set it as my default gateway yet according to connection properties (from the top panel ) I am using local loopback :confused: . Since I can only ping myself I believe connection properties that I am using local loopback. How can I figure out what is actually happening / fix it?

[edit] more info: 

I ran "ifup eth0" and it said eth0 was already configured ( as network manager had said ) and I also "ran netstat -i" to see an interface table (:confused:  the only column of which I could understand was Iface :confused: ) and it showed an interface 'lo' which I assumed to be the looback interface:?: . I then ran "sudo ifdown lo" after which I was no longer able to even ping 127.0.1.1 (localhost) but I did not get an error whereas when I try to ping any other address, like our router, I get the error "connect: Network is unreachable ". I am now thinking it may be a hardware problem / the ibook Ethernet isn't fully supported in Ubuntu. The other thing I have noticed that may be the problem is that when I set the default gateway device ( which I assume is the device Ubuntu will try to use to connect to the Internet / LAN :?: ) to eth0 in network-manager that preference does not persist and when I quit and re-open network-manager the field for default gateway device is blank again:confused: . What console application can I use to set / check the default gateway and are my assumptions correct? Thank you for any help.

---

### Post by mips on 2006-05-07
1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**

---

### Post by n00bWillingToLearn on 2006-05-09
[QUOTE=mips]1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**[/QUOTE]
ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:30:65:78:98:3C
          inet6 addr: fe80::230:65ff:fe78:983c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:1 carrier:0
          collisions:6 txqueuelen:1000
          RX bytes:64085 (62.5 KiB)  TX bytes:6624 (6.4 KiB)
          Interrupt:41 Base address:0x8c00


 lspci | grep Eth
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM)


 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


 cat /etc/resolv.conf (nothing :confused:)


cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

---

### Post by mips on 2006-05-09
Try configuring a static ip address instead of dhcp and see if it works.

---

### Post by n00bWillingToLearn on 2006-05-09
I already tried that and it still doesn't. It is very likely a hardware problem as this is a very old machine. I have also been having problems with the clock reseting every time I shut down and other anomalies like getting an error that a certain certificate is invalid because it came from the future ( being open source and generally more fun, the error then suggested that there had been a " time warp or clock problem " :). Niether OS 9 nor X are willing to even run with these clock ( and likely other ) problems wheras Ubuntu just makes jokes about them so I think I will just be happy that the machine runs at all and leave it at that ( unless someone has any idea what is wrong / how to fix it).

---

### Post by mips on 2006-05-09
Maybe ask in the Mac forum.

---

