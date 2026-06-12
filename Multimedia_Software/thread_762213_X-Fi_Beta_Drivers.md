---
title: "X-Fi Beta Drivers"
date: 2008-04-21
forum: Multimedia Software
---

### Post by xghost on 2008-04-21
Hi,

Although I'm new to the forums I've been using linux for some time. The problem I'm having is the following.

[list]
[*]I have an X-Fi Xtreme Gamer.
[*]I installed the X-Fi Beta drivers ( XFiDrv_Linux_US-1.18 ) released April 18, 2008.
[*]I still cannot get the sound going.
[/list]

The onboard audio does work, but I wanted to get the X-Fi working, since its a pain in the rear to keep re-connecting the speakers whenever I choose to run Linux/WinXP.

I did searche around, tried many of the proposed solutions, but they didn't work for me.

Among the things I tried already are
[list]
[*]installing linux-backports-modules-generic
[*](re)installing
[list]
[*]linux-sound-base
[*]alsa-base
[*]alsa-utils
[*]installing alsa-oss
[/list]
[/list]


Some basic information that I know gets asked for a lot.

```

Script started on Sat 19 Apr 2008 02:10:29 PM AST
**xghost@ps-x:~/Desktop$ uname -a**

Linux ps-x 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

**xghost@ps-x:~/Desktop$ lspci -v**

00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev c1)

	Flags: bus master, 66MHz, fast devsel, latency 0

	Capabilities: <access denied>



00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)

	Flags: 66MHz, fast devsel



00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)

	Flags: 66MHz, fast devsel



00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)

	Flags: 66MHz, fast devsel



00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)

	Flags: bus master, 66MHz, fast devsel, latency 0



00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)

	Flags: 66MHz, fast devsel



00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)

	Flags: 66MHz, fast devsel



00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)

	Flags: 66MHz, fast devsel



00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)

	Flags: 66MHz, fast devsel



00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)

	Flags: 66MHz, fast devsel



00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)

	Flags: 66MHz, fast devsel



00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)

	Flags: 66MHz, fast devsel



00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0

	I/O behind bridge: 00007000-00007fff

	Memory behind bridge: f8000000-fbffffff

	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff

	Capabilities: <access denied>



00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2) (prog-if 00 [Normal decode])

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0

	I/O behind bridge: 00008000-00008fff

	Memory behind bridge: fdf00000-fdffffff

	Capabilities: <access denied>



00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0

	Capabilities: <access denied>



00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0



00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: 66MHz, fast devsel, IRQ 11

	I/O ports at fc00 [size=64]

	I/O ports at 1c00 [size=64]

	I/O ports at 1c80 [size=64]

	Capabilities: <access denied>



00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: 66MHz, fast devsel



00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20

	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]

	Capabilities: <access denied>



00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]

	Capabilities: <access denied>



00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1) (prog-if 8a [Master SecP PriP])

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0

	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]

	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]

	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]

	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]

	I/O ports at f000 [size=16]

	Capabilities: <access denied>



00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17

	I/O ports at 09f0 [size=8]

	I/O ports at 0bf0 [size=4]

	I/O ports at 0970 [size=8]

	I/O ports at 0b70 [size=4]

	I/O ports at dc00 [size=16]

	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

	Capabilities: <access denied>



00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18

	I/O ports at 09e0 [size=8]

	I/O ports at 0be0 [size=4]

	I/O ports at 0960 [size=8]

	I/O ports at 0b60 [size=4]

	I/O ports at c800 [size=16]

	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

	Capabilities: <access denied>



00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19

	I/O ports at c400 [size=8]

	I/O ports at c000 [size=4]

	I/O ports at bc00 [size=8]

	I/O ports at b800 [size=4]

	I/O ports at b400 [size=16]

	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

	Capabilities: <access denied>



00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])

	Flags: bus master, 66MHz, fast devsel, latency 0

	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32

	I/O behind bridge: 00009000-00009fff

	Memory behind bridge: f0000000-f7ffffff

	Capabilities: <access denied>



[b]00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

	Subsystem: ASUSTeK Computer Inc. Unknown device 81f6

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20

	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]

	Capabilities: <access denied>[/b]



00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18

	Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

	I/O ports at b000 [size=8]

	Memory at fe029000 (32-bit, non-prefetchable) [size=256]

	Memory at fe028000 (32-bit, non-prefetchable) [size=16]

	Capabilities: <access denied>



00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)

	Subsystem: ASUSTeK Computer Inc. Unknown device cb84

	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19

	Memory at fe027000 (32-bit, non-prefetchable) [size=4K]

	I/O ports at ac00 [size=8]

	Memory at fe026000 (32-bit, non-prefetchable) [size=256]

	Memory at fe025000 (32-bit, non-prefetchable) [size=16]

	Capabilities: <access denied>



00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0

	Capabilities: <access denied>



00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0

	Capabilities: <access denied>



00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])

	Flags: bus master, fast devsel, latency 0

	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0

	Capabilities: <access denied>



01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2) (prog-if 00 [VGA])

	Subsystem: XFX Pine Group Inc. Unknown device 2252

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]

	Memory at d0000000 (64-bit, prefetchable) [size=256M]

	Memory at f8000000 (64-bit, non-prefetchable) [size=32M]

	I/O ports at 7c00 [size=128]

	[virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]

	Capabilities: <access denied>



02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

	Subsystem: ASUSTeK Computer Inc. Unknown device 819f

	Flags: bus master, fast devsel, latency 0, IRQ 16

	Memory at fdfff000 (64-bit, non-prefetchable) [size=128]

	Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]

	I/O ports at 8c00 [size=128]

	Expansion ROM at fdf00000 [disabled] [size=512K]

	Capabilities: <access denied>



03:06.0 Multimedia audio controller: Creative Labs SB X-Fi

	Subsystem: Creative Labs Unknown device 0031

	Flags: bus master, medium devsel, latency 32, IRQ 10

	I/O ports at 9c00 [size=32]

	Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]

	Memory at f0000000 (64-bit, non-prefetchable) [size=64M]

	Capabilities: <access denied>



03:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])

	Subsystem: ASUSTeK Computer Inc. Unknown device 81fe

	Flags: bus master, medium devsel, latency 32, IRQ 21

	Memory at f7fff000 (32-bit, non-prefetchable) [size=2K]

	I/O ports at 9800 [size=128]

	Capabilities: <access denied>

**xghost@ps-x:~/Desktop$ aplay -l**
**** List of PLAYBACK Hardware Devices ****

card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]

  Subdevices: 1/1

  Subdevice #0: subdevice #0

**xghost@ps-x:~/Desktop$ tail -2 /proc/asound/cards **
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe020000 irq 20

**xghost@ps-x:~/Desktop$ cat /proc/asound/modules **
 0 snd_hda_intel

**xghost@ps-x:~/Desktop$ exit**

exit


Script done on Sat 19 Apr 2008 02:22:16 PM AST

```


I also tried [this](http://ubuntuforums.org/showthread.php?t=571656&highlight=oss&page=40) procedure, but no luck..


Thanks in advance for any help :popcorn:


~xghost();

---

### Post by mastermindg on 2008-06-07
If you are running Hardy, look into PulseAudio.

---

### Post by utotmeh8 on 2008-06-07
Bump...tried everything xghost has and pulseaudio.  Still no luck.  I hope they come up with stable linux drivers soon, I miss surround sound!

---

### Post by go_beep_yourself on 2008-10-08
Would you like to sign an internet petition to get creative to release better Linux drivers?

---

### Post by markbuntu on 2008-10-08
If you are having problems getting your Creative X-FI card to work you need to use OSS4 or recompile your kernel with a patched X-Fi driver: 

To get OSS4:

[http://ubuntuforums.org/showthread.php?t=780961](http://ubuntuforums.org/showthread.php?t=780961)

To recompile your kernel and apply the patch (take extreme care doing this, recompiling a kernel is serious business and can seriously break your system,  do not do this unless you are absolutely sure you know what you are doing):

[http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

OSS4 has an x-fi driver but alsa does not yet as far as I know. If you know different, let me know. I don't know if the above works with the xtreme gamer card yet. 

Creative has recently given up on writing linux drivers and released information to the alsa and oss driver teams so another petition is not going to help.

---

