---
title: "Linksys WUSB100 v1 looses internt access on Ubuntu 12.04"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by linuxmart on 2012-05-11
Hi there,
  I had issues with my Linksys WUSB100 v1 on Ubuntu 10.10 and solved it by blacklisting some modules. On Ubuntu 11.10 it worked out of the box.

Now in Ubuntu 12.04, it connects to the router and gives me internet for about 2 minutes, and then I loose internet access. The network manager shows it as connected to the router though.
When I disconnect the usb adapter, and reconnect it, I have internet for about 2 minutes again.

Here are the results of some commands I ran on it:

lsusb

> Bus 001 Device 007: ID 1737:0070 Linksys WUSB100 v1 RangePlus Wireless Network Adapter [Ralink RT2870]

modinfo rt2800usb | grep 0070

> alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*

dmesg | grep rt2

> [   25.955942] Registered led device: rt2800usb-phy0::radio
[   25.955961] Registered led device: rt2800usb-phy0::assoc
[   25.955983] Registered led device: rt2800usb-phy0::quality
[   25.956025] usbcore: registered new interface driver rt2800usb
[ 1047.463362] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x7010 with error -19.
[ 1047.473315] phy0 -> rt2x00usb_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffff8801
[ 1049.772449] Registered led device: rt2800usb-phy1::radio
[ 1049.772485] Registered led device: rt2800usb-phy1::assoc
[ 1049.772522] Registered led device: rt2800usb-phy1::quality
[ 1239.956134] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x1004 with error -19.
[ 1242.773917] Registered led device: rt2800usb-phy2::radio
[ 1242.773952] Registered led device: rt2800usb-phy2::assoc
[ 1242.773985] Registered led device: rt2800usb-phy2::quality

modprobe -l | grep rt2

> kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
kernel/drivers/net/wireless/rt2x00/rt61pci.ko
kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
kernel/drivers/net/wireless/rt2x00/rt2500usb.ko
kernel/drivers/net/wireless/rt2x00/rt73usb.ko
kernel/drivers/net/wireless/rt2x00/rt2800usb.ko

Any ideas on how I can solve this problem?

Thanks in advance for you help.

---

