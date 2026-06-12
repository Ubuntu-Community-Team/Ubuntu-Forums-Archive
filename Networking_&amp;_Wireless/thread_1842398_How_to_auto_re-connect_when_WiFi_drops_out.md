---
title: "How to auto re-connect when WiFi drops out?"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by Buecai9ahd on 2011-09-11
I've had a search but couldn't find anything.

I leave my laptop on in the day running Tonido so I can access my files and that from other computers but the internet here is bollocks and always drops out.
When I get home and check, the network connection box is up where you enter the network password and connect to it and I manually have to click connect.

My question is, how do I get it to auto RE-connect if it drops out?
It's already set to auto connect when it logs on, wakes up from sleeping etc. but for some reason doesn't when it drops out.

Running 11.04.

Thanks for any help!

---

### Post by praseodym on 2011-09-11
If you use mixed WPA/WPA2 encryption mode the network-manager often has problems with roaming. Better use WPA2-AES instead.

If your router doesnt support WPA2 only or other clients need mixed encryption, give Wicd incl. the Add-On a try:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Deactivate the NM in autostart, choose whatever
```
iwconfig

```shows as wireless interface (**wlan0**, **eth1**, whatever) and **wext** as driver.

---

