---
title: "want to check if Brooktree Corporation Bt849A Video capture (rev 11) is active"
date: 2009-04-14
forum: Multimedia Software
---

### Post by AceRimmer234 on 2009-04-14
Sorry if this has been dealt with before... but ...lol. I have the above mentioned video capture card and want to find out if it is working and actively getting a signal. I have tried a number of different capture programs. the best i can see is there is no active camera. what do I do to activate it
 Here it is in the list when I use the command "lspci"

rusty@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 20)
03:00.0 Non-VGA unclassified device: Brooktree Corporation Bt849A Video capture (rev 11)
03:01.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
03:01.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
03:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
rusty@ubuntu:~$ 
rusty@ubuntu:~$

I am new to Ubuntu and really like it... but I need to learn alot it seems... But its great

Help me if you can please ):P
Thanks

---

### Post by AceRimmer234 on 2009-04-14
You may also notice the SBlive in the list. Would love to get a lesson on getting the front panel working

Thanks:lolflag:

---

### Post by AceRimmer234 on 2009-04-14
Here is some more info from "dmesg" about the video capture card.
Note the error message in the line

[   22.806420] Linux video capture interface: v2.00
[   22.901735] bttv: driver version 0.9.17 loaded
[   22.901738] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   22.902191] bttv: Bt8xx card found (0).
[   22.902201] bttv0: can't request iomem (0x0).
[   22.902206] bttv: probe of 0000:03:00.0 failed with error -16


Help please....](*,)

---

