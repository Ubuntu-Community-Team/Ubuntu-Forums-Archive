---
title: "Can't connect to Internet using Huawei E620"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by astro-boy on 2010-12-27
Hello I am just a newbie in Linux World, and I chosed Ubuntu for its reputation and its philosopy. I use Ubuntu 9.10 Karmic. My problem is, I tried to install my Huawei K3520 (it's recognized as Huawei E620 in Ubuntu), but sadly I don't know how to make it work so I can get internet connection.

I plugged my usb-modem and run lsusb command, and the output is like this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I already installed libusb, usb_modeswitch, usb_modeswitch-data, wvdial. I configure part of /etc/usb-modeswitch.conf to be like this:

########################################################
Huawei E620
#
# Contributor: Dale Lane

DefaultVendor=  0x12d1
DefaultProduct= 0x1001

# choose one of these:
DetachStorageOnly=1
HuaweiMode=1

When I run usb_modeswitch command, the output is like this:

Looking for default devices ...
 Found default devices (1)
Accessing device 000 on bus 001 ...
Using endpoints 0x02 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: 
     Product: 
  Serial No.: 
-------------------------
Invalid mode combination. Check your configuration. Aborting.

Does anybody know what's going on?

I tried to solve this problem for weeks but the result is not good. Can anybody help me? I am being frustated now, since it's very easy to get connect to internet using my usb-modem in Windows. FYI, I run Ubuntu on Sun xVM VirtualBox with primary OS Windows XP.

---

