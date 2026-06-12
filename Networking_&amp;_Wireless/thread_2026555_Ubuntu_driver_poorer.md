---
title: "Ubuntu driver poorer?"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by icegood on 2012-07-15
I wonder why when signal is weak connecting under windows via wireles is OK while under ubuntu it cannot do so for a long time. Does anyone has same issue?
Under windows
Atheros AR9285 Wireless Network Adapter
PCI\VEN_168C&DEV_002B&SUBSYS_10891A3B&REV_01
PCI\VEN_168C&DEV_002B&SUBSYS_10891A3B
PCI\VEN_168C&DEV_002B&CC_028000
PCI\VEN_168C&DEV_002B&CC_0280
driver  9.2.0.427 from atheros.
Under ununtu - embedded driver for 12.04
Laptop - asus k52d

---

### Post by Kirk Schnable on 2012-07-15
Can you give me the output of:

```
lspci -v
```

Also, let's look at your signal levels. While you're connected to your wireless, get me the output of:

```
iwconfig
```

Kirk

---

### Post by icegood on 2012-07-21
Now ready to reply. 
iwconfig
```

wlan0     IEEE 802.11bgn  ESSID:"ice dd-wrt"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: BC:F6:85:43:18:02   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:3   Missed beacon:0


```
lspci -v :
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
    Subsystem: ASUSTeK Computer Inc. Device 1bf2
    Flags: bus master, 66MHz, medium devsel, latency 32
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=03, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fdf00000-fe8fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 1bf2
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    Memory behind bridge: fea00000-feafffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 1bf2
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe900000-fe9fffff
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Port (Slot+), MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Device 1bf2
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [110] Virtual Channel
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 43
    I/O ports at f090 [size=8]
    I/O ports at f080 [size=4]
    I/O ports at f070 [size=8]
    I/O ports at f060 [size=4]
    I/O ports at f050 [size=16]
    Memory at feb0a000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] MSI: Enable+ Count=1/4 Maskable- 64bit+
    Capabilities: [70] SATA HBA v1.0
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: ahci

00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb09000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb08000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb07000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb06000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 41)
    Flags: 66MHz, medium devsel
    Kernel driver in use: piix4_smbus
    Kernel modules: sp5100_tco, i2c-piix4

00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 11b3
    Flags: bus master, slow devsel, latency 32, IRQ 16
    Memory at feb00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=64

00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
    Memory at feb05000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1313
    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 17
    Memory at feb04000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
    Capabilities: [e4] Debug port: BAR=1 offset=00e0
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
    Flags: fast devsel
    Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Flags: fast devsel
    Capabilities: [f0] Secure device <?>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
    Flags: fast devsel

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1bf2
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fdf20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fdf00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx_updates, radeon

01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Radeon HD 5400/6300 Series]
    Subsystem: ASUSTeK Computer Inc. Device 1bf2
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fdf40000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fea00000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
    Capabilities: [170] Power Budgeting <?>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

05:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device 1a07
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe907000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80) (prog-if 01)
    Subsystem: ASUSTeK Computer Inc. Device 1a07
    Flags: fast devsel, IRQ 18
    Memory at fe906000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel modules: sdhci-pci

05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device 1a07
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fe905000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 80)
    Subsystem: ASUSTeK Computer Inc. Device 1a07
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at fe904000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-

05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 1905
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe900000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at d100 [size=128]
    I/O ports at d000 [size=256]
    Capabilities: [68] Power Management version 3
    Capabilities: [50] Express Legacy Endpoint, MSI 00
    Capabilities: [40] MSI-X: Enable- Count=8 Masked-
    Capabilities: [70] MSI: Enable+ Count=1/8 Maskable+ 64bit+
    Kernel driver in use: jme
    Kernel modules: jme

```

---

### Post by icegood on 2012-07-22
Checked. Same story in unubuntu, kubuntu and xubuntu. Seems that drivers frm live CD are OK. but updated newest ones are not OK. Hope it helps

---

### Post by bakegoodz on 2012-07-22
The Atheros Windows driver has more programed into it overcomes noisy wifi enviroments. So you can get better performace with the Windows driver in some enviroments.

---

### Post by icegood on 2012-07-23
> **bakegoodz said:**
>  So you can get better performace with the Windows driver in some enviroments.
Maybe perfomance under Windows is really better, i hasn't checked that. At least in case when linux driver already connected i have satisfactory speed. The problem only that i cannot connect in satisfactory way. So it's rather sowtware bug.

---

