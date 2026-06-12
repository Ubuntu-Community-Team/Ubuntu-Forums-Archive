---
title: "Alfa AWUS036H getting driver version"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by john_thalyburg on 2011-06-22
Hello!

I am using Ubuntu 11.04. The Kernel 2.6.38-8 comes with drivers for chipspet Realtek RTL8187. Device works ok, no problems. But I would like to get the current driver version. I searched with this code:

```
sudo lsusb -v -s 004
```Displays bunch of information about this usb device (Alfa AWUS036H), but no driver version. I followed [this tutorial]("http://www.cyberciti.biz/faq/linux-find-wireless-driver-chipset/"), replacing lspci with upper lsusb, but as I said it outputs bunch of information, but no line with Kernel driver in usage. I tried to search it with:

```
sudo lsusb -v -s 004 | grep -i driver
```But no luck. I don't get it whz it does not have the driver information. Is there another command, to get the driver version in use for specific USB device?

---

