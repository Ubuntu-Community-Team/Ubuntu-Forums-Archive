---
title: "Annoying slow sound ..."
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by samae on 2007-04-22
_Here is my problem :_
Ever since I had Edgy everything in my sound system was all right. And then I updated to Feisty.

It fixed a lot of minor bugs here and there but it disturbed my audio system : now my laptop give me the impression of running in slow motion in fact it plays sounds very slowly ... It applies in any program I have used so far.

I really dont get it so please help because it looks unsual, and I haven't found any threads about this problem : my system plays sounds but slow and grave ...

I've tried many tricks to know were it came from by I'm desperate now :s

_Anyway this was my problem, and here follows my config and some tests :_

And I'm running Xubuntu 64bit 7.04

```

tail -2 /proc/asound/oss/sndstat
Mixers:
0: Realtek ALC650F
```

```

amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [-12.00dB] [on]
  Front Right: Playback 23 [74%] [-12.00dB] [on]
Simple mixer control 'Master Mono',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-16.50dB] [on]
Simple mixer control '3D Control - Center',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Depth',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 15
  Mono: 0 [0%]
Simple mixer control '3D Control - Switch',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-1.50dB] [on]
  Front Right: Playback 22 [71%] [-1.50dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-46.50dB] [off]
  Front Right: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Surround Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Surround Jack Mode',0
  Capabilities: enum
  Items: 'Shared' 'Independent'
  Item0: 'Independent'
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Center/LFE Down Mix',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-46.50dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 0 [0%] [-34.50dB] [off] Capture [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off] Capture [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 0 [0%] [-34.50dB] [off]
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'Mic Boost (+20dB)',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic Select',0
  Capabilities: enum
  Items: 'Mic1' 'Mic2'
  Item0: 'Mic1'
Simple mixer control 'Video',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 19 [61%] [-6.00dB] [on] Capture [off]
  Front Right: Playback 19 [61%] [-6.00dB] [on] Capture [off]
Simple mixer control 'Phone',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono: Playback 20 [65%] [-4.50dB] [on]
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [off]
Simple mixer control 'IEC958 Playback AC97-SPSA',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 3
  Mono: 2 [67%]
Simple mixer control 'PC Speaker',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 15
  Mono: Playback 0 [0%] [-45.00dB] [off]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch pswitch-joined cswitch cswitch-exclusive
  Capture exclusive group: 0
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Front Left: Playback 23 [74%] [0.00dB] [on] Capture [off]
  Front Right: Playback 23 [74%] [0.00dB] [on] Capture [off]
Simple mixer control 'Mono Output Select',0
  Capabilities: enum
  Items: 'Mix' 'Mic'
  Item0: 'Mix'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 10 [67%] [15.00dB] [on]
  Front Right: Capture 10 [67%] [15.00dB] [on]
Simple mixer control 'Mix',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Mix Mono',0
  Capabilities: cswitch cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'Analog to IEC958 Output',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Channel Mode',0
  Capabilities: enum
  Items: '2ch' '4ch' '6ch'
  Item0: '6ch'
Simple mixer control 'Duplicate Front',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Exchange Center/LFE',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'External Amplifier',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Swap Surround Slot',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
```

```

lspci -nv
00:00.0 0600: 1039:0756 (rev 02)
        Subsystem: 1043:1977
        Flags: bus master, medium devsel, latency 32
        Capabilities: <access denied>

00:01.0 0604: 1039:0004 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: fa200000-fe2fffff
        Prefetchable memory behind bridge: 00000000bde00000-00000000ddefffff
        Capabilities: <access denied>

00:02.0 0601: 1039:0964 (rev 36)
        Flags: bus master, medium devsel, latency 0

00:02.5 0101: 1039:5513 (rev 01) (prog-if 80 [Master])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 128
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:02.6 0703: 1039:7013 (rev a0) (prog-if 00 [Generic])
        Subsystem: 1043:1816
        Flags: medium devsel, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at ec00 [size=128]
        Capabilities: <access denied>

00:02.7 0401: 1039:7012 (rev a0)
        Subsystem: 1043:1103
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at e400 [size=256]
        I/O ports at e000 [size=128]
        Capabilities: <access denied>

00:03.0 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at febff000 (32-bit, non-prefetchable) [size=4K]

00:03.1 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]

00:03.2 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]

00:03.3 0c03: 1039:7002 (prog-if 20 [EHCI])
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.0 0280: 14e4:4318 (rev 02)
        Subsystem: 1043:120f
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at febfa000 (32-bit, non-prefetchable) [size=8K]

00:0a.0 0607: 1180:0476 (rev b3)
        Subsystem: 1043:1107
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at 58000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

00:0a.1 0c00: 1180:0552 (rev 08) (prog-if 10 [OHCI])
        Subsystem: 1043:1977
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at febf9800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:0a.2 0805: 1180:0822 (rev 17)
        Subsystem: 1043:1977
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at febf9400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0a.3 0880: 1180:0592 (rev 08)
        Subsystem: 1043:1977
        Flags: medium devsel, IRQ 5
        Memory at febf9000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0b.0 0200: 10ec:8139 (rev 10)
        Subsystem: 1043:1045
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at d800 [size=256]
        Memory at febf8c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 0600: 1022:1100
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 0600: 1022:1101
        Flags: fast devsel

00:18.2 0600: 1022:1102
        Flags: fast devsel

00:18.3 0600: 1022:1103
        Flags: fast devsel

01:00.0 0300: 10de:0167 (rev a1) (prog-if 00 [VGA])
        Subsystem: 1043:188a
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fe2e0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 0280: 14e4:4318 (rev 02)
        Subsystem: 1737:0049
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at 54000000 (32-bit, non-prefetchable) [size=8K]
```


```

asoundconf list
Names of available sound cards:
SI7012
```

I haven't modified the default options in /etc/asound.conf

Only APIC errors in dmesg (so it should have nothing to do with it) :
APIC error on CPU0: 40(40)


```
cat /proc/interrupts
           CPU0       
  0:    1220416   IO-APIC-edge      timer
  1:         12   IO-APIC-edge      i8042
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc
  9:      41894   IO-APIC-fasteoi   acpi
 12:        133   IO-APIC-edge      i8042
 14:      47833   IO-APIC-edge      ide0
 15:      43399   IO-APIC-edge      ide1
 16:     326391   IO-APIC-fasteoi   nvidia
 17:     326709   IO-APIC-fasteoi   yenta, bcm43xx
 18:      68323   IO-APIC-fasteoi   ohci1394, SiS SI7012
 19:          0   IO-APIC-fasteoi   sdhci:slot0
 20:       9169   IO-APIC-fasteoi   ohci_hcd:usb1
 21:     112730   IO-APIC-fasteoi   ohci_hcd:usb2
 22:          0   IO-APIC-fasteoi   ohci_hcd:usb3
 23:      12908   IO-APIC-fasteoi   ehci_hcd:usb4
NMI:          0 
LOC:    1220276 
ERR:         48
```

---

### Post by ronan001 on 2007-04-25
I have updated to feisty fawn also and i am getting a similar problem.

If i play a mp3 or movie files (Divx) it plays in slow motion!!! I have not tested it with other formats.

```

ronan@ronan-desktop:~$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux ronan-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
M Audio Audiophile 24/96 at 0xdc00, irq 17

Audio devices:
0: ICE1712 multi (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: M Audio Audiophile 24/96 MIDI

Timers:
31: system timer

Mixers:
0: ICE1712 - multitrack


```

```

ronan@ronan-desktop:~$ amixer
Simple mixer control 'IEC958',0
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'IEC958 Multi',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'IEC958 Multi',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [off]
  Front Right: Capture 0 [0%] [off]
Simple mixer control 'IEC958',1
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'Digital Mixer'
Simple mixer control 'ADC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 163
  Mono: 112 [69%] [-7.50dB]
Simple mixer control 'ADC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 163
  Mono: 147 [90%] [10.00dB]
Simple mixer control 'DAC',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 127
  Mono: 112 [88%] [-7.50dB]
Simple mixer control 'DAC',1
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 127
  Mono: 147 [116%] [10.00dB]
Simple mixer control 'Deemphasis',0
  Capabilities: enum
  Items: '44.1kHz' 'Off' '48kHz' '32kHz'
  Item0: '44.1kHz'
Simple mixer control 'H/W',0
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: enum
  Items: 'PCM Out' 'H/W In 0' 'H/W In 1' 'H/W In 2' 'H/W In 3' 'H/W In 4' 'H/W In 5' 'H/W In 6' 'H/W In 7' 'IEC958 In L' 'IEC958 In R' 'Digital Mixer'
  Item0: 'PCM Out'
Simple mixer control 'H/W Multi',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'H/W Multi',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 96
  Front Left: Capture 0 [0%] [-144.00dB] [off]
  Front Right: Capture 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 68 [71%] [-42.00dB] [off]
  Front Right: Playback 68 [71%] [-42.00dB] [off]
Simple mixer control 'Multi',1
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 62 [65%] [-51.00dB] [off]
  Front Right: Playback 62 [65%] [-51.00dB] [off]
Simple mixer control 'Multi',2
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',3
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',4
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',5
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',6
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 0 [0%] [-144.00dB] [off]
  Front Right: Playback 0 [0%] [-144.00dB] [off]
Simple mixer control 'Multi',7
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 9 [9%] [-130.50dB] [off]
  Front Right: Playback 9 [9%] [-130.50dB] [off]
Simple mixer control 'Multi',8
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 45 [47%] [-76.50dB] [on]
  Front Right: Playback 45 [47%] [-76.50dB] [on]
Simple mixer control 'Multi',9
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 96
  Mono:
  Front Left: Playback 45 [47%] [-76.50dB] [on]
  Front Right: Playback 45 [47%] [-76.50dB] [on]
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000' 'IEC958 Input'
  Item0: '8000'
Simple mixer control 'Multi Track Internal Clock Default',0
  Capabilities: enum
  Items: '8000' '9600' '11025' '12000' '16000' '22050' '24000' '32000' '44100' '48000' '64000' '88200' '96000'
  Item0: '8000'
Simple mixer control 'Multi Track Peak',0
  Capabilities: volume
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Capture channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Limits: 0 - 255
  Front Left: 76 [30%]
  Front Right: 90 [35%]
  Rear Left: 0 [0%]
  Rear Right: 0 [0%]
  Front Center: 0 [0%]
  Woofer: 0 [0%]
  Side Left: 0 [0%]
  Side Right: 0 [0%]
  Rear Center: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
  ?: 0 [0%]
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Multi Track Volume Rate',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 255
  Mono: 225 [88%]


```

```


ronan@ronan-desktop:~$ lspci -nv
00:00.0 0600: 8086:2570 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 0604: 8086:2571 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ffc00000-ffcfffff
        Prefetchable memory behind bridge: d7f00000-f7efffff

00:1d.0 0c03: 8086:24c2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1462:7420
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e400 [size=32]

00:1d.1 0c03: 8086:24c4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1462:7420
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at e800 [size=32]

00:1d.2 0c03: 8086:24c7 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1462:7420
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ec00 [size=32]

00:1d.7 0c03: 8086:24cd (rev 02) (prog-if 20 [EHCI])
        Subsystem: 1462:7420
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at ffeffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 0604: 8086:244e (rev 82) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: ffd00000-ffdfffff
        Prefetchable memory behind bridge: 40000000-400fffff

00:1f.0 0601: 8086:24c0 (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 0101: 8086:24cb (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: 1462:7420
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fc00 [size=16]
        Memory at 40100000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 0c05: 8086:24c3 (rev 02)
        Subsystem: 1462:7420
        Flags: medium devsel, IRQ 11
        I/O ports at 0c00 [size=32]

01:00.0 0300: 1002:5964 (rev 01) (prog-if 00 [VGA])
        Subsystem: 1043:c008
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b800 [size=256]
        Memory at ffcf0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ffcc0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 0380: 1002:5d44 (rev 01)
        Subsystem: 1043:c009
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Memory at ffce0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:03.0 0401: 1412:1712 (rev 02)
        Subsystem: 1412:d634
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at dc00 [size=32]
        I/O ports at d800 [size=16]
        I/O ports at d400 [size=16]
        I/O ports at d000 [size=64]
        Capabilities: <access denied>

02:0b.0 0200: 10ec:8139 (rev 10)
        Subsystem: 1462:742c
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at cc00 [size=256]
        Memory at ffdfff00 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at 40000000 [disabled] [size=64K]
        Capabilities: <access denied>


```

```

> asoundconf list
Names of available sound cards:
M2496

```

```

ronan@ronan-desktop:~$ cat /proc/interrupts
           CPU0       
  0:     185537   IO-APIC-edge      timer
  1:       1138   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          1   IO-APIC-fasteoi   acpi
 12:      84642   IO-APIC-edge      i8042
 14:       6919   IO-APIC-edge      libata
 15:      27017   IO-APIC-edge      libata
 16:      52656   IO-APIC-fasteoi   uhci_hcd:usb1, radeon@pci:0000:01:00.0
 17:        781   IO-APIC-fasteoi   uhci_hcd:usb2, ICE1712
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb3
 19:       6814   IO-APIC-fasteoi   ehci_hcd:usb4, eth0
NMI:          0 
LOC:     185419 
ERR:          0
MIS:          0

```

---

### Post by ronan001 on 2007-04-25
ok, my system seems to be ok now???

What i did was booted into the edgy version of Kubuntu from the boot menu. 

I checked what settings when being used by the mixer. (by clicking the speaker icon in the bottom right and selecting mixer).

I wrote down the settings and logged back into fiesty. i changed the settings to match edgy and it still woudnt work.

i then logged out,  logged into the middle option on my boot menu which happens to be a version of fiesty aswell! i'm not sure when its from, it appeared today at some stage after i have installed fiesty. 

Anyway the sound would not work in this version, so i clicked restart computer. I then heard the log out sound working properly, i have no idea why it worked on the logout.

I logged into the most recent version of fiesty and the sound is fine. (although i did have to higher up the volume using the ADC slider in the output tab)

All in all, i havnt an idea what has fixed it and i hope it is fixed. i.e. next time i log in that it will be working. :lolflag: :lolflag: :lolflag: :lolflag:

---

### Post by samae on 2007-04-25
I don't know where this problem came from, but I discovered that if I did not had my pcmcia wifi card plugged, sound was normal (?)
Still I don't understand, and that's annoying ...

---

### Post by mirwin77 on 2007-04-25
I was having the same slow sound problem since upgrading to Feisty.  I recently changed the multi-track internal clock rate (use Kmix or Alsa-Mixer, in Kmix the setting is under the "switches" tab) from 8000 to 44100 and everything is cool now.  Not sure why the clock rate was reset during the upgrade.  Hope this helps.

---

