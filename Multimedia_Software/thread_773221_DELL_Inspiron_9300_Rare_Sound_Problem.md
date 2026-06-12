---
title: "DELL Inspiron 9300 Rare Sound Problem"
date: 2008-04-28
forum: Multimedia Software
---

### Post by zeabuntu on 2008-04-28
A big hello to all those nice people who help us fix our problems here in this amazing forum. I updated my computer to the new version of Ubuntu 8.04 on my DELL Inspiron 9300 4 days ago. I am having a rare problem with my sound card i think it is. The built in subwoofer of my computer is always loud. When I turn the volume down, the speakers will get quiet, but the subwoofer will still have the same highest volume. Does anyone know how can I fix this problem? I thank all of u for helping me ;)

---

### Post by Glucklich on 2008-04-28
I have a link that you might be interested in. I don't know if it will help, but... here it goes:

[https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560)


A guy has a similar laptop to yours. According to him he worked it out by doing something like this:


Mario Carrión wrote on 2008-03-20: (permalink)

I've fixed the sound problem on my Dell Inspiron 1420 running Hardy and adding the following to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=dell-m26


Hope this helps you.

---

### Post by Glucklich on 2008-04-28
Write "lspci -v" (without the ") and check if you have the same soundcard. If you have i think you won't have any problem. Oh, and check about the model.

---

### Post by zeabuntu on 2008-04-28
This is all it showed me when I entered that code:

xxxxx@Xxxxxxx:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Unknown device 0189
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: dd000000-dfefffff
	Prefetchable memory behind bridge: c0000000-cfffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
	Memory behind bridge: dcf00000-dcffffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ed00 [size=256]
	I/O ports at ec40 [size=64]
	Memory at dffffe00 (32-bit, non-prefetchable) [size=512]
	Memory at dffffd00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Conexant Unknown device 5423
	Flags: medium devsel, IRQ 18
	I/O ports at ee00 [size=256]
	I/O ports at ec80 [size=128]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Dell Unknown device 0189
	Flags: medium devsel, IRQ 10
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV41.8 [GeForce Go 6800] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 019c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at de000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at dfe00000 [disabled] [size=128K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Unknown device 0189
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at dcffc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at dcf00000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00001800-000018ff
	16-bit legacy interface ports at 0001

03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at dcffb800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
	Subsystem: Dell Unknown device 0189
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at dcffb700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dcffe000 (32-bit, non-prefetchable) [size=8K]

xxxxx@Xxxxxxx:~$

---

### Post by zeabuntu on 2008-04-28
> **Glucklich said:**
> I have a link that you might be interested in. I don't know if it will help, but... here it goes:

[https://bugs.launchpad.net/ubuntu/+bug/122560](https://bugs.launchpad.net/ubuntu/+bug/122560)


A guy has a similar laptop to yours. According to him he worked it out by doing something like this:


Mario Carrión wrote on 2008-03-20: (permalink)

I've fixed the sound problem on my Dell Inspiron 1420 running Hardy and adding the following to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=dell-m26


Hope this helps you.

Thanks for that Glucklich but my computer has sound the problem is that when Turn the volume downm the front speakers will go down, but the subwoofer located right besides the battery wont go down. It will stay playing out loud.

---

### Post by bocmaxima on 2009-05-25
I am going to bump this because I am having the exact problem with my 9300. Running 9.04

Any ideas?

---

### Post by s5cressey on 2009-06-17
Hi zeabuntu,

I am also using a Inspiron 9300. If you haven't tried this yet, go under System > Preferences > Sound Preferences. Under Default Mixer Tracks, select "Intel ICH6 (Alsa mixer)" select "Master", "Master Mono", "PCM". This will allow you to control the two front speakers and the sub with the front volume controls rather than just turning the front up and down.

Hopefully your problem is this simple; if not best of luck.

---

### Post by Mr. Cthulhu on 2009-06-18
s5cressey,

I'm using an Inspiron 9300 as well, and had the issue of the volume being really loud on the lowest settings (not just from the speakers - through headphones too).  Even though it was for a slightly different issue, your fix seemed to completely repair the problem.  Thanks!

---

### Post by aaronchall on 2009-09-17
Fixed my problem too!  What does PCM mean anyways?

---

### Post by Master Cabbage on 2010-08-30
> **s5cressey said:**
> Hi zeabuntu,
 
I am also using a Inspiron 9300. If you haven't tried this yet, go under System > Preferences > Sound Preferences. Under Default Mixer Tracks, select "Intel ICH6 (Alsa mixer)" select "Master", "Master Mono", "PCM". This will allow you to control the two front speakers and the sub with the front volume controls rather than just turning the front up and down.
 
Hopefully your problem is this simple; if not best of luck.
 
I've just installed Ubuntu on my Inspiron 9300 and I have been noticing that I can't really hear the subwoofer. I adjust the volume using the front volume controls so maybe what is happening is what is described here. I will try your fix later today and see if it works!

Edit: Couldn't really find anything like that in Ubuntu 10.04. I tried playing with the Hardware settings in sound preferences, but only one option would actually make noise. Perhaps the laptop sub-woofer is working and it is just a matter of EQ settings, which RhythmBox lacks...

---

### Post by R3p1h on 2011-05-14
Hi, I was looking hard to solve this problem, I am sure you already fixed

but for the user that coming for search engine websites this is the solution

[http://ubuntuforums.org/showpost.php...47&postcount=4]("http://ubuntuforums.org/showpost.php?p=8314847&postcount=4")

work for me and I think work for anyone that have dell laptop inspiron.
I have Dell Inspiron E1705 / 9400 in ubuntu 10.4

---

