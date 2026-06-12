---
title: "Not Loading Driver For USB Wireless Adapter"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by checkit on 2009-08-22
I have a D-Link DWL-G122 (rev. B1) USB wireless adapter, and I am trying to get it to run using the native drivers.

When I run sudo lshw -C network, I get the following:

```
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:40:c4:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:11:0a:95:3a:0c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:17:9a:d0:ff:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

As per the instructions in [WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Device%20Drivers"), I am expecting to find something like "driver=<aaa>" in the configuration line to indicate that a driver has been configured for this device.

If I run lsmod | grep usb, I get the following:
```
rt2500usb              27904  0 
rt2x00usb              18816  1 rt2500usb
rt2x00lib              36224  2 rt2500usb,rt2x00usb
mac80211              216948  2 rt2x00usb,rt2x00lib
usbhid                 35712  0 
hid                    50560  1 usbhid
usbcore               149616  6 rt2500usb,rt2x00usb,usbhid,uhci_hcd,ehci_hcd
```

This indicates that the correct driver (rt2500usb) has been loaded.

Can anyone tell me what I need to do in order to set up the driver correctly?  Thanks in advance.

---

