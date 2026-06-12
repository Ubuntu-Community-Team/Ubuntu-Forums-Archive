---
title: "WiFi not responding in certain public areas"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by renchu on 2011-09-16
I am using a Toshiba Laptop 205 Ubuntu 10.04. I am experiencing a problem using the laptop at the public library. The problem doesn't exist elsewhere (home/university). It is also fairly recent in this location. Browser is Chrome, but also happens in Firefox
When I try to access certain pages, the system continues to cycle, never giving me access. What is strange for me it that it only happens on certain pages, for example: I can get to Yahoo main page and Yahoo mail; Same for google, but if I try to access AOl mail nothing but cycling.. I can get to Facebook mainpage but if I try to move to groups or messages, it goes into this cycling ( wait) mode. Refreshing doesn't help nor can I log out.  If I use the library Pc, I also have no such problem.  How do I begin to diagnosis where my issue is.
A setting change,perhaps; something with Flash??  Im at a loss.
Any help would be appreciated
thanks

---

### Post by SecretCode on 2011-09-16
This sounds more like something is blocked, than a wifi problem. I would suspect that the library have started filtering sites you can access via wifi - and maybe not deliberately, just via some package or filter rules they've downloaded.

Can other people access these sites with different computers at the same sites? (Over wifi. The library PC might not go through the same filters.)

---

### Post by praseodym on 2011-09-16
Public networks often use no, WEP or mixed WPA/WPA2 encryption. The latter often makes problems with the network-manager. Try Wicd instead:


```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```
Choose whatever "iwconfig" gives you as wireless interface and **wext** as driver. Maybe you have to uninstall network-manager completely in Lucid:
```
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```

---

### Post by renchu on 2011-09-16
Ill ask about this but I'd be surprised if they have changed anything, at least for AOL.. thanks

---

### Post by renchu on 2011-09-16
Ill give it a shot tomorrow when Im there. Appreciate the help, all.....

---

