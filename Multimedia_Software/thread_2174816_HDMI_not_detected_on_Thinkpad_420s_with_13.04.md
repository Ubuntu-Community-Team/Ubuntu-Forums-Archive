---
title: "HDMI not detected on Thinkpad 420s with 13.04"
date: 2013-09-16
forum: Multimedia Software
---

### Post by Severin_Wischmann on 2013-09-16
I tried to use a second screen over HDMI, which I just could not manage to set up. The built laptop has an integrated Intel Graphics and a NVIDIA NVS 4200m. Also I got rid of unity and am using gnome3, if that is relevant

After googling and trying out a lot I thought I'd ask here.
Stuff I tried: [http://ubuntuforums.org/showthread.php?t=1726575&page=2&p=10706900#post10706900](http://ubuntuforums.org/showthread.php?t=1726575&page=2&p=10706900#post10706900), [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) (there's no driver listed in software center, tried the rest)

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 32767 x 32767
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 310mm x 174mm
   1600x900       60.0*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```

```
$ lspci -v 
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Lenovo Device 21d2
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 21d3
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 21d2
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at f1625000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei

00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])
    Subsystem: Lenovo Device 21d2
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
    I/O ports at 40b0 [size=8]
    Memory at f162c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
    Subsystem: Lenovo Device 21ce
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f1600000 (32-bit, non-prefetchable) [size=128K]
    Memory at f162b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 4080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 21d2
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f162a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 21d2
    Flags: bus master, fast devsel, latency 0, IRQ 50
    Memory at f1620000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f1500000-f15fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0d00000-f14fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f0bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
    Memory behind bridge: f0c00000-f0cfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 21d2
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f1629000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci

00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
    Subsystem: Lenovo Device 21d2
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 21d2
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 46
    I/O ports at 40a8 [size=8]
    I/O ports at 40bc [size=4]
    I/O ports at 40a0 [size=8]
    I/O ports at 40b8 [size=4]
    I/O ports at 4060 [size=32]
    Memory at f1628000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 21d2
    Flags: medium devsel, IRQ 10
    Memory at f1624000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]

03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 3e)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f1500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi

05:00.0 System peripheral: Ricoh Co Ltd MMC/SD Host Controller (rev 07)
    Subsystem: Lenovo Device 21d2
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f0d00000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci

0d:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 21d2
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f0c00000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

```

There is no xorg.conf (I deleted the ones generated by nvidia-xconfig). In BIOS I now set Display to Integrated Graphics and disabled OS detection of Optimus.

---

### Post by Bucky Ball on 2013-09-16
*Thread moved to **Multimedia & Video**.*

Welcome. You'll have more luck here.

---

### Post by Linuxisfast on 2013-09-16
Hi remove Ubuntu 13.04 and install 12.04.3 latest and Nvidia Optimus will be enabled right out of the box, no need to install or add or tweak anything. HDMI works very well with sound on my dual graphic system.

---

### Post by Severin_Wischmann on 2013-09-17
@Bucky Ball: Thanks for moving

@Linuxisfast: Thanks, but I was hoping to not reinstall everything again to be able to use my HDMI port...

---

### Post by Linuxisfast on 2013-09-17
> **Severin_Wischmann said:**
> @Bucky Ball: Thanks for moving

@Linuxisfast: Thanks, but I was hoping to not reinstall everything again to be able to use my HDMI port...


I understand your peril but this one is tested to work here and its also a LTS.

---

### Post by Bucky Ball on 2013-09-17
> **Linuxisfast said:**
> I understand your peril but this one is tested to work here and its also a LTS.

Which means it will work until April 2017 (unless there is a radical change of how an LTS is updated/upgraded/supported). 13.04 is supported for nine months from this April (til January 2014). LTS = 5 years support. Everything else used to be 18 months, that is now 9 months. ;)

Installing 12.04 LTS might take not much time (or maybe a bit more than that) but you are covered for the next four and some years. You'll be reinstalling or upgrading to a new release next April anyway with 13.04. Good luck either way.

BUT, that doesn't mean you shouldn't continue to try and fix this. I use a really simple app called ARandR. It is in the repos. Have a look, might help. Search for 'arandr'. Install, launch. You should be able to set up each monitor how you like.

---

