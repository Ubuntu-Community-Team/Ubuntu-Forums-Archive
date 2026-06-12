---
title: "wireless wpa/wpe doesn't work on KDE but works on Gnome"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by calsaverini on 2010-03-22
Hi, 

I've recently installed KDE 4.4.1 just to try on a Dell 1545 laptop with Ubuntu 9.10 previously installed. 

My problem is that the wireless connection works just perfectly with nm-applet under Gnome, but when I login on KDE and ask KNetworkManager to connect to the same network as before, it can't finish the connection. 

When I choose the connection the program asks for my passphrase, I type it and then it just sticks on "activating network" and nothing happens.

My experience with KDE is zero, so I don't even know where to start looking. I'd even tried to kill KNetworkManager and try to replace it with nm-applet, but I think there's a daemon that restarts it immediately.

---

### Post by melodaf on 2010-06-09
Hey man =)

I am having a similar issue, but it happens with a wired ethernet card under KDE 4.1 (Kubuntu 8.10).

With both Ubuntu and even the beta release of Chrome OS my network card works just fine. But when I boot Kubuntu the eth0 interface don't get any ip address. I even tried to manually load the module of my card (r8169) with modprobe and manually assign an ip address to the interface, but no luck. 

Oh yeah, and dhclient keeps waiting for a dhcp response, and goes to sleep when it doesn't get it. 

This problem is driving me crazy for some months.

---

