---
title: "No sound"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by k51 on 2008-04-14
Hi,
I recently installed Ubuntu Feisty and everything ran fine except Ubuntu
plays no sound at all.
I've read through thread after thread trying different solutions but to
no avail.
I upgraded to Gutsy, thinking the upgrade may fix it, but it didn't, so
I upgraded to Hardy and still no sound.
Sound works fine on the Windows partition.
Here's some info:
```
$ cat /proc/asound/modules
 0 snd_hda_intel
```

```
$ lspci -v
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio
(rev a2)
        Subsystem: Elitegroup Computer Systems Unknown device a88d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
$ sudo cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe028000 irq 16

```

```
$ aplay /usr/share/sounds/login.wav
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
```

```
$ cat /etc/modules
fuse
lp

```

```
$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux Feisty 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA NVidia at 0xfe028000 irq 16

Audio devices:
0: ALC861VD Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC660-VD
```

```
$ uname -a
Linux Hardy 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

```
$ ls -la /dev/snd/*
crw-rw----+ 1 root audio 116,  0 2008-04-14 22:58 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  4 2008-04-14 22:58 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116, 24 2008-04-14 23:23 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116, 16 2008-04-14 23:23 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  1 2008-04-14 22:58 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 2008-04-14 22:58 /dev/snd/timer

```

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.15 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA NVidia                                                                                                        &#9474;
&#9474; Chip: Realtek ALC660-VD                                                                                                 &#9474;
&#9474; View: [Playback] Capture  All                                                                                           &#9474;
&#9474; Item: Master [dB gain=0.00]                                                                                             &#9474;
&#9474;                                                                                                                         &#9474;
&#9474;                                                                                                                         &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;                 &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;       &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;  &#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;                 &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;       &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;       &#9484;&#9472;&#9472;&#9488;      &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;       &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;       &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;       &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;OO&#9474;       &#9474;OO&#9474;                 &#9474;OO&#9474;      &#9474;OO&#9474;                  &#9474;OO&#9474;      &#9474;OO&#9474;       &#9474;OO&#9474;                 &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;                 &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                  &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;       &#9492;&#9472;&#9472;&#9496;                 &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;      100               100<>100    80<>80    16<>16     33<>33     71<>71    81<>81     39<>39    33<>33    100<>100    &#9474;
&#9474;  < Master >  Headphon    PCM       Front    Front Mi   Front Mi     Line       CD        Mic     Mic Boos   PC Speak    &#9474;
&#9474;                                                                                                                         &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

Nothing is muted in regular volume control.
If there's anything else you need to know just ask.

Any help would be appreciated, I need sound if I'm going to continue using Ubuntu.

Thanks,

---

### Post by k51 on 2008-04-15
Anyone?

---

### Post by xc3RnbFO8P on 2008-04-15
Try this:
[http://ubuntuforums.org/showthread.php?t=603809]("http://ubuntuforums.org/showthread.php?t=603809")

---

### Post by gleble on 2008-04-15
Or this [http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147) 
if you havn't tried it

---

### Post by warp99 on 2008-04-15
> **k51 said:**
> Hi,
I recently installed Ubuntu Feisty and everything ran fine except Ubuntu
plays no sound at all.
I've read through thread after thread trying different solutions but to
no avail.
I upgraded to Gutsy, thinking the upgrade may fix it, but it didn't, so
I upgraded to Hardy and still no sound.
Sound works fine on the Windows partition.

Any help would be appreciated, I need sound if I'm going to continue using Ubuntu.

Thanks,

Thanks for posting some information on your sound card so we can help. This seems to be a problem with this card and the snd-hda-intel sound module. The chipset you have is a realtek ACL888 and with this chipset you may have to set the model:

[http://ubuntuforums.org/showpost.php?p=4711231&postcount=4](http://ubuntuforums.org/showpost.php?p=4711231&postcount=4)

Edit:
I just notice that you have the ALC660-VD chipset **not** the ALC888, so here are the options for those models:
```

Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
                ATI SB450, SB600, RS600,
                VIA VT8251/VT8237A,
                SIS966, ULI M5461

    model       - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO si$
    single_cmd  - Use single immediate commands to communicate with
                codecs (for debugging only)
    enable_msi  - Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

          Model name    Description
          ----------    -----------

        ALC861VD/660VD
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF OUT
	  6stack-dig	6-jack with SPDIF OUT
	  3stack-660	3-jack (for ALC660VD)
	  3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
	  lenovo	Lenovo 3000 C200
	  dallas	Dallas laptops
	  hp		HP TX1000
	  auto		auto-config reading BIOS (default)

```

---

