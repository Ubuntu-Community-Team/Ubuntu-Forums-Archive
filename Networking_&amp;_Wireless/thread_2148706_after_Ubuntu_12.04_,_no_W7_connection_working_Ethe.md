---
title: "after Ubuntu 12.04 , no W7 connection working: Ethernet, WiFI, USB tethering"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by Poutrathor on 2013-05-26
Hi, 

dual boot W7/Ubuntu 12.04  on an Asus

Followed the thread below to get Ethernet working n Ubuntu (already had WiFi working): [http://ubuntuforums.org/showthread.php?t=2050126](http://ubuntuforums.org/showthread.php?t=2050126) 
Then tried to add Aircraft-ng (but stop to go work on W7/eclipse) and I had  also run the 426 updates stacked since the last time I open my Ubuntu. 

On Windows 7, no connection at all is functioning properly: no ethernet, no wifi, not even connecting my SGalaxy 3 in USB tethering. All ok in Ubuntu (from where I am writing).
I have adapters detected on Device Manager and drivers updated for my WiFi & Ethernet. 


Ever heard of this issue ? What could be wrong? Advices?

Edit: I add some results you might need to get an idea of the issue:

> [QUOTE]Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.
 
C:\Windows\system32>ipconfig
 
Windows IP Configuration
 
 
Wireless LAN adapter Wireless Network Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Ethernet adapter Local Area Connection:
 
   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::4df5:8614:ead1:decc%13
   Autoconfiguration IPv4 Address. . : 169.254.222.204
   Subnet Mask . . . . . . . . . . . : 0.0.0.0
   Default Gateway . . . . . . . . . :
 
Ethernet adapter Bluetooth Network Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter Reusable ISATAP Interface {625393FB-7615-4625-A1E5-D2E829E07185}:
 
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter isatap.{9882B06F-B920-42F5-8CCD-FA84F0AF0B18}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter isatap.{B33F93CA-AB00-4EF6-8D90-3B0B2BAC8EA6}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter isatap.{8675E6E1-F8E4-4C1A-BE17-BD0C64BB354E}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter Teredo Tunneling Pseudo-Interface:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
C:\Windows\system32>
[/QUOTE]

screenshot of device manager:

[IMG]http://imgur.com/5ajUqCh[/IMG]

Thanks for help!

Postscript: lots of karma to whoever updates things to make Asus shortcut working!

---

### Post by Poutrathor on 2013-05-27
bump.

If a guru would look at it, I would be so happy ...

---

### Post by Poutrathor on 2013-06-11
Asus Support provides me with a very simple solution, if someone meets the same issue...

He made me **restore Windows system.** 

That does not modify your windows data nor your Ubuntu/W7 dual boot. It does not work at once. The restoreation to the point saved just before I installed Atheros driver was unsuccessful, so the one before but the oldest restoration point was ok (after the 2nd try). So it is not work-the-first-time solution, but insist and Windows will end up re-configuring itself correctly.

I am still 99% sure it was the Atheros drivers in a way or the other, because of the dates. If someone successfully have them working Linux/W7, I am always interesting in hearing about.

---

