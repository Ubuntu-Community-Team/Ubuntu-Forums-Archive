---
title: "I would like to stop wireless at boot, and get a working network manager gui"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by PARO on 2013-03-28
I installed ubuntu mini so I could get a vanilla Mate Desktop on 12.04, and that worked fine.  However, whenever I start my computer there seems to be a pause at boot while it tries to connect.  When it fails, I won't beable to connect or reconnect. It doesn't do this consistently, but when it does, it leads to a couple minutes boot and then I log in without wireless access.

I tried installing network-manager and network-manager-gnome and started nm-applet the applet says "networking disabled" and there is no option to start (enable networking and enable wireless are grey).  from a terminal it says something about permissions i think. Anyway, it seems it is not playing well with the default interface.  I tried to remove entries in /etc/network/interfaces but it still tried to connect at boot it just failed and i still couldnt use nm-applet or the network-manager-gnome interface still.  

So, I'd like to know how I can stop whatever it is from trying to get me online at boot, and then hopefully network-manager or if there's another prefered way to get online from the tray, or simple commands or whatever after i'm logged in, then that would be nice.

---

### Post by PARO on 2013-03-29
Well from playing around with /etc/network/interfaces and comparing it to my other systems, I was able to solve my problem, and I figured I'd post back in case anyone else has this issue.  

When you install Ubuntu via the mini.iso (the network install image), it sets up an automatic wireless connection in /etc/network/interfaces.  By deleting the connection information, my system would time out the connection, and I still wasn't able to use network-manager to establish a connection, something else was already trying.  I tried deleting the file all together thinking a new one might get created at boot that would fix the problem, but that didn't work either.  This line ```
 auto wlan0
iface wlan0 inet dhcp 
``` needed to be removed (along with the ssid and wireless key).  The file should contain only the loopback network interface info ```
auto lo
iface lo inet loopback
``` Now network-manager is working as expected. [SOLVED]

---

