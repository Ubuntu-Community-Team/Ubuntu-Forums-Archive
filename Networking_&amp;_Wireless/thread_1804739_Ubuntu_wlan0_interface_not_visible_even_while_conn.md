---
title: "Ubuntu wlan0 interface not visible even while connected to Wifi"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by amerninja13 on 2011-07-15
EDIT: The issue was caused by the proprietary Broadcom STA driver I was using; I needed to switch to the open source B43 driver (in my case, the low power chipset version), however I'm having further problems with this driver (although it does find wlan0 if you star the driver from the Terminal, and it doesn't consider it ethernet). It's not fully solved.

Hello,

I'm running Ubuntu 11.04 on a Dell Inspiron 1440, it has a 64-bit processor.

I have a Wifi connection setup that successfully sends and receives internet data. However, Ubuntu appears to think that I'm still connected via ethernet (I was earlier today).

Whenever I go into a program (like Ettercap and Wireshark) or use airmon-ng in the Terminal, it only shows the eth2 interface (Ethernet) and not the wlan0 interface (Wifi).

Anyone have any solutions (maybe by editing the interfaces file)?

In my /etc/udev/rules.d file, it displays the following:

```

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:64:71:e7:f3", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x1668:0x6010 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:05:2f:0e:3b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="70:1a:04:78:6b:f2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="70:1a:04:78:6b:f2", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

```

Ubuntu thinks that my Wifi (802.11) interface is eth2, when it should be wlan0 (which is also in the list, but isn't used at all by Ubuntu).

---

### Post by Z.K. on 2011-07-19
Does it really matter since obviously your Wi-Fi is working?  I have the same thing.  My problem is I can't figure out the driver the card is using so I can blacklist it as it interferes with my 3G connection.

---

