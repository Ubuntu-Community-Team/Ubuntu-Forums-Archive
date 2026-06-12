---
title: "Problem with high pitch noises!!! HELP PLZ"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by kbzona on 2007-04-19
Well... first of all, im totally new to the world of linux and ubuntu, and until now ive enjoyed it so far...

Ive started using edgy.. now Feisty...

Ive noticed that in Edgy and Feisty there are some high pitch noises when i move the mouse, use beryl effects.... when i use ZynaddsubFX (excelente app!!!)

Specially in the case of ZynaddsubFx.. this noises comes when i play higher notes only

Ive read these guide seeking for a possible solution but since im still a noob in this i need some help.

[http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises](http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises)

Perhaps others solutions??

thnx


PD: lspci

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
05:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
05:00.1 Display controller: ATI Technologies Inc Unknown device 712a


cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xfe02d000, irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfdeff000 irq 22


cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).

---

### Post by kbzona on 2007-04-19
well this is really really wierd....

Ive search in the forum for a similar problem. And now ive solved the noisy sounds produced by mouse, beryl effects, moving windows. What did i do is to turn down and mute everything but MAster and PCM

Anyways i still have the ZynaddsubFX problem with high pitch notes... they still give me noisy pitched noises :S

TERMINAL LOG:
ZynAddSubFX - Copyright (c) 2002-2005 Nasca Octavian Paul
Compiled: Jun 21 2006 05:51:39
This program is free software (GNU GPL v.2) and 
    it comes with ABSOLUTELY NO WARRANTY.

Try 'zynaddsubfx --help' for command-line options.
Sound Buffer Size =     256 samples
Internal latency =      5.8 ms
ADsynth Oscil.Size =    512 samples

ERROR: Cannot make a jack client (possible reasons: JACK server is not running or jackd is launched by root and zynaddsubfx by another user.).

Using OSS instead.


Maybe the problem is "Using OSS instead."???? plz help this is driving me mad

---

