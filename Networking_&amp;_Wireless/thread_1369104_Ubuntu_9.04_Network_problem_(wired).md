---
title: "Ubuntu 9.04 Network problem (wired)"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by tbear2 on 2009-12-31
[FONT=Arial]Hello to All![/FONT]
  [FONT=Arial]I am new to Ubuntu.[/FONT]
  [FONT=Arial]I have installed Ubuntu 9.04 in a dual boot with Windows 2000 Pro on an old machine with a K7S5A MB[/FONT][FONT=Arial] with onboard SIS 900 PCI fast internet adapter, [/FONT][FONT=Arial]1.5 Athlon XP, 1Gig RAM.[/FONT]
  [FONT=Arial]Ubuntu 9.04 (or maybe Network Manager) doesn’t locate the network / router (Linksys WRT54G).[/FONT]
  [FONT=Arial]I have looked around the net for solutions, but not much luck.[/FONT]
  
  [FONT=Arial]More info:[/FONT]
  “ifconfig”
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0 
            inet6 addr: ::1/128 Scope:Host 
            UP LOOPBACK RUNNING  MTU:16436  Metric:1 
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:0 
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 
     
  “ifup”: failed to open statefile /var/run/network/ifstate: Permission denied 
   
  "sudo dhclient eth0"
  Internet Systems Consortium DHCP Client V3.1.1 
  Copyright 2004-2008 Internet Systems Consortium. 
  All rights reserved. 
  For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
   
  SIOCSIFFLAGS: Cannot assign requested address 
  SIOCSIFFLAGS: Cannot assign requested address 
  Listening on LPF/eth0/00:00:00:00:00:00 
  Sending on   LPF/eth0/00:00:00:00:00:00 
  Sending on   Socket/fallback 
  receive_packet failed on eth0: Network is down 
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
  send_packet: Network is down 
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
  send_packet: Network is down 
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
  send_packet: Network is down 
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19 
  send_packet: Network is down 
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
  send_packet: Network is down 
  DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
  send_packet: Network is down 
  No DHCPOFFERS received. 
  No working leases in persistent database - sleeping. 
  90

  "sudo gedit /etc/network/interfaces"
[INDENT]     auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet dhcp
[/INDENT]        
  Any help will be appreciated.
  Thanks!
tb2:confused:

---

### Post by Iowan on 2009-12-31
Check **sudo lshw -C network** to see if your interface is recognized, has driver, etc.

---

### Post by tbear2 on 2009-12-31
Thanks!
Here's the result...
   [SIZE=2]$ sudo lshw -c network
[/SIZE]     [SIZE=2]  *-network DISABLED      
[/SIZE]   [SIZE=2]       description: Ethernet interface
[/SIZE]   [SIZE=2]       product: SiS900 PCI Fast Ethernet
[/SIZE]   [SIZE=2]       vendor: Silicon Integrated Systems [SiS]
[/SIZE]   [SIZE=2]       physical id: 3
[/SIZE]   [SIZE=2]       bus info: pci@0000:00:03.0
[/SIZE]   [SIZE=2]       logical name: eth0
[/SIZE]   [SIZE=2]       version: 90
[/SIZE]   [SIZE=2]       size: 100MB/s
[/SIZE]   [SIZE=2]       capacity: 100MB/s
[/SIZE]   [SIZE=2]       width: 32 bits
[/SIZE]   [SIZE=2]       clock: 33MHz
[/SIZE]   [SIZE=2]       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
[/SIZE]   [SIZE=2]       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full latency=128 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
[/SIZE]     [SIZE=2]  *-network DISABLED
[/SIZE]   [SIZE=2]       description: Ethernet interface
[/SIZE]   [SIZE=2]       physical id: 1
[/SIZE]   [SIZE=2]       logical name: pan0
[/SIZE]   [SIZE=2]       serial: fa:11:51:ad:01:d7
[/SIZE]   [SIZE=2]       capabilities: ethernet physical
[/SIZE]   [SIZE=2]       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/SIZE]   
  
What next?

---

### Post by Iowan on 2009-12-31
The "send_packet: Network is down" seems a little ominous - does it work when booted into Windows? [This]("http://ubuntuforums.org/showthread.php?t=1156441") fixed my wired connection problems.

---

### Post by tbear2 on 2010-01-01
Hi Iowan,
Yes it works fine in Windows 2000 Pro (how I am connecting at the moment.)
It also works fine on Knoppix 3.7 but shows a similar problem with a Knoppix V6 CD.

I wonder if the Network Manager is looking for a wireless network instead of a wired network?

Please, any help will be appreciated.

tb2

---

### Post by tbear2 on 2010-01-01
Hi All,
[FONT=Verdana]I got to thinking about Knoppix 3.7 working and decided to do an “ifconfig” in Knoppix 3.7.  It has a whole section on eht0 that is missing when I do it in Ubuntu 9.04:[/FONT]  [FONT=Verdana] [/FONT]
  [INDENT][LEFT][FONT=Verdana]knoppix@ttyp1[knoppix]$ ifconfig[/FONT]
  
[FONT=Verdana]eth0      Link encap:Ethernet  HWaddr [/FONT][FONT=Verdana]00:00:00:00:00:00[/FONT][FONT=Verdana][/FONT]
  
[FONT=Verdana]          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT]
  
[FONT=Verdana]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT]
  
[FONT=Verdana]          RX packets:3 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  
[FONT=Verdana]          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  
[FONT=Verdana]          collisions:0 txqueuelen:1000[/FONT]
  
[FONT=Verdana]          RX bytes:1026 (1.0 KiB)  TX bytes:1274 (1.2 KiB)[/FONT]
  
[FONT=Verdana]          Interrupt:22 Base address:0xd400[/FONT]
  
[FONT=Verdana] [/FONT]
  
[FONT=Verdana]lo        Link encap:Local Loopback[/FONT]
  
[FONT=Verdana]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
  
[FONT=Verdana]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
  
[FONT=Verdana]          RX packets:8 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  
[FONT=Verdana]          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  
[FONT=Verdana]          collisions:0 txqueuelen:0[/FONT]
  
[FONT=Verdana]          RX bytes:400 (400.0 b)  TX bytes:400 (400.0 b)[/FONT][/LEFT]
[/INDENT]
[FONT=Verdana][/FONT]
  [FONT=Verdana] [/FONT]
[FONT=Verdana] [/FONT]  [FONT=Verdana]Thanks for trying to help.[/FONT]
At this point I am totally lost.
tb2
[FONT=Verdana][/FONT]
  [FONT=Courier] [/FONT]

---

### Post by tbear2 on 2010-01-02
OK!
So I decided to see what happened if I booted into Ubuntu with the network cable unplugged.

Results from ifcongfig and sudo dhclient eth0 are the same as when the cable is plugged in, so I am guessing the problem is Network Manager.

Suggestions???

Any help would be appreciated...

---

### Post by Iowan on 2010-01-02
> **tbear2 said:**
> 
```
     auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet dhcp

```        
 With eth0 defined in */etc/network/interfaces*, Network Manager usually won't touch it. You can try commenting out the two eth0 lines, save and reboot/restart.

---

### Post by tbear2 on 2010-01-02
I'll give that a try...

---

### Post by tbear2 on 2010-01-02
OK.
I commented out the two eth0 lines.
Then I did a sudo /etc/init.d/networking restart

 No change.
Tried a reboot to Ubuntu.
No change.

---

### Post by tbear2 on 2010-01-03
I downloaded Ubuntu 9.10, burned a CD, & tried it on live CD. It connected to my network, and to the Internet.

So, I un-installed Ubuntu 9.04 and installed 9.10 in a dual boot with windows and everything seems to be working again.

Thanks to everyone!  
This forum is a great resource and I am sure I will be back to learn more!

All the best, :razz:
tb2

---

