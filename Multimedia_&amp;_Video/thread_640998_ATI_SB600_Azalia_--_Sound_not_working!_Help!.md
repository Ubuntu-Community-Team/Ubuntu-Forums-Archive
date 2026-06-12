---
title: "ATI SB600 Azalia -- Sound not working! Help!"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by mlucian72 on 2007-12-14
I'm using Feisty on a Toshiba laptop, and I can't get the sound to work at all. I am very new to linux, but I'm trying to learn. This sound card is listed as ATI SB600 Azalia, and I have the sound control working (volume,etc.) but there is no sound from the speakers, and is not muted.
 Here is the lspci output:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7916
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791f
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

 Does anyone know how to get this to work? I know there are problems with sound in Gutsy, this is why I've installed Feisty, I hope I can get it to work with this distro.
 Any help will be greatly appreciated!!!

   Thanks in advance!

---

### Post by TuxLove on 2007-12-19
I had the same problem with this card. Here's how I fixed it...

[http://ubuntuforums.org/showthread.php?p=3983746#post3983746](http://ubuntuforums.org/showthread.php?p=3983746#post3983746)

:guitar:

---

