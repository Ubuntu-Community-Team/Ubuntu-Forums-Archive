---
title: "Audio Died Abruptly"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by kevmartin on 2007-03-11
Hi All,

I'm running Edgy and Windows XP on dual boot.  My Audio has suddenly stopped working in Linux.  Well when I say suddenly, that's not quite true.  At first it seems to not work only when I had the Windows Virtualbox running.  But today, audio has gone completely.  It still works just fine if I boot the computer into windows.

Other threads here lead me to find these commands to provide some information, but I'm not sure where to go next.  Any suggestions would be great, thanks:

```
kev@kev-desktop:~$ aplay -l lists
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
kev@kev-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: efd00000-efefffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e7f00000
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: efc00000-efcfffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: ef700000-efbfffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, medium devsel, latency 0, IRQ 66
        I/O ports at ff40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, medium devsel, latency 0, IRQ 74
        I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, medium devsel, latency 0, IRQ 50
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: ef600000-ef6fffff
        Prefetchable memory behind bridge: 00000000e8000000-00000000ebf00000
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at ffa0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 233
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fea0 [size=16]
        Memory at effffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Dell Unknown device 01d1
        Flags: medium devsel, IRQ 10
        I/O ports at ece0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0602
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at e0000000 (64-bit, prefetchable) [size=128M]
        Memory at efde0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at dc00 [size=256]
        Expansion ROM at efe00000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon X600(RV380)
        Subsystem: ATI Technologies Inc Unknown device 0603
        Flags: bus master, fast devsel, latency 0
        Memory at efdf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
        Subsystem: Dell Unknown device 01d1
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at ef7e0000 (32-bit, non-prefetchable) [size=128K]
        Memory at ef800000 (32-bit, non-prefetchable) [size=4M]
        I/O ports at cce0 [size=32]
        Capabilities: <access denied>

05:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

05:04.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 1007
        Flags: bus master, medium devsel, latency 64, IRQ 169
        I/O ports at bce0 [size=32]
        Capabilities: <access denied>

05:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant Unknown device 200f
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at ef6f0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at bcd8 [size=8]
        Capabilities: <access denied>

```

```
kev@kev-desktop:~$ sudo modprobe snd-ca0106
Password:
kev@kev-desktop:~$ 

```

Oh, and I also ran the alsamixer and raised everything up well above zero:

```


&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.11 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: CA0106                                                                 &#9474;
&#9474; Chip:                                                                        &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: IEC958                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;             &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;             &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     >
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;             &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;    &#9474;OO&#9474;                                                                      &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;                                                                      &#9474;
&#9474;            59<>59    55<>55   55<>55   63<>63    65<>65   80<>80   75<>75    &#9474;
&#9474; < IEC958 >IEC958 C  IEC958 F IEC958 R IEC958 U  Analog C Analog F Analog R   &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


```

---

### Post by kevmartin on 2007-03-11
Well, at least I found a workaround for my most desperate audio need (audio alerts of incoming IM's which I need big time for working) - Gaim allows you to use the system beep instead of normal sound files as the alert sound.

Needless to say though, I really would like my sound to work properly (as it was previously).

Thanks

---

### Post by kevmartin on 2007-03-12
I have a major clue that I'm sure will help those in the know to tell me what's wrong, but unfortunately doesn't help me much without advice.

My boot loader (grub) has entries for kernel 2.6.17-11-386 as well as 2.6.15-28-386

I had been using the default one (2.6.17) and getting no sound.
I just tried booting to 2.6.15 and now have sound again.

This is good of course, but still begs the question 'what's causing this and how do I fix it?'

Any advice would be welcomed.  Thanks.

---

### Post by Ergo on 2007-03-12
I have had similar events occur with my machine.  I hate to tell you but another mixer has your volume adjusted down.  I found that more than one program or mixer program could control the audio level.  I went through every program that had sound control and adjusted them all to the same level.  Closed all programs and rebooted.  I then had sound and now I only adjust the levels through the alsa mixer gui.  Good luck, I hope it helps.

---

### Post by kevmartin on 2007-03-13
Weirder and weirder - it fixed itself.  I was manually booting in to the older kernel each time I rebooted and having no problems with audio.  Then I inadvertently used the newer kernel again today when the PC rebooted itself on a power hiccup, and lo and behold, sound is working again.

---

