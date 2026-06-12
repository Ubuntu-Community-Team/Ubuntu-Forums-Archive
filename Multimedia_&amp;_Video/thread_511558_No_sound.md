---
title: "No sound"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by cablejimmy on 2007-07-27
I have no sound. I have no idea what to do about it.

```
cablejimmy@Calebs:~$ sudo lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 746 Host (rev 10)
        Subsystem: ASRock Incorporation Unknown device 0746
        Flags: bus master, medium devsel, latency 0
        Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [c0] AGP version 3.0

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=02, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: cfd00000-cfefffff
        Prefetchable memory behind bridge: 8fa00000-cfbfffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
        Subsystem: ASRock Incorporation Unknown device 5513
        Flags: bus master, medium devsel, latency 128
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ff00 [size=16]
        Capabilities: [58] Power Management version 2

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: ASRock Incorporation Unknown device 7012
        Flags: bus master, medium devsel, latency 32, IRQ 22
        I/O ports at c000 [size=256]
        I/O ports at bc00 [size=128]
        Capabilities: [48] Power Management version 2

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at cfff8000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at cfff9000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
        Subsystem: ASRock Incorporation Unknown device 7001
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at cfffa000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation Unknown device 7002
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
        Subsystem: ASRock Incorporation Unknown device 8201
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at b800 [size=256]
        Memory at cfff7000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at 60000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2

00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) (prog-if 85)
        Subsystem: ASRock Incorporation Unknown device 0180
        Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 21
        I/O ports at d800 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d000 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at c800 [size=16]
        I/O ports at c400 [size=128]
        Capabilities: [58] Power Management version 2

00:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4760 SBLive!
        Flags: bus master, medium devsel, latency 32, IRQ 23
        I/O ports at b400 [size=32]
        Capabilities: [dc] Power Management version 1

00:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at dc00 [size=8]
        Capabilities: [dc] Power Management version 1

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600] (prog-if 00 [VGA])
        Subsystem: C.P. Technology Co. Ltd Unknown device 2064
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 23
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9800 [size=256]
        Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at cfec0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
        Subsystem: C.P. Technology Co. Ltd Unknown device 2065
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at a0000000 (32-bit, prefetchable) [size=256M]
        Memory at cfee0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2

```

Any help?

---

### Post by nzadLithium on 2007-07-28
it looks like you have onboard sound as well as a soundblaster live card. 
Have you tried changing your speakers over to the other card? Or maybe plugging a spare set of speakers into the other one?

the most likely reason for this to happen i think is because you have not set a default soundcard. So its possible this is caused by all your sound applications playing to the wrong card?

If it is this then to fix it you goto system, preferences, sound. Then click the sounds tab. At the bottom is a box that has the default sound card. Switch that to the card your wanting to use.

I read on these forums that some people have a problem with on restart the default resets to the wrong one.

On this thread: [http://ubuntuforums.org/showthread.php?t=188148](http://ubuntuforums.org/showthread.php?t=188148)
ogami1972 says: 
i followed the instructions on this thread
[http://ubuntuforums.org/showthread.php?t=114551](http://ubuntuforums.org/showthread.php?t=114551)
this is what i added to the end of my /etc/modprobe.d/alsa-base

#hard set for sound cards
options snd-usb-audio index=1
options snd_ICE1712 index=0
options snd-ICH6 index=2

then i
$sudo update-modules
and rebooted- voila!

so you need to put this in terminal: lsmod
look for something to do with your sound cards

then do options (your primary soundcard driver from lsmod) index=0
options (your secondary soundcard driver from lsmod) index=1

hopefully that will set the defaults on startup. :)

---

### Post by nzadLithium on 2007-07-29
Also i posted a thread about me getting a new soundcard. I was told it is not advisible to have onboard sound enabled while using a soundcard. You should go into ur pc's bios settings and disable onboard sound.

---

### Post by cablejimmy on 2007-08-16
Thanks. All I had to do was disable onboard sound in my computer's bios settings, and it worked!

---

