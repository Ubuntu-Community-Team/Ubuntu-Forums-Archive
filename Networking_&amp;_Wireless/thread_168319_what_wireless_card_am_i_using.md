---
title: "what wireless card am i using ?"
date: 2006-04-30
forum: Networking &amp; Wireless
---

### Post by harys on 2006-04-30
hi, i issue the command below to take note of the details of my chipset wireless card in order to configure it with ndiswrapper. could you please tell me what is my chipset card and how to configure it : 
harys@harys> lspci -v
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 0e)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c8100000-c81fffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00000000-00000fff
        Memory behind bridge: 00000000-000fffff
        Prefetchable memory behind bridge: 0000000000000000-0000000000000000
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 38c0 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 38e0 [size=32]

0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 3c00 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at c8000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0d, sec-latency=32
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: c8200000-c82fffff
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 3000 [size=256]
        I/O ports at 3880 [size=64]
        Memory at c8000800 (32-bit, non-prefetchable) [size=512]
        Memory at c8000400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 3400 [size=256]
        I/O ports at 3800 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 3c40 [size=16]

0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: medium devsel, IRQ 7
        I/O ports at 3c20 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 3150 (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 4000 [size=256]
        Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:0b:00.0 CardBus bridge: Texas Instruments: Unknown device 8031
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at 20000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0b, secondary=0c, subordinate=0f, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00005400-000054ff
        I/O window 1: 00005800-000058ff
        16-bit legacy interface ports at 0001

0000:0b:00.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c8208000 (32-bit, non-prefetchable) [size=2K]
        Memory at c8200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:0b:00.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: medium devsel, IRQ 10
        Memory at c8204000 (32-bit, non-prefetchable) [disabled] [size=8K]
        Capabilities: <available only to root>

0000:0b:00.4 0805: Texas Instruments: Unknown device 8034
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: medium devsel, IRQ 10
        Memory at c8209000 (32-bit, non-prefetchable) [disabled] [size=256]
        Memory at c8208c00 (32-bit, non-prefetchable) [disabled] [size=256]
        Memory at c8208800 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <available only to root>

0000:0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Hewlett-Packard Company: Unknown device 3082
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 5000 [size=256]
        Memory at c8209400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:0b:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
        Subsystem: Hewlett-Packard Company: Unknown device 1356
        Flags: fast devsel, IRQ 5
        Memory at c8206000 (32-bit, non-prefetchable) [disabled] [size=8K]

harys@harys>

i'm using an hp pavilion zd 8000.
thanks. harys

---

### Post by el duderino on 2006-04-30
If I had to guess I'd say the last one on the list, the Broadcom one.
Have a dig through the wiki and forum figure out which model and all other details you need.

---

### Post by jak on 2006-04-30
It's a Broadcom BCM4318. The PCI ID for it is 14e4:4318 I do beleive. If you get it to work, please please please tell me how. It feels impossible.

---

### Post by harys on 2006-04-30
hi, that's the reply i got on another forum about it : 

that's the broadcom entry at the bottom i guess, and looks like there is a native driver for it, so ndiswrapper wouldn't be needed: [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/) it says on the page there that it has gone into the mainline 2.6.17-r2 kernel but that's brand shiny new kernel in beta. if you are prepared to wait ohh... a month? i'm sure your distro of choice will have a new kernel package that will contain the driver, or you can get the driver from that site directly and install it.
__________________

Let me know if you discove something.

harys

---

### Post by jak on 2006-04-30
Indeed, the nice and shiny Dapper Drake 6.06 Beta comes with the new kernel with the bcm43xx modules in it. It's a shame it doesnt actually work for the bcm4318 though.. Well it kindof does. It just refuses to connect to my AP.

---

