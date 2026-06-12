---
title: "newbie with Tectra 8000 toshiba audio questions"
date: 2009-05-25
forum: Multimedia Software
---

### Post by farmerscotty on 2009-05-25
Hello and thanks for letting me in! I am new to ubuntu and loaded it on a toshiba tectra 8000 laptop version 9.04 I don't have any sound card anywhere that I can find, and I have checked in bios that it is turned on. I have updated some stuff from typing in tectra 8000 ubuntu sound stuff........added abunch of packages that it said to do......but I don't have hardware or don't know how to get to it? messed with this all day and am ready to quit was going to use the laptop to run a low power fm station playing OTR radio shows.......about to give up.........I need real simple help....
 
thanks scott the farmer in missouri
 
I followed this link but I don't have the hardware? [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
 
 
 
lspci -v
 
@toshibatectra8000:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, medium devsel, latency 64
Memory at e0000000 (32-bit, prefetchable) [size=256M]
 
00:04.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, medium devsel, latency 64, IRQ 11
Memory at df000000 (32-bit, prefetchable) [size=16M]
Memory at ff800000 (32-bit, non-prefetchable) [size=4M]
Memory at ff700000 (32-bit, non-prefetchable) [size=1M]
Capabilities: <access denied>
Kernel modules: neofb
 
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
Flags: bus master, medium devsel, latency 0
 
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
Flags: bus master, medium devsel, latency 64
[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
I/O ports at fe60 [size=16]
Kernel driver in use: ata_piix
 
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
Flags: bus master, medium devsel, latency 64, IRQ 11
I/O ports at ffe0 [size=32]
Kernel driver in use: uhci_hcd
 
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
Flags: medium devsel, IRQ 9
Kernel driver in use: piix4_smbus
Kernel modules: i2c-piix4
 
00:09.0 Communication controller: Toshiba America Info Systems FIR Port Type-O (rev 23)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, slow devsel, latency 64, IRQ 11
I/O ports at ff80 [size=32]
Kernel driver in use: donauboe
Kernel modules: donauboe
 
00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, slow devsel, latency 0, IRQ 11
Memory at 30000000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=01, subordinate=04, sec-latency=0
Memory window 0: 20000000-23fff000 (prefetchable)
Memory window 1: 24000000-27fff000
I/O window 0: 00001000-000010ff
I/O window 1: 00001400-000014ff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
 
00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC97 (rev 05)
Subsystem: Toshiba America Info Systems Device 0001
Flags: bus master, slow devsel, latency 0, IRQ 11
Memory at 30001000 (32-bit, non-prefetchable) [size=4K]
Bus: primary=00, secondary=05, subordinate=08, sec-latency=0
Memory window 0: 28000000-2bfff000 (prefetchable)
Memory window 1: 2c000000-2ffff000
I/O window 0: 00001800-000018ff
I/O window 1: 00001c00-00001cff
16-bit legacy interface ports at 0001
Kernel driver in use: yenta_cardbus
Kernel modules: yenta_socket
 
01:00.0 Network controller: RaLink RT2600 802.11 MIMO
Subsystem: Linksys Device 0052
Flags: bus master, slow devsel, latency 64, IRQ 11
Memory at 24000000 (32-bit, non-prefetchable) [size=32K]
Capabilities: <access denied>
Kernel driver in use: rt61pci
Kernel modules: rt61pci
 
@toshibatectra8000:~$ aplay -l
cottbradley@toshibatectra8000:~$ aplay -l
aplay: device_list:217: no soundcards found...
@toshibatectra8000:~$
 
 
 
when I click on default sound card nothing happens......I know I don't have it found........how do I find it?

---

### Post by farmerscotty on 2009-05-26
anyone have an idea?

---

