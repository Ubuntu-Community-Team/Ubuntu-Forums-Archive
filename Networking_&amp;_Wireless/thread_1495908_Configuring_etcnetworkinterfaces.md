---
title: "Configuring /etc/network/interfaces?"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by meklu on 2010-05-28
I would like to configure that file as I can't connect to Internet in e.g. recovery mode without running nm-applet and a GUI thingy, which really pisses me off. I've got a Ralink 3070 USB -adapter and the rt2870sta module for it (from Ubuntu's default kernel). The name of the interface is wlan0, wifi security is WEP (shared, ie. not open) with a 40/128-bit ASCII key. Any suggestions?

---

### Post by chili555 on 2010-05-28
If Network Manager is running, it is unlikely you will get manual configuration working. I have tried and failed many times. If you want to connect manually, I suggest you remove Network Manager. Find out if Network Manager is running with:```
ps aux | grep -i network
```

I then suggest you set up /etc/network/interfaces as follows:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-ssid yourrouter
wireless-key s:your5or13characterasciikey 
```

---

### Post by meklu on 2010-05-28
> **chili555 said:**
> If Network Manager is running, it is unlikely you will get manual configuration working. I have tried and failed many times. If you want to connect manually, I suggest you remove Network Manager. Find out if Network Manager is running with:```
ps aux | grep -i network
```I then suggest you set up /etc/network/interfaces as follows:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-ssid yourrouter
wireless-key s:your5or13characterasciikey 
```
Thanks! I followed your instructions (removed NetworkManager, tweaked the file) *but* I had to add the line "wireless-keymode restricted" in the end of the file.
*mental thumbs-up to chili555*

---

