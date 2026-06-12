---
title: "nu2ubuntu -- dishnetwork and ubuntu"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by simplybrilliant on 2008-01-14
Hi all, 

Just recently installed Ubuntu desktop.  Still finding my way around this elegant operating system.  However, I do need help on how to get my dishnetwork to work in Ubuntu. 

The dishnetwork worked fine and very well using WinDVR and could watch TV on my computer.  So all the hardware is set; I just need the software program to run dishnetwork in Ubuntu.

Anyone? 

Thanks

---

### Post by tgalati4 on 2008-01-15
>sudo apt-get install xawtv

>man xawtv

What kind of card are you using?

Post the output of:

>lspci -v

---

### Post by simplybrilliant on 2008-01-15
<<first of all thanks for responding.  Here's the out:  lspci -v >>



00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at f2100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at b000 [size=8]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at a000 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at a400 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at a800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ac00 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f2180000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: f0000000-f1ffffff
        Prefetchable memory behind bridge: f2000000-f20fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]
        Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: medium devsel, IRQ 3
        I/O ports at 0500 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Elitegroup Computer Systems Unknown device 1867
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at b800 [size=256]
        I/O ports at bc00 [size=64]
        Memory at f2181000 (32-bit, non-prefetchable) [size=512]
        Memory at f2182000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: PROLINK Microsystems Corp Unknown device 4011
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at f2000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

01:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: PROLINK Microsystems Corp Unknown device 4011
        Flags: medium devsel, IRQ 18
        Memory at f2001000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

01:01.0 Communication controller: Agere Systems LT WinModem (rev 02)
        Subsystem: Agere Systems LT WinModem
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at f1004000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 9000 [size=8]
        I/O ports at 9400 [size=256]
        Capabilities: <access denied>

01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: Elitegroup Computer Systems Marvell 88E8001 Gigabit Ethernet Controller (ECS)
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at f1000000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at 9800 [size=256]
        [virtual] Expansion ROM at f2020000 [disabled] [size=128K]
        Capabilities: <access denied>

01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at f1005000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at 9c00 [size=128]
        Capabilities: <access denied>

---

### Post by tgalati4 on 2008-01-16
So, it appears that you are not using a satellite tuner card.  Based on your lspci, you have a brooktree video capture chipset:


01:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
Subsystem: PROLINK Microsystems Corp Unknown device 4011
Flags: bus master, medium devsel, latency 32, IRQ 18
Memory at f2000000 (32-bit, prefetchable) [size=4K]
Capabilities: <access denied>

01:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
Subsystem: PROLINK Microsystems Corp Unknown device 4011
Flags: medium devsel, IRQ 18
Memory at f2001000 (32-bit, prefetchable) [size=4K]
Capabilities: <access denied>

So I assume that you are running a composite/s-video cable from your dishnetwork box to your PC and now you are trying to see the video.  xawtv should work assuming you have the appropriate module loaded to wake up the brooktree chipset.

A simple check, do you have the file /dev/video or /dev/video0?

>ls -la /dev/video

or

>ls -la /dev/video0

If so, then xawtv should display the video on that device.

---

### Post by simplybrilliant on 2008-01-16
thanks.  I'll try it when I get home.  You know, I record a lot of tennis matches; especially now with the Australian Open; and I need to transfer recorded matches from my Dishnetwork DVR to my computer's hard drive; so that I can delete previously recorded stuff on my DVR.  All 80 hours of DVR is used up! 

So I will try to get this thing working as soon as possible, however, i might revert back to Windows XP and when the Australian Open is over; I'll try ubuntu again.  Thanks again.

---

### Post by tgalati4 on 2008-01-18
If your dish network box has a firewire port, you MAY be able to add an additional firewire drive.  Beware that some boxes have the connection but no circuitry inside (as one of my collegues found out!).  You will have to do a google search on your particular model to see what others have done.  You are not alone with the recording limit.

---

