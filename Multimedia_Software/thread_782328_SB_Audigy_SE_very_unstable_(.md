---
title: "SB Audigy SE very unstable :("
date: 2008-05-04
forum: Multimedia Software
---

### Post by WalmartSniperLX on 2008-05-04
Hey everyone. I did some research on getting Audigy SE sound cards working in 8.04 and decided to get one because I heard support is getting a lot better. However I'm having some problems ever since I installed the card. Most likely it's my fault. Also, when it comes to ALSA, OSS, or any sound configuration in Linux, I'm a complete novice.

Main problems are:
1) My system seems to want to switch between my 'ATI HDA HDMI' onboard audio (or is it the HDMI chip on my Radeon HD2600 Pro?) and my Audigy SE, which prevents me from hearing any audio at all

2) I get audio when listening to music (mp3, cd) and watching videos (DVD, mpg, avi, etc) but I don't get any sound when streaming flash. Sometimes I do but it cracks and pops, and usually just stops after 10-20 seconds or so.

3) Recording. Audacity used to work perfectly fine with my onboard audio. Ever since I put the SB Audigy SE in my system, I just can't get it to record. If I select OSS as my record device in the preferences, it hangs when I click the record button.

Here's my entire lspci:

```
 00:00.0 Host bridge: ATI Technologies Inc RX780/RX790 Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV630 [Radeon HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)
03:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
03:06.0 Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)
03:07.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b) 
```

Im still trying to learn everything there is about configuring sound hardware/settings in linux.

---

