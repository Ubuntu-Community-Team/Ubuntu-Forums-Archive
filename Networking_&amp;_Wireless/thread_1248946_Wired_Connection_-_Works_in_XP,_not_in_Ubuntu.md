---
title: "Wired Connection - Works in XP, not in Ubuntu"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by herrma29 on 2009-08-24
Hello,

I just moved into my new apartment and am having some trouble getting the internet connection to work. My wired connection has no problem in XP, but when I try to connect in Ubuntu, it shows it as connected, but nothing comes up.

I am able to connect when I put the IP info from XP into Ubuntu, but I would really rather it do so automatically. XP is set to autoconfig. I am running 8.04. 

Thanks for any help!

---

### Post by Iowan on 2009-08-24
Hardy is one of the (desktop) versions I skipped, but I remember static addresses being something of a challenge.  Network Manager seemed to handle DHCP alright, though. What are results of **ifconfig -a**? If your interface has a valid (non-avahi) address, perhaps the problem is with gateway or DNS.

---

### Post by herrma29 on 2009-08-24
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:89:11:4e  
          inet6 addr: fe80::20f:b0ff:fe89:114e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46109 errors:11 dropped:11 overruns:0 frame:11
          TX packets:27742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33186204 (31.6 MB)  TX bytes:4361021 (4.1 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:b8:e3:33  
          inet addr:192.168.1.121  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:feb8:e333/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1276682 (1.2 MB)  TX bytes:122276 (119.4 KB)
          Interrupt:22 Base address:0xa000 Memory:b8006000-b8006fff 

eth0:avahi Link encap:Ethernet  HWaddr 00:0f:b0:89:11:4e  
          inet addr:169.254.4.213  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111639 (109.0 KB)  TX bytes:111639 (109.0 KB)


That is what I got from running ifconfig -a

I am currently using a wireless router, but I won't have access to it consistently. I changed the setting to my wired connection to dhcp and the wired connection option in the drop down from my network icon disappeared. Let me know what you come up with.

Thanks.

---

### Post by karthick87 on 2009-08-25
Post the output of /etc/network/interfaces file

---

### Post by abhilash82 on 2009-08-25
Use the new network manager applet.

[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)

---

### Post by herrma29 on 2009-08-25
The contents of that file is:

auto lo
iface lo inet loopback






iface eth0 inet dhcp
address 72.44.104.77
netmask 255.255.255.192
gateway 72.44.104.65

auto eth0

---

### Post by LrdOfNightmares on 2009-08-25
Hey guys, i have the same problem, but my output of /etc/network/interfaces is this

auto lo
iface lo inet loopback


nothing more.. :?

---

### Post by Iowan on 2009-08-25
> **herrma29 said:**
> 
iface eth0 inet dhcp
address 72.44.104.77
netmask 255.255.255.192
gateway 72.44.104.65

auto eth0Can't argue if it works - but that arrangement *should* confuse the machine. Perhaps it ignores the static settings when it's told to use DHCP? 
Try editing */etc/network/interfaces*, and commenting out (#) the address, netmask, and gateway lines. Restart and check **ifconfig -a** again. If no address, try **dhclient eth0** and post the results.

---

### Post by herrma29 on 2009-08-25
This is what I got from ifconfig -a after restarting. The wired connection was set to roaming:

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:89:11:4e  
          inet6 addr: fe80::20f:b0ff:fe89:114e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:280 (280.0 B)  TX bytes:468 (468.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:b8:e3:33  
          inet6 addr: fe80::212:f0ff:feb8:e333/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:3 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1796 (1.7 KB)  TX bytes:2532 (2.4 KB)
          Interrupt:22 Base address:0x8000 Memory:b8006000-b8006fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74700 (72.9 KB)  TX bytes:74700 (72.9 KB)


dhclient eth0 gave me this:

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0f:b0:89:11:4e
Sending on   LPF/eth0/00:0f:b0:89:11:4e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 72.44.104.69 from 72.44.104.65
DHCPREQUEST of 72.44.104.69 on eth0 to 255.255.255.255 port 67
DHCPACK of 72.44.104.69 from 72.44.104.65
bound to 72.44.104.69 -- renewal in 129668 seconds.


It's been a long while since I've bothered with anything mildly techie on my computer, so I really have no clue what to make of this. Thanks for the replies!

---

### Post by herrma29 on 2009-08-25
Well...something is working now. I have the wired connection set to DHCP, and it is connected to the internet. The only thing now that is quirky is the applet is showing the four bars for a wireless signal rather than the two monitors.

---

### Post by herrma29 on 2009-08-26
Well, it's back to not working again...no clue what I did.

---

