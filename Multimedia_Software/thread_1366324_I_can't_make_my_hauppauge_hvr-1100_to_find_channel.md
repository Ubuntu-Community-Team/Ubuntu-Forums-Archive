---
title: "I can't make my hauppauge hvr-1100 to find channels with ubuntu 9.10 karmic"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Alvarlinux on 2009-12-28
Hello everybody,


            I need some help or advice with my tv tuner, since it doesn't find any channels, probably because Karmic recognises my Hauppauge HVR-1100 tv tuner card as a Philips card. I don't know what to do, nor what drivers to download, I don't even know whether that's the solution or not! So please, help me out before I decide to downgrade to Jaunty, with which everything used to work.


Thank you very much.

---

### Post by laceration on 2009-12-28
The card uses a Phillips chip, it is not being recognized wrongly.  The drivers are probably in the kernel for this but you likely need firmware.  Check out this page:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1110)

You set it up before, did you totally forget what you did before?  Did you do a fresh install or an upgrade?  Sometimes firmware gets put in a kernel specific directory and doesn't work with a new kernel.  Make sure you firmware is in /lib/firmware/

If the problem is not this, where are your channels, or what what program are you using to tune and watch TV.

---

### Post by Alvarlinux on 2009-12-28
Hello,


I made a fresh install but still doesn't work. I'm trying to make Mythtv, Me-Tv and even VLC to work, without success.


Thank you.

---

### Post by xc3RnbFO8P on 2009-12-28
In Terminal show the output of:
> dmesg
> lspci -nv


---

### Post by Alvarlinux on 2009-12-28
alberto@alberto-karmicdesktop:~$ lspci -nv
00:00.0 0600: 10de:07c5 (rev a2)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 0500: 10de:07cb (rev a2)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0

00:01.0 0500: 10de:07cd (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:01.1 0500: 10de:07ce (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:01.2 0500: 10de:07cf (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:01.3 0500: 10de:07d0 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:01.4 0500: 10de:07d1 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:01.5 0500: 10de:07d2 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:01.6 0500: 10de:07d3 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:02.0 0500: 10de:07d6 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:03.0 0601: 10de:07d7 (rev a2)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0
    I/O ports at 4f00 [size=256]

00:03.1 0c05: 10de:07d8 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 4900 [size=64]
    I/O ports at 4d00 [size=64]
    I/O ports at 4e00 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:03.2 0500: 10de:07d9 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:03.3 0b40: 10de:07da (rev a2)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
    Memory at fea80000 (32-bit, non-prefetchable) [size=512K]

00:03.4 0500: 10de:07c8 (rev a1)
    Subsystem: 1025:0137
    Flags: 66MHz, fast devsel

00:04.0 0c03: 10de:07fe (rev a1) (prog-if 10)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fea7f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:04.1 0c03: 10de:056a (rev a1) (prog-if 20)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fea7ec00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:08.0 0101: 10de:056c (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:09.0 0403: 10de:07fc (rev a1)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at fea78000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:0a.0 0604: 10de:056d (rev a1) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>

00:0b.0 0604: 10de:056e (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0c.0 0604: 10de:056f (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0d.0 0604: 10de:056f (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:0e.0 0104: 10de:07f8 (rev a2) (prog-if 85)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 27
    I/O ports at d480 [size=8]
    I/O ports at d400 [size=4]
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=16]
    Memory at fea7c000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:0f.0 0200: 10de:07dc (rev a2)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 28
    Memory at fea73000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at c880 [size=8]
    Memory at fea7e800 (32-bit, non-prefetchable) [size=256]
    Memory at fea7e400 (32-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:10.0 0300: 10de:07e5 (rev a2)
    Subsystem: 1025:0137
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at fea40000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

01:06.0 0480: 1131:7133 (rev d1)
    Subsystem: 0070:6701
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

01:07.0 0c00: 1106:3044 (rev c0) (prog-if 10)
    Subsystem: 1462:309d
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at febff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

---

### Post by laceration on 2009-12-28
If you did a fresh install you wiped out all the stuff that would make your card work.  The link in my prev post has instructions on how to set up your card.  If you did not save any of your home directory you will have to scan for channels too.

---

### Post by Ferux on 2010-01-23
Has this problem been solved? I'm also thinking of buying this card.

---

