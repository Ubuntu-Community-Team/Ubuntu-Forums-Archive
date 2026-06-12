---
title: "b43 and other problems"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by devildoc5 on 2009-06-22
ok instead of hijacking everyone elses thread I decided I would start my own thread.  I am a complete and absolute n00b here, here is a basic run down of my problems thus far:

1. I am not able to install the b43 driver and can only use the sta driver (need to install b43 for monitor mode among other things)

2. Only have wireless internet at this time, so know hard wiring for updates to wireless or anything else.

I have used the following posts and have been unable to get anything working

[http://ubuntuforums.org/showthread.php?p=7496434#post7496434](http://ubuntuforums.org/showthread.php?p=7496434#post7496434)
[http://ubuntuforums.org/showthread.php?t=1071298](http://ubuntuforums.org/showthread.php?t=1071298)

In the second thread I have the same problem as the OP however I can not seem to get b43-fwcutter working properly.  It keeps coming up with "invalid file" or "invalid md5" errors.  



Also on a side note my conky shutsdown suddenly at (seemingly) random times.

Any help with this issue would be greatly appreciated.  BTW I am running Jaunty 9.04

---

### Post by ugm6hr on 2009-06-22
Try this: [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

But replace the Intrepid packjage with this one: [http://packages.ubuntu.com/jaunty/utils/b43-fwcutter](http://packages.ubuntu.com/jaunty/utils/b43-fwcutter)

Make sure you disable the STA / wl driver.

---

### Post by Ayuthia on 2009-06-22
> **devildoc5 said:**
> ok instead of hijacking everyone elses thread I decided I would start my own thread.  I am a complete and absolute n00b here, here is a basic run down of my problems thus far:

1. I am not able to install the b43 driver and can only use the sta driver (need to install b43 for monitor mode among other things)

2. Only have wireless internet at this time, so know hard wiring for updates to wireless or anything else.

I have used the following posts and have been unable to get anything working

[http://ubuntuforums.org/showthread.php?p=7496434#post7496434](http://ubuntuforums.org/showthread.php?p=7496434#post7496434)
[http://ubuntuforums.org/showthread.php?t=1071298](http://ubuntuforums.org/showthread.php?t=1071298)

In the second thread I have the same problem as the OP however I can not seem to get b43-fwcutter working properly.  It keeps coming up with "invalid file" or "invalid md5" errors.  



Also on a side note my conky shutsdown suddenly at (seemingly) random times.

Any help with this issue would be greatly appreciated.  BTW I am running Jaunty 9.04

From the first link that you provided, kevdog and I would like to know what wireless card you are using.  Can you post the results of lspci -nn?

Also, the link that ugm6hr provided, it is a guide to get the b43 module working without an internet connection.  That will work also.

---

### Post by devildoc5 on 2009-06-23
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)


Have not tired the link provided but will give it a shot here in a minute and let you know what happens.  Thanks for the help so far.

---

