---
title: "wireless won't work on certian connections"
date: 2011-11-16
forum: Networking &amp; Wireless
---

### Post by Metal Hed on 2011-11-16
Hi, I am setting up my son's school computer lab up on Linux, the problem is that the wireless will not connect to the schools internet? When I bring the computers back to my place they connect to mine just fine? I'm not a networker by any means so this problem is quite confusing. HEEEELLLPPPP!!!!!!

---

### Post by praseodym on 2011-11-16
Hi,

school networks/open networks often "only" use WEP- or mixed WPA/WPA2-encryption, which causes problems with the network-manager. Try Wicd instead:


```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Deactiviate "connect automatically" in the network-manager applet, and choose **wlan0** as interface name and **wext** as driver in Wicd.

---

