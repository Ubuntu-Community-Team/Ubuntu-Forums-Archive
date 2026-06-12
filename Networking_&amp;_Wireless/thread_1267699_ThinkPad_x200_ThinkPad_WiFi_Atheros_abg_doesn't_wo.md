---
title: "ThinkPad x200 ThinkPad WiFi Atheros a/b/g doesn't work"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by SevinK on 2009-09-16
Hello,

I have read this post: [http://ubuntuforums.org/showthread.php?t=968715](http://ubuntuforums.org/showthread.php?t=968715)
since I ordered my ThinkPad x200 with the ThinkPad Wifi chipset (Atheros) a/b/g. I downloaded the madwifi snapshot and madwifi-hal snapshot from [http://snapshots.madwifi-project.org/madwifi-0.9.4/](http://snapshots.madwifi-project.org/madwifi-0.9.4/) and [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/) , respectively. I have build-essential installed and successfully compiled and installed via sudo make and sudo make install both of those madwifi files. 

After restarting my x200 and removing the ethernet cable, it still cannot recognize any wifi networks.

What's strange is that even my laptop doesn't list Atheros chipset...
Here's my lspci -v | less output

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Lenovo Device 20e0
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Lenovo Device 20e4
    Flags: bus master, fast devsel, latency 0, IRQ 2298
    Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Lenovo Device 20e4
    Flags: bus master, fast devsel, latency 0
    Memory at f2400000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
    Subsystem: Lenovo Device 20e6
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f2826800 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07) (prog-if 85 [Master SecO PriO])
    Subsystem: Lenovo Device 20ea
    Flags: 66MHz, fast devsel, IRQ 18
    I/O ports at 1828 [size=8]
    I/O ports at 180c [size=4]
    I/O ports at 1820 [size=8]
    I/O ports at 1808 [size=4]
    I/O ports at 1810 [size=16]
    Capabilities: <access denied>

00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07) (prog-if 02)
    Subsystem: Lenovo Device 20ec
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
    I/O ports at 1830 [size=8]
    Memory at f2624000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
    Subsystem: Lenovo Device 20ee
    Flags: bus master, fast devsel, latency 0, IRQ 2299
    Memory at f2600000 (32-bit, non-prefetchable) [size=128K]
    Memory at f2625000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1840 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Lenovo Device 20f0
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 1860 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Lenovo Device 20f0
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Lenovo Device 20f0
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 18a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Lenovo Device 20f1
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2826c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo Device 20f2
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f2620000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f2500000-f25fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0000000-f1ffffff
    Prefetchable memory behind bridge: 00000000f2900000-00000000f29fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Lenovo Device 20f0
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 18c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Lenovo Device 20f0
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 18e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Lenovo Device 20f0
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1c00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Lenovo Device 20f1
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f2827000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
    Subsystem: Lenovo Device 20f5
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Lenovo Device 20f8
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
    I/O ports at 1c48 [size=8]
    I/O ports at 183c [size=4]
    I/O ports at 1c40 [size=8]
    I/O ports at 1838 [size=4]
    I/O ports at 1c20 [size=32]
    Memory at f2826000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Lenovo Device 20f9
    Flags: medium devsel, IRQ 11
    Memory at f2827400 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1c60 [size=32]
    Kernel modules: i2c-i801

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device e020
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 2000 [size=256]
    Memory at f2500000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
Any ideas? Currently using Ubuntu 9.04 with 2.26.28-15

---

### Post by chili555 on 2009-09-16
> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. Device e020
Flags: bus master, fast devsel, latency 0, IRQ 11
I/O ports at 2000 [size=256]
Memory at f2500000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied> You may have ordered it with an Atheros chipset, but you have one with a Realtek chipset. Do you want to send it back or do you want to try to configure the Realtek? If the latter, please let us see:```
sudo lspci -v
```You can skip posting all the stuff that doesn't relate to the Realtek.

---

### Post by SevinK on 2009-09-16
Here it is:

```

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device e020
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 2000 [size=256]
    Memory at f2500000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-e0-4c-ff-fe-22-55-88

```
So, do I need the Realtek WLAN driver? How could have they messed this up...

And yes, I would like to enable/configure to use on Ubuntu 9.04

---

### Post by chili555 on 2009-09-16
Your card is not (yet, hopefully) supported in Linux. If you google, you will find no solution that I can find. *Now*, do you want to send it back??

---

### Post by SevinK on 2009-09-16
I see. I am currently dual-booting Win XP and Ubuntu and the wifi card works on XP. It is unfortunate that Linux does support this Realtek chipset...I guess Lenovo started to replace their Atheros chipsets with Realtek onces (since June 2009 AFAIK). Anyhow, I may just buy an external USB wifi adapter just so I can use it on linux as I just got off the phone with Lenovo and they will charge me money to replace the Realtek WLAN chipset in my laptop anyway.

Do you know any good and reliable USB wireless adapters that work fine on Ubuntu 9.04?

---

