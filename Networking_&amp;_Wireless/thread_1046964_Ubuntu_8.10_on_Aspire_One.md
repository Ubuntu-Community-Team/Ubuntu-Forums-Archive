---
title: "Ubuntu 8.10 on Aspire One"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by slammed87d21 on 2009-01-21
I've got 8.10 installed on my Aspire One. My problem is with my wireless. In 8.04.1, I had signal comparable with Wndoze XP. In 8.10, my signal just plain sucks. I don't know if it makes a difference, but I had the acerhk module installed in 8.04.1. Can't seem to find it now. Here's output of lspci:  > 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
. Also, when trying to setup madwifi per the wiki, it didn't work for some reason. Set it up like my other Acer, but not sure if that's the problem since the same madwifi driver worked in 8.04.1.

---

### Post by pytheas22 on 2009-01-21
Please post the output of these commands, in this order:
```

lshw -C Network
lspci -nn | grep -i atheros
lsmod | grep ath
sudo modprobe -r ath_pci ath9k
sudo modprobe ath9k
sudo iwlist scan
sudo rmmod ath9k
sudo modprobe ath_pci
sudo iwlist scan
dmesg | grep -e ath -e wlan
```

---

### Post by slammed87d21 on 2009-01-25
Swapped my Atheros Card for a Broadcom card. Fixed my problems, and increased my signal.

---

