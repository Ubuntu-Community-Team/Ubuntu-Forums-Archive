---
title: "Wired connection problem, can't connect"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by tenchu77491 on 2010-06-20
Here's the story:

I haven't used Ubuntu since opened this account quite a while ago. Since that time I moved to Archlinux and I love it. I do however run lubuntu live from a USB for my work PC. I am having a problem with it. I think it's okay to post here because the core of the system is still Ubuntu. I don't think LXDE is the problem. 

I start up the live environment and it says 'wired connection connected' but I can not load any pages or do anything. 

I thought it may be a problem with configuration so I copied down (from Windows) the IP, Subnet, Gateway and DNS. I put them in manually and it doesn't say connected any more and still no connection at all. I am unsure what to do from here.  

I am not really familiar with Ubuntu enough to try much. I tried to 'dhcpcd eth0' but dhcpcd isn't installed. I guess the default Ubuntu network manager has dhcp enabled automatically. I am unsure. 

What can I do?

---

### Post by tenchu77491 on 2010-06-21
No ideas?

---

### Post by tenchu77491 on 2010-06-21
Last call for any advice, thanks for reading~

I am trying to use it at a public school computer (I am a teacher). The school network seems to be really picky, but the IP/DNS/Gateway and Subnet are all in Windows and I manually done it in lubuntu, is there another reason why it wouldn't work, and why a standard automatic DHCP wouldn't work?

---

### Post by Iowan on 2010-06-21
Once/day (24 hours) is generally considered adequate for bumping ;)

Where you put the manual entries *might* be responsible for the lack of "connected" message. Interfaces configured via */etc/network/interfaces* used to override Network Manager - maybe not-so-much now. 

Another option is to try **sudo dhclient eth0**. If it connects, but can't access internet, you can check results of * cat /etc/resolv.conf* for nameserver address(es), and **route -n** for gateway address - it should be on bottom line, with UG designator.

---

### Post by tenchu77491 on 2010-06-22
Sorry for the strange output, I had to get creative to paste it from inside the live environment without internet.




ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:13:77:86:98:e9
Sending on   LPF/eth0/00:13:77:86:98:e9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.10.101 from 192.168.10.1
DHCPREQUEST of 192.168.10.101 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.10.101 from 192.168.10.1
bound to 192.168.10.101 -- renewal in 57 seconds.
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
ubuntu@ubuntu:~$ 


It looks like this, does nothing but say connected and spin on resolving the host:

[http://img413.imageshack.us/img413/5639/201006221346211024x768s.png](http://img413.imageshack.us/img413/5639/201006221346211024x768s.png)

PS:

The numbers from route -n and the dhclient are different from those inside of Windows and the IPv4 config.

---

### Post by tenchu77491 on 2010-06-22
20 hour bump~

---

### Post by Iowan on 2010-06-22
The different subnets is kinda interesting... Your post shows router/gateway at 192.168.10.1, but the image has 192.168.0.1... Can you ping internet by IP address (74.125.95.104)?

---

### Post by tenchu77491 on 2010-06-23
```
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:13:77:86:98:e9
Sending on   LPF/eth0/00:13:77:86:98:e9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.10.100 from 192.168.10.1
DHCPREQUEST of 192.168.10.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.10.100 from 192.168.10.1
bound to 192.168.10.100 -- renewal in 50 seconds.
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
ubuntu@ubuntu:~$ ping 74.125.95.104
PING 74.125.95.104 (74.125.95.104) 56(84) bytes of data.
From 192.168.10.1 icmp_seq=1 Destination Net Unreachable
From 192.168.10.1 icmp_seq=2 Destination Net Unreachable
From 192.168.10.1 icmp_seq=4 Destination Net Unreachable
From 192.168.10.1 icmp_seq=5 Destination Net Unreachable
From 192.168.10.1 icmp_seq=6 Destination Net Unreachable
From 192.168.10.1 icmp_seq=7 Destination Net Unreachable
From 192.168.10.1 icmp_seq=8 Destination Net Unreachable
From 192.168.10.1 icmp_seq=9 Destination Net Unreachable
^C
--- 74.125.95.104 ping statistics ---
9 packets transmitted, 0 received, +8 errors, 100% packet loss, time 8003ms

ubuntu@ubuntu:~$ 

```
:confused:

---

### Post by tenchu77491 on 2010-06-23
21 hour bump =(

---

### Post by tenchu77491 on 2010-06-23
This may sound strange but I figured it out.

I did the manual connection and did the settings from Windows' ipv4 config, but usually it didn't work. This time I decided to rename the default 'auto eth0' and I renamed it to 'eth0' and it connected. 

I have no idea why the name made a difference, but it did. I guess this is solved, strangely.

---

