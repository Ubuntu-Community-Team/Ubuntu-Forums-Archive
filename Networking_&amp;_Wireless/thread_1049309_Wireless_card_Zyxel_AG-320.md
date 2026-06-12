---
title: "Wireless card Zyxel AG-320"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by discodivaa on 2009-01-24
Hi, I have problem with my wireless PCI network card **Zyxel AG-320**. I have installed Xubuntu operation system and it can't detect this wireless card.

Can you help me plese, how to install this card successfully?
Thanks


This is a printout of "lspci -v" command:

```
root@ubuntu:~# lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 1.0
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: e6000000-e7ffffff
        Kernel modules: shpchp

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Kernel driver in use: ata_piix
        Kernel modules: ata_piix

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e000 [size=32]
        Kernel driver in use: uhci_hcd
        Kernel modules: uhci-hcd

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9
        Kernel driver in use: piix4_smbus
        Kernel modules: i2c-piix4

00:0e.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
        Subsystem: 3Com Corporation 3c905B 100BaseTX [Cyclone]
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at e400 [size=128]
        Memory at e9000000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at e8000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 1
        Kernel driver in use: 3c59x
        Kernel modules: 3c59x

00:12.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
        Subsystem: C-Media Electronics Inc CM8738
        Flags: bus master, medium devsel, latency 64, IRQ 12
        I/O ports at e800 [size=256]
        Capabilities: [c0] Power Management version 2
        Kernel driver in use: C-Media PCI
        Kernel modules: snd-cmipci

00:14.0 Network controller: ZyDAS Technology Corp. Device 2116 (rev 01)
        Subsystem: Device 340f:187e
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at e9001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e6000000 (32-bit, prefetchable) [size=32M]
        Expansion ROM at e5000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 1
        Capabilities: [44] AGP version 2.0
        Kernel modules: nvidiafb, rivafb
```

---

### Post by nixscripter on 2009-01-25
I can't tell if there is a free driver for Linux or not; Google is somewhat ambiguous. If there is a driver CD with the card, you can use the Windows XP driver using ndiswrapper.

Instructions for that are here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hope this helps.

---

### Post by discodivaa on 2009-01-31
> **nixscripter said:**
> I can't tell if there is a free driver for Linux or not; Google is somewhat ambiguous. If there is a driver CD with the card, you can use the Windows XP driver using ndiswrapper.

Instructions for that are here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hope this helps.

Thaks for your reply!

I have installed ordinary Windows driver for this wireless card, it works as client (Managed mode), but I can't turn interface to Master (AP) mode:(

```
root@york:/home/macek/zyxel# iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```

---

### Post by nixscripter on 2009-01-31
I'm afraid that isn't possible. :neutral:

According to a bit of research, NDIS provides the driver interface of [Wireless Zero Configuration (WZC)]("http://en.wikipedia.org/wiki/Wireless_Zero_Configuration"). According to [the card's manual]("http://www.zyxel.com/web/download.php?FileName=200601091403552006010914002520040811211941_20060901_1-AG-320_v1-00_UG_ed1_2006-09-01.pdf"), WZC cannot set up the card in AP mode; it's a feature of their utility.

In other words, the only way to do that would be to reverse engineer their utilty, and I think that's beyond what most in the Linux community are willing to take on.

But I am glad it works for you otherwise.

---

