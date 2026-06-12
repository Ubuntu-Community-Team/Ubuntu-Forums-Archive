---
title: "Huawei modem EC1261 problem"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by bihuboliya on 2010-07-28
Hello all,

I am using Ubuntu 10.04. In my Samsung R528 laptop Huawei EC1261 is not being detected as modem but a storage device.

**lsusb** output:
**Bus 001 Device 004: ID 12d1:1446 Huawei Technologies Co., Ltd. **

**ls /dev/ttyU*** output:
**ls: cannot access /dev/ttyU*: No such file or directory**

I have installed packages
1. usb-modeswitch_1.1.3-1_amd64
2. usb-modeswitch-data_20100623-1_all

Going through some posts I have edited **/etc/usb_modeswitch.d/12d1:1446** to include 1446:

########################################################
# Huawei, newer modems

DefaultVendor= 0x12d1
DefaultProduct=0x1446

TargetVendor=  0x12d1
TargetProductList="1001,1406,140c,141b,14ac,**[COLOR=Red]1446[/COLOR]**"

CheckSuccess=20

MessageContent="55534243123456780000000000000011060000000000000000000000000000"

Still its not working. Please help... :(

---

### Post by bihuboliya on 2010-07-28
Someone please help...

---

### Post by abhishekchanda on 2010-08-27
Add this instead -- 140b

---

