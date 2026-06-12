---
title: "Acer Aspire 5755-6699, Wired, but no wireless"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by Hovercat on 2011-12-18
[s]I managed to install the wired drivers for my new laptop, but I'm unable to find any working wireless drivers. I'm not sure what the actual wireless card is, but here's my lspci if it'll help:

```

00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation Device 16bc (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Intel Corporation Device 0082 (rev 34)
05:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
```

I'm on ubuntu 10.04.[/s]

I was able to fix it with this:

```
sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
```

[http://ubuntuforums.org/showpost.php?p=11293236&postcount=10](http://ubuntuforums.org/showpost.php?p=11293236&postcount=10)

---

