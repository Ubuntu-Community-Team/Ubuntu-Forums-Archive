---
title: "Skype mic and sound not working toshiba m305d"
date: 2010-01-28
forum: Multimedia Software
---

### Post by rah_b11 on 2010-01-28
Hi 

i have a toshiba m305d satelite laptop
i installed ubuntu karmic 9.10 and evrything seems to be working fine including wireless and ethernet which was not working previously ..
but now with alsa my mic was not working and hence i uninstalled alsa and installes oss4 as was directed by other forums ..
however with alsa my sound was working in skype but now nothing seems to work ..
i am getting error as "problem with audio playback"
i am using skype 2.0 as 2.1 was said to be not compatible with oss4
also the sounds in my pdgin im client is not working ..

here is my component information

rahul@rahul-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


i have tried checking mic using ossrecord but dint get ne output..
i also tried sound recorder which also dint work with both alsa and oss4

now the thing is with oss4 even the speakers are not working for some applications like pdgin and skype which was working with alsa 

do nebody has a fix for it plase help

---

### Post by davyboy04 on 2010-02-19
I have the same problem.  My family live far away and likes to say hi to their grandson on skype.  If I cant get this fixed then ill have to resort to going right back to windows.  Everything else works perfectly, unfortunately this is a deal breaker for me.

---

