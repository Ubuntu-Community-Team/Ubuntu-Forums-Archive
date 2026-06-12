---
title: "F6D1103 BelkinN750 Help"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by Skullxbagel on 2012-09-15
EDIT: Not F6D1103, its F9L1103


Hey everyone,
I just went out and bought a belkin N750 for ubuntu, I thought it might work, I heard all Ralink chips were built into ubuntu, but apparently not. So I got ndiswrapper and installed the XP drivers that came with install disk, and..... it doesn't work.
```
chris@chris-p7-1054:~$ ndiswrapper -l
rt2870 : driver installed
    device (050D:1103) present
chris@chris-p7-1054:~$ 

``````
chris@chris-p7-1054:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 050d:1103 Belkin Components 
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 04ca:003a Lite-On Technology Corp. 
Bus 003 Device 002: ID 046d:c245 Logitech, Inc. 

```So, I was just wondering if this is working for anyone. Should I try the newer driver files on the disks? I thought xp driver files were preffered for ndiswrapper but if anyone thinks it'll make a difference I'll try.

---

