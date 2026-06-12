---
title: "Madwifi suspend script"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by AVeryLongNickname on 2009-02-12
I'm running xubuntu 8.10 on an acer Aspire One, and I've got the wireless up-and-tunning with Madwifi-hal-0.10.5.something:P

The only problem is after suspend/hibernate I have to run 

sudo madwifi-unload
sudo /sbin/modprobe ath_pci

to get wireless network.

I'm curious if I can add these commands to a suspend script or something so I dont have to run them manually everytime i wake the computer from suspend.

Any help would be great! :) :guitar:

---

