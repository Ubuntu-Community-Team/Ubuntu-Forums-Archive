---
title: "ALSA sound not working after yesterday's update."
date: 2010-10-25
forum: Multimedia Software
---

### Post by anthony62490 on 2010-10-25
At least, I think it was the update that broke it. Anyway, my sound was working fine yesterday.

I have gone through [this]("http://ubuntuforums.org/showthread.php?t=205449") thread to try and fix my sound, and it appears that my sound card has been uninstalled.

Step 1. aplay -l
```
aplay: device_list:235: no soundcards found...
```

Step 2. lspci -v
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: ec000000-edffffff
	Prefetchable memory behind bridge: e4000000-ebffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d400 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at ee100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: ee000000-ee0fffff
	Prefetchable memory behind bridge: 40000000-400fffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 5770
	Flags: medium devsel, IRQ 255
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

**00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)**
	Subsystem: Micro-Star International Co., Ltd. Device 5790
	Flags: bus master, medium devsel, latency 0, IRQ 255
	I/O ports at e000 [size=256]
	I/O ports at e400 [size=64]
	Memory at ee101000 (32-bit, non-prefetchable) [size=512]
	Memory at ee102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: **snd-intel8x0**

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 03b3
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Memory at e8000000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at e8080000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, rivafb

02:0b.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 05) (prog-if 10)
	Subsystem: Risq Modular Systems, Inc. Device 5811
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at ee011000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 577c
	Flags: bus master, medium devsel, latency 32, IRQ 23
	I/O ports at c000 [size=256]
	Memory at ee010000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 40000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: epl, 8139too, 8139cp
```
So my sound card is being detected, but it is not installed.

Step 3. I found the module in bold at [this]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0") page.
So I looked for the package, and it does exist.
```
sudo modprobe snd-
Display all 209 possibilities? (y or n)
[...]
snd-atiixp               snd-indigodjx            snd-soc-ak4104
snd-atiixp-modem         snd-indigoio             snd-soc-ak4535
snd-au8810               snd-indigoiox            snd-soc-core
snd-au8820               **snd-intel8x0**      snd-soc-cs4270
snd-au8830               snd-intel8x0m            snd-soc-l3
snd-aw2                  snd-interwave            snd-soc-pcm3008
snd-azt2320              snd-interwave-stb        snd-soc-spdif
[...]

```

So I tried to install it. This is where I am having problems.
```
sudo modprobe snd-intel8x0
[COLOR="Red"]WARNING:[/COLOR] All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
[COLOR="Red"]FATAL:[/COLOR] Error inserting snd_intel8x0 (/lib/modules/2.6.31-22-generic/kernel/sound/pci/snd-intel8x0.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Am I going about this the right way? Any ideas on how to fix this?

EDIT: Last time my sound wasn't working, I was directed to [this]("http://ubuntuforums.org/showthread.php?t=1046137") thread. The script from this thread might work again, but if it will just be erased after every update, I'd like something a bit more permanent.

---

### Post by lidex on 2010-10-25
> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk). 
Or you could try upgrading to maverick, which has alsa 1.0.23 by default.

---

### Post by anthony62490 on 2010-10-25
Yes, I suppose you're right. But it takes a lot of time and effort to re-customise the system from a fresh install. I'm too lazy. I'll reinstall after the April release.

For now, I guess I'll just run the script again and see what happens.

EDIT: The script worked. If anyone else had this issue, try the script if the troubleshooting thread doesn't help..

---

