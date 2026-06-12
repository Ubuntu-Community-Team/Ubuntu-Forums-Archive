---
title: "no wireless networks found (gateway m520, bcm4306)"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by elsaturnino on 2008-12-26
I'm trying to get my sister's old laptop (a gateway m520) set up on ubuntu but the wireless connection just isn't working. I've done the following steps:

1) installed b43-fwcutter
2) enabled driver in system -> admin -> hardware driver
3) confirmed that the interface is up using ifconfig/iwconfig

The problem is that no networks show up when I check in the network manager applet. I have also tried "iwlist wlan0 scan" and no networks are located there. I tried setting up the connection to my wireless network using iwconfig but when I try "sudo dhclient wlan0" it says "no DHCPOFFERS received". Any help would be greatly appreciated!

---

### Post by elsaturnino on 2008-12-26
After a lot of headache and heartache, I finally got the thing to work under ndiswrapper. If anyone is interested, I mostly followed the steps found [URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"]here] but I also had to do the following:

1) Add b43, b43legacy, ssb, and b44 to /etc/modprobe.d/blacklist
2) run the command "update-initramfs -u"
3) reboot

Sadly, this also disables the wired networking but I will work on getting them both working soon.

---

