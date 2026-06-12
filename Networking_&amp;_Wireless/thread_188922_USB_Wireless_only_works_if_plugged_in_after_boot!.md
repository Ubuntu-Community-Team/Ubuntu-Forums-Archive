---
title: "USB Wireless only works if plugged in after boot!"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by cabbage on 2006-06-04
Greetings,

I've just performed a fresh install of Dapper from the desktop CD and I've got a strange USB wireless problem. I set everything up as I had done before for Brezzy - installed ndiswrapper utils v1.8, used the same driver as before with my Netgear WG111, and configured interface via the network GUI.

However wireless only works if I boot with the adapter unplugged, and then plug it in afterwards. When it doesn't work everything seems OK: lsusb shows the device, ndiswrapper says the driver is loaded and the hardware detected, and iwconfig/ifconfig show an interface, but no light comes on the device.

Under Brezzy the wireless adaptor was named wlan0, but now its eth0 (when it works) and eth1 (when it doesn't).

Looking in messages, when I plug the adapter in I get:
> usb 1-1: new full speed USB device using uhci_hcd and address 2
ndiswrapper: driver netwg111 (NETGEAR, Inc.,06/04/2004, 3.0.18.201) loaded
wlan0: vendor: 'NETGEAR WG111 802.11g Wireless USB2.0 Adapter'
wlan0: ndiswrapper ethernet device 00:0f:b5:92:4b:e7 using driver netwg111, 0846:4240.F.conf
wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
ieee80211: 802.11 data/management/control stack, git-1.1.7
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
usbcore: registered new driver islusb


But if its plugged in during boot I don't get any mention of ndiswrapper loading the netwg111 driver, and instead just see:

> usb 1-1: new full speed USB device using uhci_hcd and address 2
islusb: No suitable configuration found, trying 3887 support

Even if I then unplug and re-plug it in ndiswrapper doesn't load the driver.

I've checked which kernel modules are loaded when it works and not, and the only difference is that ipv6 is loaded when it works.

Any ideas?

Thanks in advance.


Paul

---

### Post by cabbage on 2006-06-05
OK, like other people are finding, Dapper now has native drivers for some usb wireless devices and unless you tell it not to load them you will have problems when trying to use ndiswrapper.

In this case add:

    blacklist islsm
    blacklist islsm_usb

to /etc/modprobe.d/blacklist to stop the native WG111 drivers from loading. Add ndiswrapper to /etc/modules and everything is OK again!

Hope this helps...

---

