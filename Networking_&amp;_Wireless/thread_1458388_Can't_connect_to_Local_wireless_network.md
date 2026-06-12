---
title: "Can't connect to Local wireless network"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by polardude1983 on 2010-04-19
I am running Ubuntu 9.10 and I have a Linkseys wireless USB its WUSB11 v 2.* something lol its to small for me to read haha its like 2.6 or 2.8 or something.

Anyways yes networking and wireless is enabled. And it lists the wireless network im trying to connect to.

Its name is Doss and its unprotected no security enabled no mac enabled. I hit to try to connect it and the icon goes round and round and then says you are not connected.

---

### Post by 405jayb on 2010-04-20
Try setting security to it and see what that does.

---

### Post by LeeDaugherty on 2010-04-20
Polardude - It is probably not getting an IP from the router, check the router for MAC authentication and even simpler it supports B/G/N or whatever protocol your adapter is using.  Telling what kind of router might help as well.

---

### Post by polardude1983 on 2010-04-21
The router is a linksys wirelss-g 2.4ghz

Wireless network mode: mixed
SSID: doss
Wireless channel: 6 (which it seems you cant set i ubuntu 9.10?)
SSID broadcast: enabled

Security Mode: disabled

Wireless MAC filter: disabled

it still seems to not connect

---

### Post by polardude1983 on 2010-04-22
Anybody got any bright ideas?

---

### Post by bobyy on 2010-04-23
Hy
Find what is your wireless netw card
#sudo ifconfig -a
after that do a:
#sudo iwconfig wlan0 essid doss

if you have no encryption should do the trick

regard

---

### Post by bobyy on 2010-04-23
?

---

### Post by polardude1983 on 2010-04-23
no unfortunately still not connecting :/

---

