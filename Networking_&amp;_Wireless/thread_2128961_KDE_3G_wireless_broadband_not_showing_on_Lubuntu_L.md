---
title: "KDE 3G wireless broadband not showing on Lubuntu Laptop"
date: 2013-03-24
forum: Networking &amp; Wireless
---

### Post by RoosterHam on 2013-03-24
[COLOR=#000000][INDENT]I have a Huawei E367 HSPA+ usb modem. I also have a laptop with which I often use wireless broadband, with Lubuntu 12.10 installed. Formerly has had Fedora and Ubuntu 12.04. The Huawei showed up in the network manager in Fedora+Gnome, in Ubuntu+Unity and in Lubuntu, all immediately after plugging it in. 

I installed the KDE desktop on the Lubuntu laptop that this had been working. Since then, when logged into a KDE session, plugging the usb modem in does not add an interface to the network manager. The connection comes up in "Wireless Broadband" tab of "manage connections," as do all the wlan and ethernet profiles I have set before installing KDE. But editing my wwan connection pops up a message saying "No agents were available for this request".

lsmod, lsusb, and tail -f /var/log/syslog all tell me that everything is detected and configured exactly the same as always (by which I mean lsusb has always seen an E398 but the E367 still worked that way). Is this a problem with the KDE ModemManager?[/INDENT]


[/COLOR]

---

