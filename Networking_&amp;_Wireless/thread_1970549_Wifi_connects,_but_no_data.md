---
title: "Wifi connects, but no data"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by HarveyDX on 2012-05-01
Hi all,

I just fresh installed 12.04 on my laptop which had 11.10. I can connect to my wifi just fine, but when I go to a website it says that it is not available. I cant ping google.com. When I connect a cable it runs just fine. I remembered that 11.10 had wifi run fine out off the box. 
My system is a HP Probook 5330m. Can anyone tell me what Im doing wrong? Thanks in advance.

---

### Post by ubudog on 2012-05-01
Hi there, could you please post the output of: 
```
ifconfig
```
```
sudo lspci -v
```

---

### Post by HarveyDX on 2012-05-01
Hey thx for replying,

here goes:

```
eth0      Link encap:Ethernet  HWaddr 10:1f:74:c5:17:a6  
          inet6 addr: fe80::121f:74ff:fec5:17a6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21347794 (21.3 MB)  TX bytes:666019 (666.0 KB)
          Interrupt:20 Memory:d0700000-d0720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19843 (19.8 KB)  TX bytes:19843 (19.8 KB)

wlan0     Link encap:Ethernet  HWaddr a0:88:b4:d3:c0:2c  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a288:b4ff:fed3:c02c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5777 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:730480 (730.4 KB)  TX bytes:630965 (630.9 KB)

```


```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d0724000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: mei
	Kernel modules: mei

00:16.3 Serial controller: Intel Corporation 6 Series/C200 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 2090 [size=8]
	Memory at d072b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: serial

00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
	Subsystem: Hewlett-Packard Company Device 1623
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0700000 (32-bit, non-prefetchable) [size=128K]
	Memory at d072a000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2060 [size=32]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] PCI Advanced Features
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d0729000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at d0720000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: d0600000-d06fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 164f
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: d0500000-d05fffff
	Prefetchable memory behind bridge: 00000000bfb00000-00000000bfbfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 164f
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: d0400000-d04fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device 164f
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d0728000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 2088 [size=8]
	I/O ports at 209c [size=4]
	I/O ports at 2080 [size=8]
	I/O ports at 2098 [size=4]
	I/O ports at 2040 [size=32]
	Memory at d0727000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci

02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0503000 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at bfb00000 [disabled] [size=64K]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 164f
	Flags: fast devsel, IRQ 18
	Memory at d0502000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [a4] Power Management version 3
	Capabilities: [80] Express Endpoint, MSI 00
	Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
	Kernel modules: sdhci-pci

03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at d0400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number a0-88-b4-ff-ff-d3-c0-2c
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
```

---

### Post by ubudog on 2012-05-01
Be sure the wireless button is turned on, and check in "Additional Drivers" for any wireless drivers.
(Additional Drivers can be accessed via the Dash)

---

### Post by HarveyDX on 2012-05-01
Wireless is turned on. I can connect and everything...I get an ipadres but there is no data exchange. also there are no additional drivers.

---

### Post by ubudog on 2012-05-01
Hmm... could you post the output of: 
```
uname -a
```

---

### Post by ubudog on 2012-05-01
Try this (as per chili555, [here]("http://ubuntuforums.org/showthread.php?p=11890907")): 

Disconnect your ethernet cable, and do:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```

Is your wifi working?

---

### Post by HarveyDX on 2012-05-02
Yes that worked! Thank you very much sir!

---

### Post by ubudog on 2012-05-02
> **HarveyDX said:**
> Yes that worked! Thank you very much sir!

[s]Awesome!  Does it survive a reboot?[/s]

Edit:
To make it persistent, please do [this]("http://ubuntuforums.org/showpost.php?p=11888778&postcount=36").

---

