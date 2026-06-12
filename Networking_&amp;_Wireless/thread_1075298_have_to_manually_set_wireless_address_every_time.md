---
title: "have to manually set wireless address every time"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by falinx on 2009-02-20
hey everyone, I have a dell inspiron 510m and it seems that every time I start up ubuntu workstation I have to input the wireless details and apply them, otherwise the card simply doesn't work.

Here is my /etc/network/interfaces screen printout...

[I]auto lo
iface lo inet loopback




iface eth1 inet static
address 192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1
wpa-psk xyz"obviously it's a long string here which I am leaving out :))
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid lynx

auto eth1

iface ppp0 inet ppp
provider ppp0

auto ppp0
[/I]

Any help would be greatly appreciated. 

PS I'm using hardy

---

### Post by superprash2003 on 2009-02-20
strange.. your interfaces file seems perfect.. do you enter these settings in the network manager?? next time when you boot, go to the terminal and type **sudo /etc/init.d/networking restart**

---

