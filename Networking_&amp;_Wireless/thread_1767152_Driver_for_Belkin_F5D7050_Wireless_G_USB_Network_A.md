---
title: "Driver for Belkin F5D7050 Wireless G USB Network Adapter"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by themightydeity on 2011-05-25
[LEFT]Device: Belkin F5D7050 Wireless G USB Network Adapter
Version: 4xxx
   FCC ID: RAXWN4501H
System : Ubutnu 11.04 64 bit

Problem: Frequent restart on high traffic, (torrents with 70+ peers) 
this problem was also in ubuntu 10.10

Solution in Windows 7 x64:

By default windows comes with the Atheros Generic Driver(athrxusb.sys) for this device.
Even the installation file from Belkin official site has same driver(athrxusb.sys) for Windows 7 and Vista
Only solution in windos is to replace that driver with older one of Windows XP (BLKWGU64.sys)
There is slight problem in that because the older driver is not digitally signed ,so i have to use some hacks in Win7 like TESTSIGNING ON and DDISABLE_INTEGRITY_CHECKS off for boot
and install a software called ‘Driver Signature Enforcement Overrider’ and then install driver.

Failed Attempts in Ubuntu:

Blacklisted the driver from 
/etc/modprobe.d/blacklist

lsusb:
```
Bus 001 Device 010: ID 050d:705c Belkin Components F5D7050 Wireless G Adapter v4000 [Zydas ZD1211B]
```Installed the Win XP x64 (BLKWGU64.sys) driver using NDISWRAPPER

after a restart , I cannot use that driver

Then I decided to use the generic driver (athrxusb.sys) using NDISWRAPPER , after a restart i could use the driver properly and connect to the internet , but my problem was not solved , it also restarted automatically

Questions:
1. Is there any solutions to this problem , i searched whole forum but couldn't find it?

2. Why is the Windows XP driver not working but Windows 7 is working on NDISWRAPPER?

3. Everytime the device gets disconnected i cannot use it, i have to pull it out from USB and put it again , is there an alternative process possible with some codes?


I hope that i am clear enough.

[/LEFT]

---

