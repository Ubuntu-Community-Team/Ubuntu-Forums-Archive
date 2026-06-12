---
title: "Wireless connection disconnects without any clear reason"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by Naygral on 2012-12-22
I am using a newly installed Xubuntu 12.10 32 bit with only the programs that came with it, I have updated it with all the latest updates. Nothing else has been changed by me.

I can connect just fine to my wireless connection and be on the internet, but after a random amount of time (between 30 minutes and 1 hour) I will get kicked out and the computer will ask for my wireless password again. After I have written the correct password the computer will try to connect but then ask for the password again after a few seconds.

The computer will now not connect to the internet until I restart my computer, the internet will then work perfectly again for the next 30-1 hour before it repeats the same pattern.

By using "lspci | grep Wireless" I got this, not sure if this is the appropriate information that is needed to find a solution:

**02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)**

This is my first install of any Linux distro and I would appreciate that if additional information is needed to solve this problem, then please do tell how I acquire said information.

---

### Post by steeldriver on 2012-12-22
can you either run lspci again with the -v (verbose) option or run lshw, and make a note of the driver? it should be something like 'ath9k' or 'ath5k'

```
lspci -v

lshw -C network
```

---

### Post by Naygral on 2012-12-22
> **steeldriver said:**
> can you either run lspci again with the -v (verbose) option or run lshw, and make a note of the driver? it should be something like 'ath9k' or 'ath5k'

```
lspci -v

lshw -C network
```

This is what I get when I use lspci -v:
If there's a need of more information, you are more than welcome to tell me how to get it!

```
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7e00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f7d00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0
    Memory at f7e80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8437
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 7f700000-7f8fffff
    Prefetchable memory behind bridge: 000000007f900000-000000007fafffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7f00000-f7ffffff
    Prefetchable memory behind bridge: 000000007fb00000-000000007fcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7cf7c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=32]
    Memory at f7cf7800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: medium devsel, IRQ 11
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device 8468
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbff0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

```

---

### Post by steeldriver on 2012-12-22
OK well the ath9k driver has historically had some problems with hardware encryption - I'm a bit out of the loop so this may not be the issue but it's something to try:

1. remove the driver module and re-insert it with hw encryption turned off

```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```2. if that works (no errors) and the connection stops disconnecting, you can make it persist across reboots by adding the nohwcrypt parameter to a config file

```
 echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```

---

