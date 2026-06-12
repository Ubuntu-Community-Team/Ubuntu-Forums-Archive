---
title: "USB wireless device"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by TimmyK. on 2012-06-22
Howdy. I just got Ubuntu Studio on my Sony Viao desktop. I plugged in my USB wireless device (a Netgear WNA3100) and it didn't do anything. Is there a driver for this somewhere, preferably one that can be installed by USB drive? Thanks.

---

### Post by praseodym on 2012-06-23
Please show:
```

uname -a
lsusb
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
cat /etc/network/interfaces
route -n
```

---

### Post by TimmyK. on 2012-06-23
OK, check the pictures I posted.

---

### Post by praseodym on 2012-06-24
Do you have a cable connection? If yes:

```
sudo apt-get install linux-headers-$(uname -r) linux-headers-lowlatency-pae build-essential dkms ndisgtk ndiswrapper-dkms
```
Its a Broadcom-Chipset which only works with the windows driver (see attached). Unpack it and install it with the tool.

See: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Do you have a PCI-wireless device (Module **rt2500pci** loaded)?

There are two drivers for a wired device loaded. Please show:

```
lspci -nnk | grep -iA2 net
```

The packages ndiswrapper-utils-1.9, ndiswrapper-common, ndiswrapper-dkms, and ndisgtk are also on the CD. Copy them to "Downloads" and install them via:
```

sudo dpkg -i ~/Downloads/*.deb
```

---

