---
title: "connecting to Vista ad hoc"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by meysam on 2009-02-23
Hi,
I have installed ubuntu 8.4 on my laptop (extensa 5220)
there is another machine with vista and my internet connected to it. I shared internet connection with vista by using ad hoc connection.
in my laptop I can see the ad hoc network but when I try to connect to it, nothing happen.
my laptop connects to my university wireless then the wireless card is ok.
should I do anything in my laptop to be able to connect to an ad hoc network.
Thank you.

---

### Post by TenPlus1 on 2009-02-23
usually I edit the /etc/network/interfaces file directly in terminal and put these lines to access my own ad-hoc network:

auto lo
iface lo inet loopback

iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-keymode open
wireless-key s:password
wireless-essid wirelessnet

auto wlan0

---

### Post by meysam on 2009-02-23
Thank you very much for your help.
I tried your solution. but nothing happened. again on system tray I clicked on my ad hoc name and it asked me for password.I entered the password again and after that nothing happened.
my interface file is like this now:

auto lo

iface lo inet loopback


iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
wireless-mode ad-hoc
wireless-keymode WPA Personal
wireless-key s:123456789
wireless-essid ppp

auto wlan0

---

