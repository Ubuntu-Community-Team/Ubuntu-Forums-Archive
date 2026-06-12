---
title: "Unable to get HDMI Audio to appear in aplay -l"
date: 2009-06-30
forum: Multimedia Software
---

### Post by kevlyn on 2009-06-30
I have been trying to get the HDMI passthrough on my videocard working in Ubuntu 9.04. It works in windows. I have searched and tried many things until finally my sound completly quit working. Followed the sticky'ed thread here to reinstall sound. I now have sound back except for system sounds such as startup, shutdown, etc. (if anyone knows how to get this working let me know but it's not critical.) 

I do have the SPDIF output on the motherboard going to the NVIDIA GTX 260 but I can't get the output out of the SPDIF. Any Help would be appreciated

Here is output from lspci -v
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 82d3
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fa000000-fe9fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at c880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at cc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: ASUSTeK Computer Inc. Device 82fe
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fea00000-feafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at c080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at c400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at c480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f9fff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
    I/O ports at bc00 [size=8]
    I/O ports at b880 [size=4]
    I/O ports at b800 [size=8]
    I/O ports at b480 [size=4]
    I/O ports at b400 [size=32]
    Memory at f9ffe800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: ASUSTeK Computer Inc. Device 82d4
    Flags: medium devsel, IRQ 15
    Memory at f9fff400 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT200 [GTX260-216] (rev a1)
    Subsystem: nVidia Corporation Device 064b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fe980000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

02:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device 8226
    Flags: bus master, fast devsel, latency 0, IRQ 2299
    Memory at feac0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: ATL1E
    Kernel modules: atl1e

04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 8294
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at febff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

```and aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```The only thing I can find is it's possible that alsa driver version 1.0.20 may provide updates to the drivers but I'm unable to get that version installed as alsa always reports 1.0.18 when running cat /proc/asound/version. I've tried following the instructions on the sticky'ed thread for compiling from alsa source downloaded from alsa and same thing. 

Please Help ](*,)

---

### Post by kevlyn on 2009-07-01
Has anyone run into this or have anything to try?

I've continued looking around but haven't found anything new.

Thanks in advance

---

### Post by bmhm on 2009-10-04
Same problem here.

Using Laptop Acer Aspire 5738 (aka 5738G).
Graphics Card: NVidia GeForce G 105M (G98).

I installed the latest driver (which is an 185.xx), but I still get no HDMI support. However, There might be support some day.

Watch out you always try the latest drivers. Once you found working drivers, stick to them.  

Hope that helps. If you find it hard to upgrade drivers, search for EnvyNG.

Regards,
Ben

---

