---
title: "EliteGroup 910 - Audio problems"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by PugTheBlack on 2006-10-09
I am running Dapper Drake on a EliteGroup 910 Laptop, and I have some problems getting sound to work. 

**Specs:**

**# Core Logic** 
        Intel® 915PM(Alviso)+ ICH6-M
**# Video & Graphics**   	
	Graphic controller: NVIDIA® GeForce Go 6800 (NV42M, MXM-III) / 6600 (NV43M, MXM-II)
	PCI-Express X16
	External 128 / 256 MB DDR VRAM on VGA board
**# Audio**   	
	SPDIF out, Azalia 7.1 channel support
	Four headphone jacks support 8 channels surround sound output
	Built-in high quality 2.1 channels speaker system, with 5 drivers (high frequency*2, median frequency*2 and subwoofer *1)

To me it looks like the soundcard DOES get detected, though I am not sure whether or not it's the right one that gets detected. 

**lspci output**

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
0000:06:03.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev f0)
0000:06:05.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
0000:06:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
0000:06:06.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
0000:06:06.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:06:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)

**aplay -l output**
mariusw@wbg-mariusw:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****

mariusw@wbg-mariusw:~$ modinfo soundcore
filename:       /lib/modules/2.6.15-27-686/kernel/sound/soundcore.ko
description:    Core sound module
author:         Alan Cox
license:        GPL
alias:          char-major-14-*
vermagic:       2.6.15-27-686 SMP preempt 686 gcc-4.0
depends:
srcversion:     DD426F1CCA2CC5F060F6F92

As far as Ive been able to figure out I should be running the ALSA snd-hda-intel driver, but I cant get it to work as it should... 

Any pointers would be appreciated, I have tried to go through the comprehensive guide, but could still not get the thing to work.. 

Cheers 

Pug

---

### Post by PugTheBlack on 2006-10-10
Bumpeti bump - I know this looks like a similar problem to quite a few of the other requests on the forum, and any replies are welcome. 

-Pug

---

### Post by PugTheBlack on 2006-10-11
Only thing I can figure is if I am using the wrong driver ...

aplay -l does not show card not found... but it also shows NO output  devices... 

System - Preferences - Sound shows my card as SAA7133 ...

...

Oh well, I'll probably figure it out one of these days, but till then any hints or tips would still be appreciated :) 

-Pug

---

### Post by PugTheBlack on 2006-10-12
Tried installing Mandriva 2007 PowerPack and got the same problem there... well not exactly the same, but my Sound Card doesnt work there either :-) 

-Pug

---

### Post by PugTheBlack on 2006-10-13
Anyone? 

-Pug

---

### Post by PugTheBlack on 2006-10-14
Well I still havent gotten this thing to work - compiled the ALSA 1.0.13 drivers 

root@wbg-mariusw:/# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.13.
Compiled on Oct 14 2006 for kernel 2.6.15-27-686 (SMP).

And still no go .. 

root@wbg-mariusw:/# aplay -l
aplay: device_list:222: no soundcards found...

Posted a BUG report on the ALSA Project bugtracking system, and hope they can help me out a little bit... 

in the meantime, if you guys can come up with something - dont hesitate to let me know :-) 

-Pug

---

