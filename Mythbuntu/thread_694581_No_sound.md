---
title: "No sound"
date: 2008-02-12
forum: Mythbuntu
---

### Post by Sparrismannen on 2008-02-12
I just installed Mythbuntu and i get no sound at all.

Yeasterday i tryed this sudo apt-get install linux-backports-modules but I still doesn´t get any sound.

I have a  Gigabyte GA-MA69GM-S2H mb and i´m using HDMI to conect to my TV if thats any help.

Hope anyone have a clue whats wrong!!

---

### Post by murchball on 2008-02-12
The first thing to check is that sound is not muted, run alsamixer from a terminal.

---

### Post by newlinux on 2008-02-12
> **Sparrismannen said:**
> I just installed Mythbuntu and i get no sound at all.

Yeasterday i tryed this sudo apt-get install linux-backports-modules but I still doesn´t get any sound.

I have a  Gigabyte GA-MA69GM-S2H mb and i´m using HDMI to conect to my TV if thats any help.

Hope anyone have a clue whats wrong!!

How are you routing sound to your TV? I don't believe the linux drivers support audio over HDMI yet, but I could be wrong.

---

### Post by Sparrismannen on 2008-02-12
> **newlinux said:**
> How are you routing sound to your TV? I don't believe the linux drivers support audio over HDMI yet, but I could be wrong.

I only using HDMI, so you think i should check if i can get sound from S/PDIF?
I have tryed with the line out, where you connect PC speakers but there is no sound from that either.
Nothing but the headphones are off in Alsamixer.

---

### Post by newlinux on 2008-02-12
Do you get no sound from mythtv? or no sound from any application? Try playing an audio file with mplayer and see if you get any info about audio errors.

---

### Post by Sparrismannen on 2008-02-12
> **newlinux said:**
> Do you get no sound from mythtv? or no sound from any application? Try playing an audio file with mplayer and see if you get any info about audio errors.

I´m geting no sound from everything!! Don´t get any errors what i know of anyway but i dont know where to look either...

---

### Post by newlinux on 2008-02-12
Hmmm, what is the output when you type:
```

aplay -l

```
and 

```

lspci -v

```
This will at least let you know if ubuntu has recognized your sound card.

---

### Post by Chuckels550 on 2008-02-13
You say you have an HDMI connection to your TV.  Do you have a DVI to HDMI connection?  DVI is strictly display and has no audio, whether or not you have an adapter cable.  

If you are using a DVI to HDMI cable, you need an audio connection to get sound and your TV may not support a separate audio connector with HDMI.  My LCD TV doesn't.  I have to use a DVI to DVI connection to get a separate audio connection by stereo mini jack.

---

### Post by Sparrismannen on 2008-02-13
> **Chuckels550 said:**
> You say you have an HDMI connection to your TV.  Do you have a DVI to HDMI connection?  DVI is strictly display and has no audio, whether or not you have an adapter cable.  

If you are using a DVI to HDMI cable, you need an audio connection to get sound and your TV may not support a separate audio connector with HDMI.  My LCD TV doesn't.  I have to use a DVI to DVI connection to get a separate audio connection by stereo mini jack.

Nope i have HDMI to HDMI cable to connect and that should carry both the audio and the video. And my TV should support audio in via HDMI.

I will try to connect with a S/PDIF cable today and i hope that this will get me sound!!

---

### Post by Sparrismannen on 2008-02-13
> **newlinux said:**
> Hmmm, what is the output when you type:
```

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and 

```

lspci -v

```
This will at least let you know if ubuntu has recognized your sound card.
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
        Subsystem: Giga-byte Technology Unknown device 5000
        Flags: bus master, 66MHz, medium devsel, latency 32

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fde00000-fdffffff
        Prefetchable memory behind bridge: 00000000d8000000-00000000dfffffff
        Capabilities: <access denied>

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: Giga-byte Technology Unknown device b002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 22
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 19
        Memory at fe029000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
        Subsystem: Giga-byte Technology Unknown device 4385
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Unknown device 5002
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f900 [size=16]

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: Giga-byte Technology Unknown device a022
        Flags: bus master, slow devsel, latency 32, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: Giga-byte Technology Unknown device 5001
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdd00000-fddfffff
        Prefetchable memory behind bridge: fdc00000-fdcfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series (prog-if 00 [VGA])
        Subsystem: Giga-byte Technology Unknown device d001
        Flags: bus master, fast devsel, latency 32, IRQ 18
        Memory at d8000000 (64-bit, prefetchable) [size=128M]
        Memory at fdfe0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at ee00 [size=256]
        Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
        Subsystem: Giga-byte Technology Unknown device 7919
        Flags: bus master, fast devsel, latency 32, IRQ 19
        Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
        Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
        Subsystem: Giga-byte Technology Unknown device e000
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 23
        I/O ports at de00 [size=256]
        Memory at fddfe000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>


dont know where to look but heres what i get when i type in those codes..

---

### Post by Sparrismannen on 2008-02-15
Anyone??

---

### Post by newlinux on 2008-02-15
It looks like your sound card is detected, so that isn't the problem. It could be the proper modules for it aren't loaded by default or other things. Try going through this post:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And I would do these steps without using spdif or even trying to use audio through HDMI. First get sound working at all. Then configuring it to use spdif is a separate step. For some this stuff just doesn't work properly by default...

---

### Post by Sparrismannen on 2008-02-15
> **newlinux said:**
> It looks like your sound card is detected, so that isn't the problem. It could be the proper modules for it aren't loaded by default or other things. Try going through this post:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

And I would do these steps without using spdif or even trying to use audio through HDMI. First get sound working at all. Then configuring it to use spdif is a separate step. For some this stuff just doesn't work properly by default...
Yeah then it´s not mutch to do. Can´t finde the driver to my sound card.... Windows here i come!

---

