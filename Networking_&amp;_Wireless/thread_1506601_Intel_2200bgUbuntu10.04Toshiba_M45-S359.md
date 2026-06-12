---
title: "Intel 2200bg/Ubuntu10.04/Toshiba M45-S359"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by cdw on 2010-06-10
Installed 10.04 yesterday, cannot get wireless to complete connection:
wifi hosts are recognized and listed, two green dots are lit on system
panel, but blue arrow only ceses circling with the message "wireless
network disconnected"

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:27:43:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:4c:f5:07  
          inet6 addr: fe80::213:ceff:fe4c:f507/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2920 (2.9 KB)
          Interrupt:11 Base address:0xe000 Memory:b800b000-b800bfff 

lo        Link encap:Local Loopback  
 inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0

---

### Post by mhpathfinder on 2011-02-04
It's February 3rd, 2011 so I'm betting that Ubuntu 10.04 is now running your wifi just fine, after nine months of updates.

I bartered some technical help and network solutions for a friend.  He provided me with his old Toshiba M45-S359 laptop as payment. I am quite elated with its performance and speed, even with only 1 gig of RAM.  I installed Ubuntu 10.04 and everything, I mean everything, worked right "out of the box."  All hardware, network, wifi, ports---everything is fine.  I'm sure that some keyboard shortcuts are not doing what they would normally do, since the system was designed around Win XP, but I haven't found any yet.  I also installed Ubuntu 10.04's Netbook 2D ElF launcher from Synaptics Package Manager.

For a four-year-old laptop, the M45-S359 is great.  I'm upgrading the RAM to 2 gigs; the battery from a 6-cell to a 12-cell, which should provide about five hours of battery life.  I'm using Jupiter, a utility developed by FEWT, which helps control power/hardware/CPU clock speed to maximize battery life, if needed.  You can download Jupiter from Sourceforge.  It works with most netbooks and laptops.

When I received the laptop, hardware was working fine.  I originally intended to make this an Ubuntu/Windows dual boot.  I think I've been away from Windows for too long.  It seems so buggy, slow and sluggish.  It's a wonder that anyone tolerates it.  I started paring down the installed software--trial versions, annual-paid-renewal system utilities, etc.  I decided it wasn't worth the effort.  So, I wiped out the hard drive, created a / partition and a /home partition, and swap.  Installed Ubuntu 10.04.  I and will use this as a full Ubuntu system,either for myself or to put up for sale.

---

