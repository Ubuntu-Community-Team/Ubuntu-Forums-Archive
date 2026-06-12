---
title: "Suggestions for PCMCIA Wireless-G card (with WPA)?"
date: 2006-05-09
forum: Networking &amp; Wireless
---

### Post by GogglesPisano on 2006-05-09
Hi All --

I'm running Ubuntu 5.10 on my 5-year-old Gateway laptop.  I'd like to get it on my (existing) 802.11g network, which uses WPA encryption.

Can anyone suggest a PCMCIA wireless NIC that:

(1) Works "out of the box" (or nearly so) with Ubuntu
(2) Supports 802.11g and WPA encryption

(I'd like to avoid ndiswrapper, if possible)

Thanks!

---

### Post by vr04 on 2006-05-09
You might wanna look at the Ubuntu Wiki, [over here]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28hardware%29"). There's a list of many user-tested cards.

---

### Post by jml on 2006-05-09
The wiki suggested in the previous post is a good idea, but there are two other things to consider.  First, Ubuntu 5.10 does not support WPA encryption out of the box.  You need to download, install and configure an application called wpa_supplicant.  Its a command line utility that is configured by manually editing a configuration file.  You should be able to get it from the Universe repository.  Before you go too far, you should go to the wpa_supplicant web site (Google for wpa_supplicant and you will find it,) and make sure the wireless card you are thinking about buying has a chipset compatible with wpa_supplicant. They also have a good how-to on configuring the application.  They even supply a generic configuration file to act as a starting point.  To be honest, I have never been able to get it to work with Ubuntu.  The only two distros I ever got WPA working on were Kanotix and Mandriva 2006, and I've been playing with Linux since 1998.

Second point, I've read that Ubuntu 6.06 will support WPA encryption out of the box, so you might want to wait until that distro ships.  Good luck.

---

