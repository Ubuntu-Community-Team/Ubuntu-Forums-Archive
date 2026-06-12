---
title: "VIA VNT 6656 not working in ubuntu 12.04"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by kakila on 2012-06-06
Hi,
After the update to 12.04 my usb wireless adapter stoped working.
```
lsusb
```
> 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]
Bus 003 Device 002: ID 0bda:0156 Realtek Semiconductor Corp. Mass Storage Device
Bus 004 Device 002: ID 0ac8:3430 Z-Star Microelectronics Corp.

I found some post saying that the driver vt6656* should do the trick, but it is not in my system. The command
```
dmesg | egrep 'vt6|vnt|country'
``` returns nothing.

Where can I get drivers for this hardware (I have updated linux-firmware).

Thanks

---

### Post by ksterkarl11 on 2012-09-22
I am having the same issue - did you ever get anywhere with this?

---

### Post by kakila on 2012-09-22
No, no answer neither I could find a solution. I am testing mint and so far everything works (it just took some effort to put it in a USB stick).

---

### Post by Bhrigu on 2012-10-18
Hi,

Could you please explain what you did to it works in Mint?
After using 12.04 I have installed Mint 13 (kernel 3.2.0-32-generic, linux-firmware-nonfree installed), but issue is still here - there are no kernel modules for vt6656 :(

Thanks.

---

### Post by kakila on 2012-10-18
Try following this instructions. I must say I hacked a bit.
[http://wiki.debian.org/vt665x](http://wiki.debian.org/vt665x)

Once you get this module working everything goes back to normal. I do know why Ubuntu doesn't have it.

Clearly installing Debian squeeze will also install this module.

Let me know if it worked for you.

---

### Post by Bhrigu on 2012-10-22
Thanks for your answer, but it didn't work for me 'cause these instructions for 2.6 kernel whereas Ubuntu/Mint have 3.2 (or just maybe I misunderstood you).

But I found another solution - wi-fi works after [installing 3.6.2 kernel]("http://alancads.wordpress.com/2012/10/13/installing-kernel-3-6-2-quantal-in-ubuntu-12-04/").

---

