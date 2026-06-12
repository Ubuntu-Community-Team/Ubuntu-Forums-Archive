---
title: "[SOLVED] No sound Ubuntu 7.10"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by bortolozzi on 2008-03-01
Hi all,

I've been fighting with Ubuntu for a couple of weeks with no success. There is no way I can get sound working. The funny thing is that it worked after a lot of experiments and it stopped working as soon as I reboot it.

I followed the steps described in [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), and I even tried to recompile the driver (ca0106) but I get an error message when I try to load it:

```
~$ sudo modprobe snd-ca0106 
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/ac97_bus.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Error inserting snd_ac97_codec (/lib/modules/2.6.22-14-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.22-14-generic/kernel/sound/core/snd-rawmidi.ko': No such file or directory
FATAL: Error inserting snd_ca0106 (/lib/modules/2.6.22-14-generic/kernel/sound/pci/ca0106/snd-ca0106.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

today, when I type aplay -l, I get:
```
aplay: device_list:204: no soundcards found...
```

lspci -v:
```
$ lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645 Host & Memory & AGP Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8078
        Flags: bus master, medium devsel, latency 32
        Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e7000000-e7ffffff
        Prefetchable memory behind bridge: eff00000-febfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
        Flags: bus master, medium devsel, latency 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
        Flags: medium devsel
        I/O ports at e600 [size=32]

00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at e6800000 (32-bit, non-prefetchable) [size=4K]

00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at e6000000 (32-bit, non-prefetchable) [size=4K]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 807a
        Flags: bus master, fast devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at d800 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8072
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at b800 [size=256]
        I/O ports at b400 [size=128]
        Capabilities: <access denied>

00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASUSTeK Computer Inc. Unknown device 807c
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at b000 [size=256]
        Memory at e5800000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0e.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at a800 [size=32]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 1351
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
        Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at effe0000 [disabled] [size=128K]
        Capabilities: <access denied>

```

I can see "Multimedia audio controller: Creative Labs SB Audigy LS". So, at least Ubuntu seems to be recognizing the audio card.

Any tips?

Thanks in advance,
Juliano

---

### Post by mc4man on 2008-03-01
Probably not relevant but double click the little speaker icon in the top panel. If there is a tab for switches open and uncheck Analog/Digitial output jack and see what happens

---

### Post by bortolozzi on 2008-03-10
Hi all,

I have some new information about this problem.

After spending a lot of time, I gave up on trying to fix the sound and I reinstalled Ubuntu 7.10 from scratch. Surprisingly, the sound works on Totem but it doesn't work for Amarok, as well as some other applcations as VLC or the flash plug in. I can listen to music or watch videos only on Totem.

So, as far as I can tell, it means that my sound driver is loaded but not all applications can recognize it. 

Any help is appreciated.

Thanks again
Juliano

---

### Post by bortolozzi on 2008-03-13
Problem solved!!!!!

After a couple of weeks and a complete system reinstall, sound is properly working in my Ubuntu. 

What was the problem: for some reason that I didn't know, there are some applications that use a different set o sound libraries. 

With a fresh install, Totem was working properly but VNC, mplayer and Amarok were not working. As I didn't know this in advance, and I was mainly using Amarok to test the sound, I ended up messing up the sound packages trying to make it work.

So, I reinstalled everything and started from scratch. Righ after the install, I figured out that the problem was only related to some applications, not all of them. Focusing only on Amarok, without touching the sound drivers, I finally installed the package **asoundconf **and used it to set the default sound card. And it worked!!!!

It's not the most intuitive thing I've ever seen, but it's working.

Juliano

---

