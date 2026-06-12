---
title: "No sound at all"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by veribaka on 2008-01-12
I don't get sound, not even in the sound testing menu. Any ideas how I should go about this?

Here's some info:

lspci -v returns:

> 00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0000000-c00fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: [b0] Subsystem: ATI Technologies Inc RS480 PCI Bridge

00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0407000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 40000000 [disabled] [size=512K]
        Capabilities: [60] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, fast Back2Back, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0404000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0405000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at c0406000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: 66MHz, medium devsel
        I/O ports at 8040 [size=16]
        Memory at c0407400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at c0400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f0200000-f02fffff
        Prefetchable memory behind bridge: f0300000-f03fffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 19
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0020000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: QUANTA Computer Inc Unknown device 0766
        Flags: bus master, medium devsel, latency 64, IRQ 21
        I/O ports at a000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Subsystem: Unknown device 18e8:6194
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at c0108000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: [40] Power Management version 2

aplay -l returns:

> **** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: SB [HDA ATI SB], dispositivo 0: ALC861VD Analog [ALC861VD Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Thanks in advance for any help!

---

### Post by xc3RnbFO8P on 2008-01-12
You can try to add this in /etc/modprobe.d/alsa-base:

options snd-hda-intel model=toshiba probe_mask=1
options snd_hda_intel model=uniwill-m31

---

### Post by veribaka on 2008-01-13
Didn't work :(.

I get sound when I jack headphones... The laptop has it's own sound device though, I should get sound without the phones :/

---

### Post by veribaka on 2008-01-13
Update: according to Device manager I got a second sound device, I don't know which one I'm supposed to use though. It's and ATi SB450 HDA.

---

### Post by xc3RnbFO8P on 2008-01-13
Have you seen this thread:

[http://ubuntuforums.org/showthread.php?t=616845&highlight=sound+problem]("http://ubuntuforums.org/showthread.php?t=616845&highlight=sound+problem")

Or you could try to install  linux-backports-modules-generic> sudo apt-get install linux-backports-modules-generic

---

### Post by veribaka on 2008-01-14
I'll check tonight when I get off of work, thanks for the pointer!

---

### Post by veribaka on 2008-01-14
Worked, thanks much!

---

