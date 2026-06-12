---
title: "Realtek Wi-Fi device"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by hex1616 on 2012-10-06
OS (Ubuntu 11.04, kernel 3.2.30 on laptop gigabyte q 2006) doesn't see wi-fi device.
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:90:f5:d3:72:6d  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4032 (4.0 KB)  TX bytes:4032 (4.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:95.81.42.59  P-t-P:195.128.182.50  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2423 errors:20 dropped:0 overruns:0 frame:0
          TX packets:2504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2041278 (2.0 MB)  TX bytes:365880 (365.8 KB
```iwconfig:
```
ppp0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.
```lspci -knn | grep "Eth\|Net" -A2 :
```
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel modules: rtl8723e
03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller [197b:0260] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:2100]
    Kernel driver in use: jme
```Help me anyone, pleas.

---

### Post by dniMretsaM on 2012-10-06
What's the output of this command:
```
lspci -v
```

---

### Post by hex1616 on 2012-10-06
```
00:00.0 Host bridge: Intel Corporation Cedarview DRAM Controller (rev 03)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation Cedarview Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 80200000 (32-bit, non-prefetchable) [size=1M]
    I/O ports at 40d0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 2
    Capabilities: [b0] Vendor Specific Information: Len=07 <?>
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 80300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 80100000-801fffff
    Prefetchable memory behind bridge: 0000000081000000-00000000811fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 2100
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: 80c00000-80dfffff
    Prefetchable memory behind bridge: 0000000080e00000-0000000080ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 2100
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 80000000-800fffff
    Prefetchable memory behind bridge: 0000000080900000-0000000080bfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 2100
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 80500000-806fffff
    Prefetchable memory behind bridge: 0000000080700000-00000000808fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: CLEVO/KAPOK Computer Device 2100
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 40a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 4080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 4060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 4040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at 80304400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [50] Subsystem: CLEVO/KAPOK Computer Device 2100

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 40c8 [size=8]
    I/O ports at 40dc [size=4]
    I/O ports at 40c0 [size=8]
    I/O ports at 40d8 [size=4]
    I/O ports at 4020 [size=16]
    Memory at 80304000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: medium devsel, IRQ 10
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

01:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8723
    Subsystem: Realtek Semiconductor Co., Ltd. Device 0726
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 3000 [size=256]
    Memory at 80100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-23-87-fe-ff-4c-e0-00
    Kernel modules: rtl8723e

03:00.0 Ethernet controller: JMicron Technology Corp. JMC260 PCI Express Fast Ethernet Controller (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at 80010000 (32-bit, non-prefetchable) [size=16K]
    I/O ports at 2100 [size=128]
    I/O ports at 2000 [size=256]
    Memory at 80000000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at 80900000 [disabled] [size=64K]
    Capabilities: [68] Power Management version 3
    Capabilities: [50] Express Legacy Endpoint, MSI 00
    Capabilities: [40] MSI-X: Enable- Count=8 Masked-
    Capabilities: [70] MSI: Enable+ Count=1/8 Maskable+ 64bit+
    Capabilities: [100] Device Serial Number 6d-72-d3-ff-ff-f5-90-00
    Kernel driver in use: jme
    Kernel modules: jme

03:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 80014200 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [100] Device Serial Number 6d-72-d3-ff-ff-f5-90-00
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90) (prog-if 01)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: fast devsel, IRQ 19
    Memory at 80014100 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [100] Device Serial Number 6d-72-d3-ff-ff-f5-90-00
    Kernel modules: sdhci-pci

03:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
    Subsystem: CLEVO/KAPOK Computer Device 2100
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 80014000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [100] Device Serial Number 6d-72-d3-ff-ff-f5-90-00
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms


```

---

### Post by mikewhatever on 2012-10-06
Here you go: [http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

### Post by hex1616 on 2012-10-07
In the fifth step:
```
# modprobe rtl8723e
FATAL: Error inserting rtl8723e (/lib/modules/3.2.30-030230-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8723e/rtl8723e.ko): Invalid argument
```

---

### Post by hex1616 on 2012-10-07
I'm reinstalled OS and did, like writes in link. All works. Thanks all.

---

