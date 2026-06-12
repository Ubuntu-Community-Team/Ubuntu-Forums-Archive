---
title: "AT&amp;T USBConnect Adrenaline with 10.04"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by plmcomputerservices on 2011-03-09
Dell Studio Laptop AMD 64 running Ubuntu 10.04
USBConnect Adrenaline 

Note: pretty new to linux and Ubuntu...

I've having difficulties getting the USBConnect Adrenaline to work properly with Ubuntu 10.04.

I've installed the latest usb_modeswitch ([http://ftp.us.debian.org/debian/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.4-2_amd64.deb](http://ftp.us.debian.org/debian/pool/main/u/usb-modeswitch/usb-modeswitch_1.1.4-2_amd64.deb)) and I've added Rezero to the repo and ran apt-get update and apt-get upgrade.

I still see the device as a USB device when plugging in.  (My guess is that the device is too new for the usb_modeswitch repo?) After ejecting the device, I see listed in the network manager (LGE LGE USB Device) but it only says disconnected and doesn't give me the option to connect with it.

I've added AT&T Data Connect to the listed of Mobile Broadband Network Connections and it's chose to use any device detected but never detects the device.

Can someone tell me what to do to get the laptop to automatically recognize the device as a modem and then to automatically/have the option to connect to the AT&T?

Thank you.

---

