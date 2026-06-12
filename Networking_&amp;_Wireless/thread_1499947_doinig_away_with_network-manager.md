---
title: "doinig away with network-manager"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by santana on 2010-06-02
Hi I would like to do away with network manager. Unfortunately, after "apt-get remove network-manager network-manager-gnome" the wifi stops working altogether. I get "Interface doesn't support scanning : network down".

What's the right way to remove network-manager while leaving the iw* wireless tools functional?

---

### Post by irv on 2010-06-02
> **santana said:**
> Hi I would like to do away with network manager. Unfortunately, after "apt-get remove network-manager network-manager-gnome" the wifi stops working altogether. I get "Interface doesn't support scanning : network down".

What's the right way to remove network-manager while leaving the iw* wireless tools functional?

Why do you want to remove the network manager? You need something to find wireless connections. What version of Ubuntu are you using. When I used 9.04 I use wicd and it removed network manager and installed it own manager. I am using 10.04 now, and have not install wicd yet. I may just stay with the network manager that come with gnome. It just seem to work and it finds all the networks around me when I am on the road.

---

### Post by pwaugh on 2010-06-02
I think what you really want to do is remove the "notification area" containing the wifi indicator from the panel.  Just right-click it and click "Remove from Panel".

patrick

---

### Post by chili555 on 2010-06-02
> **santana said:**
> Hi I would like to do away with network manager. Unfortunately, after "apt-get remove network-manager network-manager-gnome" the wifi stops working altogether. I get "Interface doesn't support scanning : network down".

What's the right way to remove network-manager while leaving the iw* wireless tools functional?I think you also need to populate /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-essid mylilrouter
wpa-psk mysecretkey
```Substitute your details, of course. Then restart networking:```
sudo /etc/init.d/networking restart
```

---

