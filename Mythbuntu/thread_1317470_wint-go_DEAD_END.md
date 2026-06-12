---
title: "wint-go DEAD END"
date: 2009-11-06
forum: Mythbuntu
---

### Post by iceman600 on 2009-11-06
im having a difficult time making this mythtv to work.... im a ubuntu user since the realease of hardy and ai canno t make this mythtv to work. i tried almost every distro i found and still no luck.( almost to the ppint of throwinf this old PC )

i have a wintv-go card without FM and i tried googling for almost a week now and still i cannot make it to work. I give up tho... maybe someone here can help me make this work for me.

this is my lspci -v

```
diablo@mythbuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8025
	Flags: bus master, fast devsel, latency 0
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: f3000000-f47fffff
	Prefetchable memory behind bridge: f5f00000-f7ffffff

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000b000-0000dfff
	Memory behind bridge: ea000000-f2ffffff
	Prefetchable memory behind bridge: f4800000-f5efffff

00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12) (prog-if 80 [Master])
	Subsystem: Sony Corporation Unknown device 80f0
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at a800 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 80f0
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a400 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
	Subsystem: Sony Corporation Unknown device 80f0
	Flags: medium devsel
	I/O ports at e800 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 80f0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a000 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
	Subsystem: Sony Corporation Unknown device 80e4
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e000 [size=256]
	I/O ports at e100 [size=64]

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 4003
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
	Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f6000000 (32-bit, prefetchable) [size=32M]
	[virtual] Expansion ROM at f5ff0000 [disabled] [size=64K]
	Capabilities: <access denied>

02:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f5000000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

02:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. WinTV Series
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at f4800000 (32-bit, prefetchable) [size=4K]
	Capabilities: <access denied>

02:0a.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Unknown device 0031
	Flags: bus master, medium devsel, latency 32, IRQ 9
	I/O ports at d800 [size=32]
	Memory at f2800000 (64-bit, non-prefetchable) [size=2M]
	Memory at ec000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
	Subsystem: GVC Corporation Unknown device 0401
	Flags: bus master, medium devsel, latency 32, IRQ 9
	Memory at eb800000 (32-bit, non-prefetchable) [size=256]
	I/O ports at d400 [size=8]
	I/O ports at d000 [size=256]
	Capabilities: <access denied>

02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Sony Corporation Unknown device 80ea
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at b800 [size=256]
	Memory at eb000000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 80d2
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at ea800000 (32-bit, non-prefetchable) [size=2K]
	Memory at ea000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

diablo@mythbuntu:~$ 

```

as you notice that my tuner card is access denied... 
:mad::mad::mad:

---

### Post by ian dobson on 2009-11-07
Hi,

The  "tuner card is access denied" because your not running as root.

What messages do you see in the syslog? do yo see a videoXXX device in your /dev directory?


Regards
Ian Dobson

---

### Post by Boppy3125 on 2009-11-07
You also may have some problems since I believe this card doesn't have an MPEG encoder.  This was my first card and I eventually gave up with that one and moved on to a Hauppauge PVR-150.

I think it should be able to work, but the encoding will be done by the processor.  Good luck.

---

### Post by iceman600 on 2009-11-07
ok... the first time i setup this card i just got black screen when i click watch live tv. now im having static lines just like no signal on tv. 

im a newbie in this mythbuntu and im confused about the filemanager. its not like ubuntu desktop that i can access folders on a GUI. this time im having problems where to look at the folders.

im on vacation right now so ill try to run as root when i get back.

is there a way to navigate thru filesystem im GUI mode like ubuntu desktop. where i can put video files on video folders and pictures an picture folders and so on...

thanks for the help. :D

i bought this card on ebay... it was labaled hauppauge 150. so mad when i got the wrong card.

---

