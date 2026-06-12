---
title: "Wireless died on network-manager update"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by Oppenheimer on 2012-06-02
Update manager just updated some packages for me (CUPS, network-manager-gnome-0.9.4.1) on my 12.04 install; on reboot my wireless didn't come up. 

Acer Aspire One 721

lspci: Broadcom BCM43225
uname: 3.2.0-24-generic x86_64
iwconfig lists the interface as iwlan0, but it doesn't show in ifconfig
iwlist scanning reports: Failed to read scan data : Network is down 
rfkill list: hardware and software blocks are both off


- network is definitely up (I'm using it right now)
- I don't think that the kernel was updated, and I tried rolling back to the previous kernel (3.2.0-17) and that didn't help either
- dmesg isn't throwing any errors
- NetworkManager is up and running, ethernet works, but does not recognize any wireless devices

I can try rolling back to the previous network-manager, but I'm not sure how to do that.

Any suggestions?

---

### Post by tuxuser33 on 2012-06-03
Grabbed from here:

[http://forum.ubuntuusers.de/topic/12-04-nm-applet-initialisiert-nicht/#post-4436757](http://forum.ubuntuusers.de/topic/12-04-nm-applet-initialisiert-nicht/#post-4436757)

Try this:

sudo apt-get install --reinstall network-manager network-manager-gnome

Did this in Linux Mint13 after same update. Worked for me.
If promted for, replace the config-files with the files from the package-maintainer.

Wiped Mint13 out nevertheless cause of other difficulties with UMTS-modems.
Went back to Mint11 XFCE

---

