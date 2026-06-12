---
title: "network-manager 0.7 no panel icon"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by psycho5 on 2008-12-20
Hi,

I am using ubuntu 8.04 and trying to make my usb gsm modem work, it installs successfully but network manager that came with 8.04 doesn't have an option to connect to it, so I upgraded the network manager by adding a line in my sources list :

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main

which worked perfectly, and network manager was installed and it indicated for me to reboot the PC. 

After reboot, I can't see any network manager icon on the panel, how can I make the icon appear on the panel again?

Thank you for your help

---

### Post by zika on 2008-12-20
(this is for 8.10): it depends of the switch in the file ```
/etc/NetworkManager/nm-system-settings.conf
```that is ```
[ifupdown]
managed={true,false}
```true=let NM rule.
false=let ifup/ifdown rule.

also, if You have eth0 or whatever in /etc/network/interfaces NM might not appear. that is how it works with 8.10 (I never had NM while in 8.04).

I'm just curious: why do You need NM in the first place when networking worked great in 8.04 and NM made a chaos in 8.10. I've got rid of it soon enough but forums are full of bad testimonies)

---

### Post by psycho5 on 2008-12-21
Well, I'm using it because it has the broadband gsm connection setup.

---

