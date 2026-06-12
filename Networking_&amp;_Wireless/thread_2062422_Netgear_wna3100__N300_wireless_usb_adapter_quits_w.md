---
title: "Netgear wna3100  N300 wireless usb adapter quits working"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by Lawrenzo6563 on 2012-09-24
Hi,
After googling around, I followed some of the steps I'd seen in this forum to get the usb adapter working. 

lsusb
Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

I have standard 11.10 that I upgraded, arch is i686

I downloaded ndiswrapper using the Ubuntu Software Center.  I didn't go to sourceforge and get the latest source and make install it.

I went to the directory where I had the driver that I had downloaded
$sudo ndiswrapper -i bcmwlhigh5.inf
$sudo modprobe ndiswrapper
$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9020) present

$sudo iwlist wlan0 scan  showed my network, very cool!!
I went into the SystemSettings-> Network-> wireless, selected my network, and connected, and was able to browse the internet YAY

Then my pc went to sleep, screen saver  AND ITS NEVER WORKED AGAIN
Now when I try the wlan0 scan,
wlan0     Interface doesn't support scanning.
iwconfig no wireless interface.

Does anyone have any suggestions, please
Thanks
Larry

---

