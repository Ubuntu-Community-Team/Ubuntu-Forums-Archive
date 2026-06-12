---
title: "Wifi not working on HP Pavillion dv6t and Ubuntu 10.04"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by gsingh2011 on 2012-01-18
I have an HP Pavillion dv6t ([http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=High+performance&series_name=dv6tqe_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/High_performance/dv6tqe_series](http://www.shopping.hp.com/webapp/shopping/computer_can_series.do?storeName=computer_store&category=notebooks&a1=Category&v1=High+performance&series_name=dv6tqe_series&jumpid=in_R329_prodexp/hhoslp/psg/notebooks/High_performance/dv6tqe_series)) and I can't get the Wifi working in Ubuntu 10.04. If I type lspci I get: 0d:00.0 Network controller: Intel Corporation Device 008b (rev 34) for my network card. Can anyone help me get this running?

---

### Post by carl4926 on 2012-01-18
```
lspci -nnk
```

Lets see exactly

---

### Post by gsingh2011 on 2012-01-18
```
gulshan@gulshan-laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
    Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c49] (rev 05)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6760]
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Kernel driver in use: r8169
    Kernel modules: r8169
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
13:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
13:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
19:00.0 USB Controller [0c03]: NEC Corporation Device [1033:0194] (rev 04)
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci

```

---

### Post by carl4926 on 2012-01-18
make sure you have kernel firmware packages installed

similar thread here
[http://ubuntuforums.org/showthread.php?t=1839893](http://ubuntuforums.org/showthread.php?t=1839893)

---

### Post by gsingh2011 on 2012-01-19
Could you post the command to install these packages? I'm not sure what to take from that thread. Thanks.

---

### Post by gsingh2011 on 2012-01-27
Could you please post those commands? I don't know what to do, but I can't stand running Windows too much longer.

---

