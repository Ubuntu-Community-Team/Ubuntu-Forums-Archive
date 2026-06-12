---
title: "Wired internet out after updates downloaded"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by Buzz Bloom on 2010-07-03
Hardware: 5 year old Compaq laptop: Presario V4000. - Intel Celeron M Processor 1.3 GHz
System: Ubuntu release 10.04 lucid - Kernel Linux 2.6.32-23 - generic - GNOME 2.30.0

Uses a wired connection through a router

SEQUENCE OF EVENTS

Friday evening - June 2, 2010

Sytem was working OK.  Downloaded Ubuntu updates.  Put laptop into Suspend mode.  Turned off master power at surge protector. 

About 4 hours later tried to Unsuspend.  Could not Unsuspend.

Pressed power button on laptop for several seconds to shutdown laptop.

Saturday morning - June 3, 2010

After Ubunto booted up, launched Firefox.  No internet access.
File-> showed "Work Offline" checked.  Unchecked it, but that didn't fix the problem.  Rebooted, and still no internet.

Tried an alternate cable (which was working with a desktop Winows XP computer) between router and laptop.  Still no internet.

Used terminal to ping the IP address of the router - ping unsuccessful.

NOTE: The router still works wired to the deskop, and also wireless to a netbook.

---

### Post by Iowan on 2010-07-03
Right-click on Network Manager and verify "Enable Networking" is checked. Some threads suggest that some updates disable it...

---

### Post by nautica17 on 2010-07-03
Try doing this. Go to terminal and type in:
sudo ifconfig eth0 192.168.1.100 up
, where the last numbers can be between 1-255. Usually I would use 100 or something that is free on your network. 
Then type exactly:
sudo route add default gw 192.168.1.1

I had a similar problem before and this fixed it for me, at least temporarily. Try and see if this at least makes your connection work.

---

### Post by Buzz Bloom on 2010-07-04
My thanks to Iowan for promptly solving my problem.

---

### Post by Buzz Bloom on 2010-07-04
My thanks to nautica17 also for responding.

---

