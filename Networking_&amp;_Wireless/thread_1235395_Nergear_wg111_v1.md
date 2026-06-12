---
title: "Nergear wg111 v1"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by jasjp on 2009-08-09
Hi

I 've got a Netgear wg111 v1, but that does'nt work.
Who can help me ?

Here is what I did :

new installation of Ubuntu 8.04
sudo ndiswrapper -i netwg111.inf (the one who is on the CD)
sudo ndiswrapper -l
netwg111 : driver installed
    device (0846:4220) present (alternate driver: p54usb)
sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
sudo modprobe -r p54usb
echo "blacklist p54usb"|sudo tee -a /etc/modprobe.d/blacklist
blacklist p54usb
sudo modprobe ndiswrapper
echo "ndiswrapper"|sudo tee -a /etc/modules
reboot


but sudo iwconfig gives :
lo        no wireless extensions.

eth0      no wireless extensions.

Any idea ?

Thanks

---

