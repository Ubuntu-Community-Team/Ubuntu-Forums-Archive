---
title: "No sound support - Help me resurect an older machine"
date: 2008-06-05
forum: Multimedia Software
---

### Post by MikeMLP on 2008-06-05
Greetings, I have started by attempting to follow the comprehensive sound problem solution guide thread, but have been stopped in my tracks fairly early on.

I am trying to get sound working on a Compaq presario 4840, circa 1998.  It has integrated sound, an ESS Audodrive.  The part number on the chip itself reads as follows: ES1887F     B337.  Word on the street is that it may be possible to get this chip working with some modprobe and/or kernel recompiling voodo...

(Using Xubuntu 8.04)

Following the guide, step one:

```
:~$ aplay -l
aplay: device_list:205: no soundcards found...
```

On to step two:

```
:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at 50000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: 40000000-410fffff
	Prefetchable memory behind bridge: 20000000-200fffff

00:03.0 Ethernet controller: Lite-On Communications Inc LNE100TX [Linksys EtherFast 10/100] (rev 25)
	Subsystem: Asante Technologies, Inc. Unknown device f001
	Flags: bus master, stepping, fast Back2Back, medium devsel, latency 66, IRQ 11
	I/O ports at 2000 [size=256]
	Memory at 41100000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 20100000 [disabled] [size=256K]
	Capabilities: <access denied>

00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
	Flags: bus master, medium devsel, latency 0

00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 2420 [size=16]

00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 2400 [size=32]

00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
	Flags: medium devsel, IRQ 9

01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA controller])
	Subsystem: Compaq Computer Corporation Unknown device 0000
	Flags: bus master, VGA palette snoop, stepping, medium devsel, latency 66, IRQ 11
	Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at 1000 [size=256]
	Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: <access denied>

```

As you can see, there appears to be no sound device detected.

From the guide:

>    Failure - If it is not listed, then there are a few things that you can do.
          o
            If your soundcard is an onboard sound card, then it might be disabled in the system's BIOS. You will have to reboot and hit the key that lets you enter into the BIOS (usually Delete, F2, or F.
          o
            If your soundcard is not onboard, make sure that it is properly seated in the PCI slot. If your card is working under Windows then this is not a problem.


The latter suggestion does not apply here.  The former suggestion, I followed, but I saw no options regarding onboard sound devices in the BIOS.  Nonetheless, something funky going on in the BIOS would not surprise me because this machine has had its CMOS battery go on it (situation is ok now), thus all of the BIOS settings were lost, and had to be guessed at.  So the BIOS might still be the problem, despite me not seeing it.  

I will post again shortly, the BIOS options available, so that everyone is on the same page.  In the meantime, are there other possibilities to try?  Thanks!

---

### Post by MikeMLP on 2008-06-05
Ok, so the BIOS is fairly sparse...  Selected options are in Italics.

There are several categories, as follows:

```

System

PCI Bus Master           *Enabled* Disabled
System POST              *Fast* Full
Power management         *Disabled* Enabled
Power on password      - this contains a subsection to... create and save a PW
Setup password         -  self explanatory
Memory speed             *Fast* slow
Alternative memory reporting:
                         *Enabled* Disabled
System inactivity timeout:
                         *Disabled* 5/10/15/20/30/40/45/60/75 minutes
Compaq Amplified Speakers
                         *Present* Not Present

Communications

Parallel Port Mode        *Bidirectional* EPP ECP Compatible

Storage

Diskette drive A:         *1.44 MB (3.5 inch)* (other options irrelevant)
Diskette drive B:         *Not Installed*
Select Operating System Type
                          *Dos only or Dos and Windows* Other operating System
Enhanced IDE Transfers    *Enabled* Disabled
Ultra 33                  *Enabled* Disabled
Primary IDE Controller    *Enabled* Disabled
Secondary IDE Controller  *Enabled* Disabled

Video

USB legacy keyboard support 
                           *Enabled* Disabled
Mouse and Keyboard wakeup event 
                           *Enabled* Disabled
PCI VGA Snoop              *Enabled* Disabled
Compaq USB multimedia monitor
                           *Present (and true)* Not Present
Onboard monochrome video mode support
                           *Enabled* Disabled

Exit

```

As you can see... not a whole lot of promise there.

---

