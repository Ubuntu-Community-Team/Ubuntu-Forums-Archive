---
title: "HP NC6000, WiFi, /Ubuntu 8.04.2/ Intel ? Drivers"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by MavsX on 2009-04-19
Hi,

Just installed Ubuntu 7.10 on HP/Compaq NC6000 laptop.  I have been searching for help to get the WiFi working.  I heard to upgrade to 8.04.2 So that is what i am running now.  

When i push the WiFi Button the light does not come on, and obviously the WiFi isn't working.  I am not seeing any network manager icons anywhere.

I found one thread that looked promising but then the link to the driver was error 404 not found.  

Please let me know what code i need to run in terminal to get the information for you guys.

I will post some output below to some common questions.

---

### Post by RedSingularity on 2009-04-19
lspci in the terminal and post the output.

---

### Post by MavsX on 2009-04-19
> code = lspci -v | less

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, fast devsel, latency 0
        Memory at b0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: 90300000-903fffff
        Prefetchable memory behind bridge: 98000000-9fffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 38c0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
:


00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 3c00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at a0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=0c, sec-latency=32
        Memory behind bridge: 90000000-902fffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 0
3) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 3c20 [size=16]
        Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: medium devsel
        I/O ports at 1200 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, medium devsel, latency 0, IRQ 11

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Mode
m Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: medium devsel, IRQ 11
        I/O ports at 3400 [size=256]
        I/O ports at 3800 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 10
        Memory at 98000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at 90300000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at 90320000 [disabled] [size=128K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
        Subsystem: Hewlett-Packard Company NC6000 laptop
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controll
er
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 90100000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 4c000000-4ffff000 (prefetchable)
        Memory window 1: 50000000-53fff000
        I/O window 0: 00001c00-00001cff
        I/O window 1: 00004000-000040ff
        16-bit legacy interface ports at 0001

02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: slow devsel, IRQ 10
        Memory at 90180000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
:
Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
        Memory at 90200000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=09, subordinate=0c, sec-latency=176
        Memory window 0: 54000000-57fff000 (prefetchable)
        Memory window 1: 58000000-5bfff000
        I/O window 0: 00004400-000044ff
        I/O window 1: 00004800-000048ff
        16-bit legacy interface ports at 0001

02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
        Subsystem: Hewlett-Packard Company NC6000 laptop
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at 90000000 (64-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at 90010000 [disabled] [size=64K]
        Capabilities: <access denied>

(END)

---

### Post by MavsX on 2009-04-19
> **Shadow121 said:**
> lspci in the terminal and post the output.

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
mavsx@mavsx-laptop:~$

---

### Post by RedSingularity on 2009-04-19
I am not seeing it under PCI cards.  What type of wireless adapter is it?  PCMCIA?  USB?

---

### Post by MavsX on 2009-04-19
yeah, i know i'm not seeing it either!

i'm assuming it is built in.  There is a little WiFi button built into the laptop at the top above the F1-F12 keys.  I don't have a pcmcia card plugged in and i am not using any usb adaptors.

Let me get a screwdriver and take off a few panels on this laptop and see what it is..i'm assuming it is intel..(i can't remember what it listed when it was running XP pro.  Stay tuned.  and thanks for the help by the way.

---

### Post by RedSingularity on 2009-04-19
No problem.  When you get a chance type "iwlist" in the terminal.

---

### Post by MavsX on 2009-04-19
Hey,

Alright looks like there is no WiFi card physically installed.  I opened up a slot on the backside of NC6000, and nothing is there.  Which would make sense, since nothing is listed.  

I'm going to drive to my office because I've got a bunch of parts to NC8000 laptops.  I'm going to try and throw in a WiFi card that I have at work.

Thanks again.  I'll definitely post back here and let you know what happens.

---

### Post by RedSingularity on 2009-04-19
Sounds good.

---

### Post by MavsX on 2009-04-19
Hey, well i went to work and sure enough i had a intel WiFi card laying around from when i took apart some HP NC8000's for parts.  I plugged it in, rebooted a few times.  Set up a quick wireless network here at work, and i am online right now.  It was easy.  

So i guess that's it. Problem solved.


Thanks again for your help man.

---

### Post by MavsX on 2009-04-19
> mavsx@mavsx-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
**[B]02:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)**[/B]
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
mavsx@mavsx-laptop:~$


there it is.  thanks bro

---

### Post by RedSingularity on 2009-04-19
No problem.  :)

---

