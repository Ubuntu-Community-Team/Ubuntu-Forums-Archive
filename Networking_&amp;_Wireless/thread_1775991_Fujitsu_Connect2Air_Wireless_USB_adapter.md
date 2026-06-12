---
title: "Fujitsu Connect2Air Wireless USB adapter"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by piapia69 on 2011-06-05
Hi,

I have just installed ubuntu 11.04 on an "old" Fujitsu-Siemens Amilo Laptop. This computer does not have an internal Wi-Fi adapter but got Connect2Air WLAN E-5400 USB adapter that was working perfectly on the windows partition.
After the ubuntu installation, p54usb was complaining about not founding isl3887usb driver in dmesg. I followed instructions found on launchpad : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549383)
Following comment #11, I installed the ubuntu-firmware-nonfree package from synaptic and rebooted the laptop.
dmesg showed that the card is detected and loaded correctly as a Wi-Fi adapter and in the network manager I can see broadcasted wireless networks.
I tried to connect to both an open (unprotected) and a WPA network without any success.

Do you have any idea ?

---

### Post by piapia69 on 2011-06-10
Hello ? Nobody has any idea about my issue ? :(

---

