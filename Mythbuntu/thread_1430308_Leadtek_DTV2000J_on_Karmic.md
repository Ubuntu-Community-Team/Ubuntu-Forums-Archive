---
title: "Leadtek DTV2000J on Karmic"
date: 2010-03-15
forum: Mythbuntu
---

### Post by sickgemini on 2010-03-15
Hi,

Hope someone can help out with this one.
I have the Leadtek DTV2000 Revision J capture card.
After some inital work, I got Mythbuntu 8.04 running and have used it for some time with no problems.

I've now done a fresh install of Karmic 9.10 and can't get the capture card to work.

I've added cx88-dvb to /etc/modules so it now looks like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

cx88-dvb
lp

```

I've updated /etc/modprobe.d/options.conf to this:
```

options cx88xx card=51

```

From all I have read this is all that is required to get the card recognised but it does not appear in the mythbackend setup.

When I run modprobe I get the following:
```

$ sudo modprobe cx88-dvb
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

```

I've read that people have got this card working with Karmic. What am I missing?

Thanks,

---

### Post by laffinet on 2010-03-15
This card is supported out of the box by 9.10, no need to modify options.conf and modules.

Try commenting out those lines you added to the files, reboot, go into backend setup, capture cards. You should be able to select your card from there.

Worked for me without a problem.

PS I saw comments about a "+" versions in this [thread]("http://ubuntuforums.org/showpost.php?p=7762068&postcount=5"). You might want to double check what version you have.

---

### Post by istvanv on 2010-03-16
You can also find out the exact version of the card with this command:
```
  /sbin/lspci -v | grep LeadTek
```
If it prints "Device 665e", then you have the original DTV2000 H. Device 6f2b is revision J, and device 6f42 is the newer "Plus" version with XC4000 tuner. If you do have the "Plus" card, then it is still possible to get it to work fully (analog+digital+radio+IR) under Linux using [this](http://www.sharemation.com/IstvanV/v4l/xc4000.html) "unofficial" driver.

---

### Post by sickgemini on 2010-03-16
Thanks laffinet
Good to know it runs out of the box. I've removed the /etc/modprobe.d/options.conf and removed the line from the /etc/modules file but still no luck.

Thanks istvanv
I've tried this and this is where it gets really interesting.
lspci -v | grep LeadTek
Returns nothing.
The full output of 'lspci -v' is pasted below.
It doesn't list the capture card. The card is definitely seated in the PCI slot.
I am running ASUS A7N8X Deluxe motherboard.
I had to disable USB2 to get the on board USB working. Maybe there is a problem with the PCI slots too.

The full output of 'lspci -v' is:
```

00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device 80ac
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-nvidia
	Kernel modules: nvidia-agp

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device 80ac
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device 80ac
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device 80ac
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device 80ac
	Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device 80ac
	Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
	Subsystem: ASUSTeK Computer Inc. Device 80ad
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 0c11
	Flags: 66MHz, fast devsel, IRQ 5
	I/O ports at e000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at e2087000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at e2082000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 80a7
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at e2086000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at e400 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at e2000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 8095
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at d000 [size=256]
	I/O ports at d400 [size=128]
	Memory at e2080000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000a000-0000bfff
	Memory behind bridge: e0000000-e1ffffff
	Prefetchable memory behind bridge: 30000000-300fffff
	Kernel modules: shpchp

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 0c11
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: dc000000-ddffffff
	Prefetchable memory behind bridge: 30100000-301fffff
	Kernel modules: shpchp

00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 809a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at e2084000 (32-bit, non-prefetchable) [size=2K]
	Memory at e2085000 (32-bit, non-prefetchable) [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: de000000-dfffffff
	Prefetchable memory behind bridge: d0000000-d7ffffff
	Kernel modules: shpchp

01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
	Subsystem: Silicon Image, Inc. Device 6112
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	I/O ports at a000 [size=8]
	I/O ports at a400 [size=4]
	I/O ports at a800 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at b000 [size=16]
	Memory at e1000000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 30000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil

02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Ethernet Controller [Tornado] (rev 40)
	Subsystem: ASUSTeK Computer Inc. Device 80ab
	Flags: bus master, medium devsel, latency 64, IRQ 22
	I/O ports at c000 [size=128]
	Memory at dd000000 (32-bit, non-prefetchable) [size=128]
	[virtual] Expansion ROM at 30100000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: 3c59x
	Kernel modules: 3c59x

03:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 807b
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 19
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at df000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

```

---

### Post by laffinet on 2010-03-16
Could be a problem with your BIOS/interrupt setup.

Check your BIOS and see if anything's there that might need changing.

I'm no expert but I would start looking in that direction.

After booting, type dmesg in a terminal and check what that gives you.

Try ```
cat /proc/interrupts 
``` and post the output

Have a look [here]("https://help.ubuntu.com/community/DebuggingIRQProblems"), try the different boot options ([here's]("https://help.ubuntu.com/community/BootOptions") how to apply, section *Change Boot Options Temporarily For An Existing Installation*

---

### Post by sickgemini on 2010-03-18
Thanks guys I've got it working now.
I've moved the capture card to a different slot and it all came up so I'm very happy.
Thanks again.

---

### Post by laffinet on 2010-03-18
Good to hear. 

You might want to mark the thread as "solved". 
*Thread tools->mark as solved*

---

