---
title: "atheros network help"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by openation1 on 2013-05-25
hello everyone..... I install 12.04 on my laptop and the wifi doesn't work..... I am new on this operating system... I m barely learning it. and I need help with this issue. I would apprecitated very much...... this is what I have.... and how can I do it?
AM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1604]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company U98Z062.12 802.11bgn Wireless Half-size Mini PCIe Card [103c:3040]
    Kernel driver in use: ath9k
    Kernel modules: wl, ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:1604]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by praseodym on 2013-05-25
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Check afterwards:
```

iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```

---

