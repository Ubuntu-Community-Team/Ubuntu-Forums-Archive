---
title: "One day, all sound gone from my 10.04 on X201i"
date: 2010-09-25
forum: Multimedia Software
---

### Post by droople on 2010-09-25
Hi

I install 10.04 by wubi on my X201i, everything worked fine, until today I realised that there's no sound anymore :(, it was there.

Nothing is muted.

I can't remember this happened after which package I installed.

Anyone can help?

Thank you in advance.


```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

dmesg | grep HDA
[   19.596514] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   19.596537] HDA Intel 0000:00:1b.0: setting latency timer to 64
```

```
jasonyu@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
    Subsystem: Lenovo Device 2193
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
    Subsystem: Lenovo Device 215a
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
    Subsystem: Lenovo Device 215f
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f2727000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
    Subsystem: Lenovo Device 2153
    Flags: bus master, fast devsel, latency 0, IRQ 31
    Memory at f2500000 (32-bit, non-prefetchable) [size=128K]
    Memory at f2525000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 1820 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
    Subsystem: Lenovo Device 2163
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f2727800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Lenovo Device 215e
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f2520000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0d, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0000000-f1ffffff
    Prefetchable memory behind bridge: 00000000f2800000-00000000f28fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: f2400000-f24fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
    Subsystem: Lenovo Device 2163
    Flags: bus master, medium devsel, latency 0, IRQ 19
    Memory at f2727c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0e, subordinate=0e, sec-latency=0
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: Lenovo Device 2166
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8a [Master SecP PriP])
    Subsystem: Lenovo Device 2169
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1840 [size=16]
    I/O ports at 1810 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: Lenovo Device 2167
    Flags: medium devsel, IRQ 11
    Memory at f2728000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 1860 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
    Subsystem: Lenovo Device 216a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 18a0 [size=8]
    I/O ports at 1894 [size=4]
    I/O ports at 1898 [size=8]
    I/O ports at 1890 [size=4]
    I/O ports at 1880 [size=16]
    I/O ports at 1850 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
    Subsystem: Lenovo Device 2190
    Flags: fast devsel, IRQ 11
    Memory at f2526000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
    Subsystem: Intel Corporation Device 1315
    Flags: bus master, fast devsel, latency 0, IRQ 32
    Memory at f2400000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
    Subsystem: Lenovo Device 2196
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
    Subsystem: Lenovo Device 2196
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
    Subsystem: Lenovo Device 2196
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
    Subsystem: Lenovo Device 2196
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Lenovo Device 2196
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
    Subsystem: Lenovo Device 2196
    Flags: bus master, fast devsel, latency 0

```

---

### Post by droople on 2010-09-26
bump

---

### Post by apexmonster on 2010-09-26
I just randomly lost sound, too.  I added myself to the "audio" group and it fixed it.  No clue why I had to do this or if there are security implications of doing so.  Hope this works for you, too!


```
sudo usermod -a -G audio username
```

---

