---
title: "Screen Flashes Black"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by pollock.tar.gz on 2006-08-20
hi. ive been having this strange problem when using ubuntu, that i ignored at first, but now its beginning to get nerve-wracking. when using ubuntu at any random time my screen will turn black for about half of a second, and then go back to normal. does anybody else have this problem? or, does anybody know a way to solve it? ](*,) 

thanks in advance

---

### Post by pollock.tar.gz on 2006-08-21
bumped..

does anybody reply to my threads?!

---

### Post by tseliot on 2006-08-21
1) What's the model of your graphic card?
2) Did you install a driver for it?
3) post the output of this command:
```
lspci -v
```

---

### Post by pollock.tar.gz on 2006-08-21
here it is:


```
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at 80000000 (32-bit, prefetchable) [size=512M]
        Capabilities: <available only to root>

0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 80ac
        Flags: 66MHz, fast devsel

0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 12
        I/O ports at e400 [size=32]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at c4002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at c4003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at c4004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard onboard nForce2 Ethernet
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 177
        Memory at c4005000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at d000 [size=8]
        Capabilities: <available only to root>

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8095
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        I/O ports at d400 [size=256]
        I/O ports at d800 [size=128]
        Memory at c4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: c3000000-c3ffffff
        Prefetchable memory behind bridge: c0000000-c0ffffff

0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc.: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: c1000000-c2ffffff
        Prefetchable memory behind bridge: a0000000-bfffffff

0000:01:06.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) (prog-if 10 [OHCI])
        Subsystem: Texas Instruments: Unknown device 8010
        Flags: bus master, medium devsel, latency 32, IRQ 201
        Memory at c3004000 (32-bit, non-prefetchable) [size=2K]
        Memory at c3000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:01:07.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Netgear MA311 802.11b wireless adapter
        Flags: bus master, medium devsel, latency 32, IRQ 209
        Memory at c0000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc: Unknown device 0402
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 209
        Memory at a0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at c000 [size=256]
        Memory at c2000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c1000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
        Subsystem: ATI Technologies Inc: Unknown device 0403
        Flags: 66MHz, medium devsel
        Memory at b0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at c2010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <available only to root>
```


[i have 3D acceleration working]

---

### Post by pollock.tar.gz on 2006-08-22
bump'd

---

### Post by pollock.tar.gz on 2006-08-22
i could really use help on this, if anybody knows a solution

---

### Post by graigsmith on 2007-06-11
im having the exact same problem. 

it started after i upgraded my videocard.  i had an ati 9200. and i upgraded to a geforce 6200.    now i get random 1 second blackouts just as you described.  must be the proprietary nvidia driver. you know what, i never had problems with my 9200.  i'm tempted to take this card back.

```
lspci -v
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
        Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 1400
        Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 3
        Memory at e4001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 12
        Memory at e4004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at e4005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
        Subsystem: Biostar Microtech Int'l Corp Unknown device 2301
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at e4000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e000 [size=8]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e3000000-e3ffffff

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 3400
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]
        Capabilities: <access denied>

00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Biostar Microtech Int'l Corp Unknown device 4100
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at e4002000 (32-bit, non-prefetchable) [size=2K]
        Memory at e4003000 (32-bit, non-prefetchable) [size=64]
        Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 32
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        Memory behind bridge: e0000000-e2ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 3
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

01:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at d400 [size=8]
        Capabilities: <access denied>

01:08.0 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Belkin Root Hub
        Flags: bus master, medium devsel, latency 32, IRQ 3
        Memory at e3000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:08.1 USB Controller: NEC Corporation USB (rev 43) (prog-if 10 [OHCI])
        Subsystem: Belkin Root Hub
        Flags: bus master, medium devsel, latency 32, IRQ 12
        Memory at e3001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:08.2 USB Controller: NEC Corporation USB 2.0 (rev 04) (prog-if 20 [EHCI])
        Subsystem: Belkin Root Hub
        Flags: bus master, medium devsel, latency 32, IRQ 12
        Memory at e3002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 12
        Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at e2000000 [disabled] [size=128K]
        Capabilities: <access denied>

```

---

### Post by Richard.F on 2007-12-18
I got the exact same problem guys. Using the restricted drivers for NVIDIA.

---

### Post by blurryone on 2007-12-21
yep me too, geforce go 7600 restricted nvidia drivers and i wouldn't say a second more like 2-3 frame drop outs. (less than half a second) but noticeable and annoying.

---

### Post by roaldz on 2007-12-21
Got this too, but I don´t find it annoying. It´s not occurring often too, so all take it for granted..

---

### Post by Xiong Chiamiov on 2007-12-21
I have a 7600gs that doesn't give me any problems.
Sorry I can't help though.

---

### Post by Xer0 on 2007-12-22
I have this too, 6600GT, restricted nvidia drivers I think. Has only appeared since upgrading to Gutsy.
No problems for about 10 minutes, then gets steadily worse, until the screen is black more often than it is not, rendering the computer un-useable. Will post diagnostics when I'm at that computer next.

---

### Post by mock_alien on 2007-12-23
Have the same problem.

It cant be good for the hardware, (or the screen) to have them blinking like that.
(and some times it freezes so it appear the the computer has "hanged",so i cant show of my ubuntu laptop as "stable" as it's not.

I have a hp dv9000t.

nvidia 7600 go

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at de300000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=06, sec-latency=0
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at de304000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: de000000-de0fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 18c8 [size=8]
        I/O ports at 18ac [size=4]
        I/O ports at 18c0 [size=8]
        I/O ports at 18a8 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at de304400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 4
        I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dc000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135c
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at da000000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at 5000 [size=32]
        Capabilities: <access denied>

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at de000000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at de000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 11
        Memory at de000c00 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 11
        Memory at de001000 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>

07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30bb
        Flags: medium devsel, IRQ 11
        Memory at de001400 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: <access denied>
-------------------------------------------------------------------------------

---

### Post by JasonSilver on 2007-12-28
I've got the same problem as well. I use a Toshiba Satellite p200-rt2 laptop, and only experienced the problems when upgrading to gutsy.

The flashing gets pretty annoying. At times I thought it was related to the web cam-- because it seemed if I moved, the screen comes back on-- but I think I've ruled that out.

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff04
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at dc200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [d0] Power Management version 2

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff04
        Flags: bus master, fast devsel, latency 0
        Memory at dc180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff03
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at dc440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d8000000-d9ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: da000000-dbffffff
        Prefetchable memory behind bridge: 00000000d4000000-00000000d5ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at dc444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=0a, sec-latency=56
        I/O behind bridge: 00005000-00005fff
        Memory behind bridge: dc000000-dc0fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff00

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1040
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, fast devsel, latency 0, IRQ 18
        I/O ports at 4000 [size=256]
        Memory at da000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 17
        Memory at dc006000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 00005000-000050ff
        I/O window 1: 00005400-000054ff
        16-bit legacy interface ports at 0001

06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at dc005000 (32-bit, non-prefetchable) [size=2K]
        Memory at dc000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

06:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, medium devsel, latency 57, IRQ 18
        Memory at dc005800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2



Thanks for any help you can bring here.
Jason

---

### Post by Dojjah on 2008-01-10
I am having this exact same problem. It started randomly. Im using gusty as well. Has any solution or cause of this problem surfaced?

---

### Post by Dojjah on 2008-01-11
ok it appears this has something to do with nvdia cards. its start to really annoying and be come more occuring.

---

### Post by rhyeal on 2008-01-14
I too am having this problem.  Sorry to repost in this thread if it seems too old but I have some other info to add.

I am using a HP dv6470us and have Gutsy installed.  On boot, I have to add noapic and nolapic to the boot line and have one error.

I have an error involving a PCI card.  The number I remember, though it flashes briefly, was 5:00.0.  It states that there was a memory resource allocation #6.  However, when running lspci -v, I found that 5:00.0 is the Nvidia card.

Below is the post of my lspci -v.

05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c6000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

I too am using proprietary drivers from Nvidia.  My theory, and I'd like some expert advice here, is that this memory allocation is causing this error.

I will search for Linux drivers for Nvidia to see if I can fix this.

And, this is my second time typing this.  The first time ended up with the computer freezing.  If I scroll too fast in a downward direction, the screen freezes apparently.

---

### Post by kefurd06 on 2008-01-14
hp pavilion dv9000t (CTO) w/ nvidia go 7600. it's nvidia + compiz-fusion. turn off all of the effects and i get no blanking. occasional freezes while browsing, then crash handler kicks in (i think that's what it is). problem is pretty bad after a suspend. look for a solution in a year or two. :/

update: i just now got a blank while scrolling up through this thread. turned off smooth scrolling, don't know if it will help.

---

### Post by tuebinger on 2008-02-25
I think I've solved my screen going black problem.  I thought it was flashing black, but it was actually going black and staying black unless I touched the mouse or keyboard, which led me to believe the computer might think the laptop lid is closed when it goes black..

 I went into preferences and changed to the 'do nothing' when laptop lid is closed option, and sure enough now the blanking has stopped. 

 Doesn't seem right to have to do this, since now my screen is going to be on all the time unless I change the settings manually each time I'm finished working on the computer.  Is anyone else experiencing this problem with their laptop?

---

### Post by Jim D v2.0 on 2008-03-26
I don't think this has anything to do with the video card. This happens to me as well and I have an ATI Radeon 9550. I noticed the problem after the last kernel update but I also upgraded my mouse and keyboard at the same time so it might be related to Xserver.

---

### Post by pkands on 2008-04-02
Same here using the fglrx driver. If I use the ATI driver, no more blanking.

---

### Post by onetb on 2008-04-03
Getting the same issues.  Hope there is some kind of resolution sometime soon.

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, fast devsel, latency 0
        Memory at ec000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) (prog-if 00 [VGA])
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at e8000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at e8080000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e8100000-e81fffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1860 [size=16]
        Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: medium devsel, IRQ 9
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at e8080c00 (32-bit, non-prefetchable) [size=512]
        Memory at e8080800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Trigem Computer Inc. Unknown device 3189
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at 2000 [size=256]
        Memory at e8100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
        Subsystem: Agere Systems LT WinModem
        Flags: bus master, fast Back2Back, medium devsel, latency 64, IRQ 9
        Memory at e8100400 (32-bit, non-prefetchable) [size=256]
        I/O ports at 2800 [size=8]
        I/O ports at 2400 [size=256]
        Capabilities: <access denied>

```

---

### Post by ccm5023 on 2008-04-07
I have a HP Pavillion dv6000t w/ nvidia graphics card.  It will flash black for half a second and sometimes freeze after it flashes.  I can stop it when I go into Applications>System Tools>Nvidia Settings and change the screen frequency to 60HZ rather than the default "Auto"

```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c2000000-c3ffffff
        Prefetchable memory behind bridge: 00000000c8200000-00000000c83fffff
        Capabilities: <access denied>

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: c4000000-c5ffffff
        Prefetchable memory behind bridge: 00000000c8400000-00000000c85fffff
        Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: c6000000-c7ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 1d00 [size=128]

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at c0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3080 [size=16]
        Capabilities: <access denied>

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at 30c0 [size=8]
        I/O ports at 30b4 [size=4]
        I/O ports at 30b8 [size=8]
        I/O ports at 30b0 [size=4]
        I/O ports at 3090 [size=16]
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=64
        Memory behind bridge: c8000000-c80fffff
        Capabilities: <access denied>

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at c0008000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30e0 [size=8]
        Capabilities: <access denied>

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

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 1366
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at c4000000 (64-bit, non-prefetchable) [size=16K]
        Memory at c8400000 (64-bit, prefetchable) [size=1M]
        Capabilities: <access denied>

05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at c7000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c6000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at c8000000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at c8000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c8000c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: medium devsel, IRQ 11
        Memory at c8001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: medium devsel, IRQ 11
        Memory at c8001400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

---

### Post by Jim D v2.0 on 2008-04-17
Another thing to check is whether or not the power supply is adequate for all of the devices that are being used.

---

### Post by JasonSilver on 2008-04-22
> **JasonSilver said:**
> I've got the same problem as well. I use a Toshiba Satellite p200-rt2 laptop, and only experienced the problems when upgrading to gutsy.

The flashing gets pretty annoying. At times I thought it was related to the web cam-- because it seemed if I moved, the screen comes back on-- but I think I've ruled that out.



Thanks for any help you can bring here.
Jason

Actually, as an update, if I plug an external keyboard mouse into the computer, so that I'm not actually touching it, everything is fine. If I hold it on my lap, then it will go black. Rapping the laptop lightly, causes it to come on. 

So I think it has something to do with a switch that is too sensitive for shutting off the monitor when the laptop closes, as someone mentioned below.

Jason

---

