---
title: "VPN to Wireless"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by rajashraful on 2011-02-02
hi,
I am using a macbook 4.1 having ubuntu 10.10 and it has a wireless card. I am connected to internet via VPN, i.e. in my hostel there is a LAN where you are connected by default through cable but if you want access to internet than you have to use your VPN log in name and password. Now I want to use this pptp vpn internet connection and make a wireless network access point in my notebook using the built in wireless card. I tried to make a "new wireless network" and did this. but from other macbooks when I want to connect to this network it shows that this is a "settings" not a "wireless access point". from other macbooks and mac os I can connect to this "settings" using the WEP password and get connected to this "settings" but there is no internet. How to make a usuable wireless access point which can use my internet providing vpn and will give a real access point of wifi. My wireless card is enabled and it is capable to detect any wifi point and get connected to that point.

---

### Post by AlexQM on 2011-02-02
I can point you in the right direction but have not add success myself with a similar issue. you need to bridge your wireless connection (Your Access Point) to the Ethernet connection using the brctl from bridge-utils.

```
sudo apt-get install bridge-utils
```

Alex

---

### Post by rajashraful on 2011-02-02
same here :(

---

### Post by AlexQM on 2011-02-04
How far have you got with setting this up? Have you installed the bridge utilities?
type "brctl" to get the syntax for it

---

### Post by rajashraful on 2012-03-19
no success

---

