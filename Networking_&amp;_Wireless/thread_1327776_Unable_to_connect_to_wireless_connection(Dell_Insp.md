---
title: "Unable to connect to wireless connection(Dell Inspiron 1300)"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by schwim on 2009-11-15
Hi there everyone,

I just replaced my Dreamlinux install with 9.10, since I like running it so much on my main machine.  Install went swimmingly and I was at the desktop in just a few minutes.

Once there however, I've run into a snag.  The system doesn't seem to be able to detect any wireless networks.  I tried manually entering the details, but it just won't connect.

Using Dreamlinux, I just had to enter the WEP key(it detected the network without any intervention) and I'm posting this from the Win install on the same machine, so I know the adapter is working.

It's a Dell Inspiron 1300.  The Windows device manager states that it's a Dell wireless 1470 Dual Band WLAN mini-PCI card.  Is this supported by 9.10?  I'd feel pretty silly getting rid of Dreamlinux for a system that I couldn't use wireless on :)

Thanks in advance to anyone that can help me get connected!
json

---

### Post by gertjan_hofman on 2009-11-15
thats a broadcom chip. Might need NDIS wrapper.  See e.g.

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by schwim on 2009-11-15
My lord, if I replaced a working system with one that requires a how-to from 2006 to get working wireless, I'll definitely be bummed.

I'll also be moving back to an OS that doesn't require a three page tutorial to get wireless on four year old technology :)

thanks,
json

---

### Post by PRC09 on 2009-11-15
See if this helps:

[http://ubuntuforums.org/showthread.php?t=1325932](http://ubuntuforums.org/showthread.php?t=1325932)

---

### Post by schwim on 2009-11-15
I can't thank you enough.  Easy-peasy and wireless is working like a charm.

Thanks again!

---

### Post by gertjan_hofman on 2009-11-16
hmm....I was kind of assuming you had tried THAT...  :)

---

### Post by schwim on 2009-11-16
I guess that's why he was much more helpful than you were.  He didn't assume anything :)

---

### Post by rdhs100 on 2010-04-08
Yesp, this solution worked for me too.  I have an Inspiron 1300 which is apparently equipped with a Broadcom BCM4318 wireless card.  I followed the advice on other threads to begin from scratch, so I reinstalled Ubuntu 9.10.  I immediately did a software update (System > Administration > Update Manager) and installed updates to everything. 

Once I had done so (and only after I had done so) the B43 Wireless driver became available.

After a restart, the wireless card was working properly.

A relief, as discussions on how to achieve the same effect in earlier versions of Ubuntu involve a lot of downloading of various ndiswrapper packages, which is very time consuming for a total N00b like yrstrly.

---

### Post by netjjordan on 2010-12-30
I tried following the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access)

On a brand new 10.10 install on a Dell Inspiron 1300 but no luck

I was doing the "b43 no internet access" route, but at this stage:

Under the desktop menu **System > Administration > Hardware/Additional Drivers**, the **b43** drivers can be activated for use

No drivers were showing. Also, the menu entry was simply called "Additional Drivers"

Thanks for any help

Julian

---

### Post by PatchesTheCaveman on 2010-12-30
Hi netjordan!  I'm sorry your having trouble with you're wireless card.

Please go to Applications > Accessories > Terminal in your top panel.  Then type the following and press Enter:
```
lspci -v
```

Copy and paste what appears into a post here.  That will give us information about your hardware and the drivers installed so we can figure out what's going on.

Thank you!

---

### Post by netjjordan on 2011-01-01
Hi

Here it is - thanks a lot:


00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at eff8 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0
	Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 20000000-201fffff
	Prefetchable memory behind bridge: 0000000020200000-00000000203fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfc00000-dfdfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at bf60 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: dfb00000-dfbfffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 01c9
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Kernel driver in use: ata_piix

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Device 01c9
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at dfbfc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

Yours, Julian

---

