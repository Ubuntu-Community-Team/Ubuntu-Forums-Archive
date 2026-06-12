---
title: "unmounting usb wireless device"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by cjreyn on 2010-02-03
Hi all,
This should be an easy one to solve. I have an external wireless card (rtl8187) which detects automatically when I plug into a usb port. It shows in lsusb as 

Bus 002 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

My question is this: Once I've brought the interface down, how do I safely remove this usb device? I would presume it would show in /dev and can be unmounted but I've no idea which device it would be (there is a device usbmon6 but unmounting this doesn't work).

If I just remove it, it works fine when I plug it in again, only it assigns the id wlan2 instead of wlan1 the first time round (my wlan0 is constant, the laptops inbuilt adapter).

Using Karmic by the way.

Cheers

---

