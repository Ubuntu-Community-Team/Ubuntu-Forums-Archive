---
title: "Soundblaster Live! 24bit not working. Newbie help"
date: 2008-10-02
forum: Multimedia Software
---

### Post by karlofski on 2008-10-02
Hello, I know absolutely nothing about what I am doing, so forgive my ignorance. I have a Soundblaster Live! 24bit PCI soundcard and I cannot find out how to make it work. Strangely I hear a sound at the login screen but that is where it stops. Once in the system I hear nothing. I tried some things from a few tutorials and forum posts but with no success. I don't know what I am doing and I am worried I may do something to cause more problems. I am using Ubuntu 8.04. 

Here is some info that I noticed other people ask for:

******************
Here is the lspci -v output:

00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
	Subsystem: ASUSTeK Computer Inc. K8V Deluxe/K8V-X motherboard
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fd300000-fd8fffff
	Prefetchable memory behind bridge: b5200000-f51fffff
	Capabilities: <access denied>

00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. A8V Deluxe or A8N-VM CSM Mainboard
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at fdd00000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at c800 [size=128]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
	Subsystem: ASUSTeK Computer Inc. A7V600/P4P800/K8V motherboard
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fdc00000 (32-bit, non-prefetchable) [size=16K]
	I/O ports at c400 [size=256]
	Capabilities: <access denied>

00:0c.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at c000 [size=32]
	Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V Deluxe/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 19
	I/O ports at e800 [size=8]
	I/O ports at e400 [size=4]
	I/O ports at e000 [size=8]
	I/O ports at d800 [size=4]
	I/O ports at d400 [size=16]
	I/O ports at d000 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 32, IRQ 19
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at b000 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at b400 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at b800 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fd900000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/K8V Deluxe motherboard (ADI AD1980 codec [SoundMAX])
	Flags: medium devsel, IRQ 20
	I/O ports at 1000 [size=256]
	Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Flags: medium devsel, IRQ 20
	I/O ports at 1400 [size=256]
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

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600] (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Radeon 9600 XT TVD
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at a000 [size=256]
	Memory at fd800000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fd700000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
	Subsystem: ASUSTeK Computer Inc. A9600XT (Secondary)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at fd600000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

*************************

 "cat /proc/asound/cards" Gives me:

 0 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0410] at 0xc000 irq 16
 1 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with AD1980 at 0x1000, irq 20

*************************************
'lsmod | grep emu' gives me no output:

*************************************

"dpkg -l | grep -v ^ii" Gives me:

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                       Version                                  Description
+++-==========================================-========================================-============================================

***********************************

I don't even know what all these commands mean, but there they are. Any help is greatly appreciated.

---

### Post by karlofski on 2008-10-02
Okay, Nevermind, I somehow got it working after much tinkering...

---

