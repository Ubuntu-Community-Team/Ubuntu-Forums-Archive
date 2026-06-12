---
title: "Newbie - Wireless Device &quot;Not ready&quot;"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by harryjamesuk on 2013-02-12
Hi,

I am new to Linux, Using Ubuntu but when I tried to go on the Networking information, It says my device is "Not ready".

By this, I know it means the Driver isn't installed so I looked online and found this driver: [http://www.wireless-driver.com/realtek-rtl8192u-wireless-linux-macos-drivers/](http://www.wireless-driver.com/realtek-rtl8192u-wireless-linux-macos-drivers/) for my device.

I read the readme which said "	1. In order to make the driver to work, the fold under firmware need
           to be put under the fold of /lib/firmware/ or 
                                       /lib/firmware/(KERNEL_VERSION)/"

So I tried to copy the folder "firmware" into /lib/firmware/ but I don't have permission to do so.

Hope you can help!

---

### Post by chili555 on 2013-02-13
Assuming the firmware file you downloaded is on your desktop, then open a terminal and do:```
sudo cp Desktop/firmware/* /lib/firmware
```However, I doubt the answer is precisely that. I assume the driver in question is r8192u_usb. If so, check:```
modinfo r8192u_usb
```It says, in part:> filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/staging/rtl8192u/r8192u_usb.ko
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
firmware:       [COLOR="Red"]RTL8192U[/COLOR]/data.img
firmware:       RTL8192U/main.img
firmware:       RTL8192U/boot.img
license:        GPL
That means the driver will look for the firmware files in /lib/firmware/RTL8192U. Therefor, what you probably really want to do is:```
sudo mkdir /lib/firmware/RTL8192U
sudo cp Desktop/firmware/* /lib/firmware/RTL8192U
```As you might expect, the wildcard * means copy *all* the files in the folder.

Please post back if you get stuck.

---

