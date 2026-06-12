---
title: "Sound problems: No system sounds, poor sound quality playback, messy sound control"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by dinhviet on 2007-11-05
I have sound problems with my Ubuntu Gutsy

1. I tried to change the system sounds and I hear nothing when I log off or log in. Moreover, I couldn't test the system sounds too.
2. Poor sound quality: When I use music or video player, the sound playback is poor, i barely hear the bass. Using equalizer helps a little bit but it's still bad (compared to windows playback).
3. The sound control button is messy. I turn down the volume, even mute it but the sound playback is still the same. It's kind of messy between ALSA mixer and OSS mixer. I'm new with Ubuntu..T_T

And here's my lspci in terminal

```
viet@Linux:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at <ignored> (64-bit, non-prefetchable)

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at fe00 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 2a3c
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: fde00000-fdefffff

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c447
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company Unknown device 2a30
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at dc00 [size=256]
        Memory at fdfff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
        Subsystem: Conexant Unknown device 200c
        Flags: bus master, medium devsel, latency 64, IRQ 255
        Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at df00 [size=8]
        Capabilities: <access denied>

```


Any help would be very appreciated. :D

---

### Post by dinhviet on 2007-11-06
I fixed the 3th problem already by uninstall and reinstall the ALSA package. However, the first and the second one is still there. 

Anyone?

---

