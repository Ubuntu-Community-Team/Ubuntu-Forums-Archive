---
title: "The sound disappear....what to do when the HWT fail?"
date: 2006-08-27
forum: Multimedia &amp; Video
---

### Post by CassioBunana on 2006-08-27
Hi guys...I've been reading past posted msg for days, trying to understand why my laptop refuse to play any sound! As a lot of other people, I've read the very good LordRaiden HWT but without success...ALSA seems to be correctly installed and modules loaded, except no applications are able to access sound devices...this is my configuration:

```

 andrea@cassioli:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
scheda 0: I82801DBICH4 [Intel 82801DB-ICH4], dispositivo 0: Intel ICH [Intel 828 01DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
scheda 0: I82801DBICH4 [Intel 82801DB-ICH4], dispositivo 4: Intel ICH - IEC958 [ Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

andrea@cassioli:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, fast devsel, latency 0
        Memory at <unassigned> (32-bit, prefetchable)
        Capabilities: <available only to root>

0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, fast devsel, latency 0

0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, fast devsel, latency 0

0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at e0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: fast devsel
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e0080000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at e0100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: e0200000-e02fffff
        Prefetchable memory behind bridge: 20000000-22ffffff

0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1810 [size=16]
        Memory at 23000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: medium devsel, IRQ 10
        I/O ports at 1880 [size=32]

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: medium devsel, IRQ 10
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <available only to root>

0000:02:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 96, IRQ 10
        Memory at e0202000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Wistron Corp.: Unknown device 1082
        Flags: bus master, fast devsel, latency 64, IRQ 10
        Memory at e0200000 (32-bit, non-prefetchable) [size=8K]
        Expansion ROM at 22000000 [disabled] [size=64K]
        Capabilities: <available only to root>

0000:02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corporation MIM2000/Centrino
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e0203000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:09.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Fujitsu Siemens Computer GmbH: Unknown device 1033
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at e0204000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 00003000-000030ff
        I/O window 1: 00003400-000034ff
        16-bit legacy interface ports at 0001

andrea@cassioli:~$ cat /proc/asound/modules
0 snd_intel8x0


```

I guess it's enough...trying to use for example mplayer I get:
```

andrea@cassioli:~$ mplayer ~/Desktop/MISTO/bass.mp3
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Banias (Family: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/andrea/Desktop/MISTO/bass.mp3.
Audio file file format detected.
Clip info:
 Title:
 Artist:
 Album:
 Year:
 Comment: Made with Sony ACID 5
 Genre: Blues
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 256.0 kbit/18.14% (ratio: 32000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
A:   8.4 (08.4) of 115.0 (01:55.0)  0.9%

MPlayer interrupted by signal 2 in module: play_audio
alsa-uninit: pcm closed


```

what else? any ideas??

---

