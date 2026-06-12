---
title: "eth0 not detected after update (Karmic)"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by ryeguy146 on 2009-11-26
After installing Karmic on a Dell Inspiron 8600 laptop, I've been having some issues. I plugged in a ethernet cable to update as I hadn't yet enabled my broadcom wireless. After the update, I rebooted and was no longer able to access the internet. I worked with the machine and discovered that it no longer recognized my wired card. I've tried adding eth0 to the /etc/network/interfaces, but when I try to bring it up, I get the error: "no such device." I have no idea how to proceed from here. I'll list my relevant information: 

ifconfig -a returns only the lo device.

/etc/network/interfaces contains only the lo device
/etc/network/resolv is empty

lspci returns two network devices:
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev-01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

As for the wireless, when I attempted to install b43-fwcutter as per [this]("http://ubuntuforums.org/showthread.php?t=1308788") thread, I'm asked to insert my CD. I do so, but it complains that it isn't labeled correctly. Is there any way for me to access the files that b43-fwcutter needs from the CD manually and pointing to it? Note: this was done before the update, when I had wired access.

Thank you for any help.

---

### Post by ryeguy146 on 2009-11-26
You know, nevermind.

I'm just going to use Arch.

---

