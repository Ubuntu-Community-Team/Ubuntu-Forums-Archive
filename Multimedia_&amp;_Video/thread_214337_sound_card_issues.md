---
title: "sound card issues"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by foxhound_oki on 2006-07-12
hi there.... im am having a fustrated time getting ubuntu to work with my sound card. i dj and i perfer to use ubuntu over windows to do my job. i installed the cd about two months ago and found that the sound wasn't working. it gave me the error that i don't have the sound card installed or drivers inplace when you click the sound icon on the desktop. i have gone throught the steps of this guide in the sticky threads and still not working. here is my output from the first few steps. could someone help me please.

sean@foxubuntu1:~$ aplay -l
aplay: device_list:218: no soundcards found...
sean@foxubuntu1:~$ lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
Flags: bus master, medium devsel, latency 64
Memory at f8000000 (32-bit, prefetchable) [size=64M]
Capabilities: <available only to root>

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro13 3x AGP] (prog-if 00 [Normal decode])
Flags: bus master, 66MHz, medium devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: fca00000-feafffff
Prefetchable memory behind bridge: e4800000-e48fffff

0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 06)
Subsystem: VIA Technologies, Inc. VT82C596/A/B PCI to ISA Bridge
Flags: bus master, stepping, medium devsel, latency 0

0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
Flags: bus master, medium devsel, latency 64
I/O ports at ffa0 [size=16]

0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 02) (prog-if 00 [UHCI])
Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
Flags: bus master, medium devsel, latency 64, IRQ 9
I/O ports at e800 [size=32]

0000:00:07.3 Bridge: VIA Technologies, Inc. VT82C596 Power Management
Flags: medium devsel

0000:00:12.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Ra deon 7500] (prog-if 00 [VGA])
Subsystem: C.P. Technology Co. Ltd RV200 QW [Radeon 7500 PCI Dual Displa y]
Flags: bus master, stepping, medium devsel, latency 64, IRQ 11
Memory at f0000000 (32-bit, prefetchable) [size=128M]
I/O ports at ee00 [size=256]
Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
Expansion ROM at febc0000 [disabled] [size=128K]
Capabilities: <available only to root>

0000:00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. RT8139
Flags: bus master, medium devsel, latency 64, IRQ 10
I/O ports at ea00 [size=256]
Memory at febeff00 (32-bit, non-prefetchable) [size=256]
Expansion ROM at febb0000 [disabled] [size=64K]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (re v 7a) (prog-if 00 [VGA])
Flags: bus master, stepping, medium devsel, latency 0
Memory at fd000000 (32-bit, non-prefetchable) [disabled] [size=16M]
I/O ports at <ignored> [disabled]
Memory at fca00000 (32-bit, non-prefetchable) [disabled] [size=4K]
Expansion ROM at fffe0000 [disabled] [size=128K]
Capabilities: <available only to root>

sean@foxubuntu1:~$ sudo modprobe snd-via82xx
WARNING: Error inserting snd_ac97_bus (/lib/modules/2.6.12-10-386/kernel/sound/p ci/ac97/snd-ac97-bus.ko): Invalid module format

please, someone help me.

---

