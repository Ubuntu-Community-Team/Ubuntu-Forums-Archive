---
title: "No sounds on Ubuntu... nothing seems to work."
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by Sharkymark on 2007-08-18
I installed ubuntu about a month ago and for life of me can not get my speakers / sound to work.  I have no idea what the problem is, I have gone through the websites / help online and nothing has me gotten me a single sound.  
Everything is turned on in alsamixer.

Any help or if you need any other information would be greatly appreciated - thanks!!


Here's some info: 

card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

lspci -v 
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
        Subsystem: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 11) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e4000000-e5ffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at b800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 24c2
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 24c2
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at b400 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology Unknown device 5004
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at e6100000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e6000000-e60fffff

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corporation Unknown device 24c2
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at cc00 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 24c2
        Flags: medium devsel, IRQ 9
        I/O ports at 5000 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Giga-byte Technology GA-8PE667 Ultra
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at d400 [size=256]
        I/O ports at d800 [size=64]
        Memory at e6102000 (32-bit, non-prefetchable) [size=512]
        Memory at e6103000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Radeon R200 QL [Radeon 8500 LE]
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 16
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e4000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:01.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at a000 [size=256]
        Memory at e6005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player/OEM
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at a400 [size=32]
        Capabilities: <access denied>

02:02.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 32
        I/O ports at a800 [size=8]
        Capabilities: <access denied>

02:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at e6004000 (32-bit, non-prefetchable) [size=2K]
        Memory at e6000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by linuxwizard on 2007-08-18
check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF. You can select which tracks/switches are visible in Volume Control  under Edit->Preferences.

---

### Post by Gremlinzzz on 2007-08-18
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

---

### Post by Sharkymark on 2007-08-19
> **linuxwizard said:**
> check that your switches are set correctly - for instance that if you use the analog output the analog switch is set ON or that the digital or S/PDIF switch is set OFF. You can select which tracks/switches are visible in Volume Control  under Edit->Preferences.

Thanks - how do I see if I am using analog or digital output?

---

### Post by linuxwizard on 2007-08-19
On your sound card their are 2 plugins 1 analog & 1 digital. Did you try changing the switches ? I also have a Sound Blaster Audigy card. Every Ubuntu/Kubuntu install I do I have to change the switch from digital to analog. I do not know why it is detected that way.

---

### Post by Sharkymark on 2007-08-19
> **Sharkymark said:**
> Thanks - how do I see if I am using analog or digital output?

Thanks for your help guys, I was able to figure it out by playing with the switches!

---

### Post by UbuntuniX on 2007-08-20
I've got sound, but it tends to randomly not function in various apps.
Could you explain the switches?

---

### Post by Sharkymark on 2007-08-22
Hello again,

I thought I had everything working - everything was fine, and now all of the sudden the sound has stopped again. It happened while I was watching a video online and at the same time sound was coming from an ad on another website.  

I tried to close all of the windows, some of them "froze", and now my sound doesn't work again.

Any thoughts?

Thanks,
Mark

---

### Post by [Alsharifi] on 2007-08-29
hey,
ive had ubuntu for a long time now and ive never had audio problems,but today the comp was sitting here alseep and after using it for a little i relized that there was no sound.i dunno what cound have gone wrong.



00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01d2
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

