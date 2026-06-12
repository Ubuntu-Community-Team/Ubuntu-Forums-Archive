---
title: "RTL8111/8168B problems in Ubuntu 11.10 amd64 (asrock ion 3d 152b)"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by MecoTom on 2011-11-05
Hi,

  I've installed ubuntu 11.10 amd64 on a asrock ion 3d 152b.

  The problem is that wireless works ugly.

  The board is:

  Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

  It is detected with the r8712u module, but many times it fails to connect. When it connects, the download speed is poor (sometimes it works well, but only for a few seconds), and very unstable. Upload speed is better. Other computers which are further from the router have better download speeds.

  I also tried r8169 ([https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393/comments/22](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393/comments/22)) and r8168 ([https://aur.archlinux.org/packages.php?ID=27000](https://aur.archlinux.org/packages.php?ID=27000)) modules, but they only detect the wired connection.

  Any ideas?

---

### Post by MecoTom on 2011-11-05
I realized that the internal wlan card is usb (I didn't know this was possible ;)).

The card is: 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

Trying to find a solution...

---

