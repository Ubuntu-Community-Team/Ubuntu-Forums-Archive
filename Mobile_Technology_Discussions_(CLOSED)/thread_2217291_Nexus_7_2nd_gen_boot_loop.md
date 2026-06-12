---
title: "Nexus 7 2nd gen boot loop"
date: 2014-04-16
forum: Mobile Technology Discussions (CLOSED)
---

### Post by l6griffin on 2014-04-16
I'm trying to setup a Nexus 7 Mobile 2nd Gen to dual boot. What I seem to have created is a boot loop. Boot up get as far as then four color spheres and goes no further. Holding down both power, and up/down volume buttons has no effect, lsusb shows it as a Nexus 4(?), apt-get says I already have newest version, adb says no device. Any ideas?

Larry

larry@larry-HP-2000:~$ lsusb
Bus 002 Device 002: ID 0461:4dd2 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 029: ID 18d1:4ee1 Google Inc. Nexus 4
Bus 001 Device 017: ID 19f2:1700  
Bus 001 Device 016: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 001 Device 015: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 001 Device 014: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
larry@larry-HP-2000:~$ sudo apt-get install ubuntu-device-flash
[sudo] password for larry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-device-flash is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
larry@larry-HP-2000:~$ adb reboot bootloader
error: device not found
larry@larry-HP-2000:~$

---

### Post by l6griffin on 2014-04-16
Fastboot seems to work where apt-get, adb don't. There is another problem in that one library, has the boot, system, and recovery files with the extension sig, and another with the extension img. I'll find those in the morn, for the time being I'll mark this thread solved.

Larry

---

