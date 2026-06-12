---
title: "Wireless on Ubuntu 10.10 server"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by Nixforce on 2011-06-12
Hi,

I recently bought a new pc for home, and was going to use it as a desktop, but decided i should use it as a server. The only problem is it is too far from the DSL modem, so i got a wireless card for the PC. It is a Canyon CNP-WF511. Does anyone know if ther are and  where i can get drivers for it.

---

### Post by Nixforce on 2011-06-12
Damn, I submitted it twice...Sorry

---

### Post by chili555 on 2011-06-12
I think it uses the Realtek 8185 chipset. It is well supported in the kernel. Tell us more about it. Open a terminal and run and post:```
lspci -nn
```

---

### Post by blueridgedog on 2011-06-12
The chipset in your device appears to be a Ralink rt2x00 and should be supported.  Have you tried connecting it to a wired connection, running update then looking to see what restricted drivers are available?

[http://linux-wless.passys.nl/query_part.php?brandname=Canyon+Tech](http://linux-wless.passys.nl/query_part.php?brandname=Canyon+Tech)

---

### Post by Nixforce on 2011-06-13
Will give it all soon, just reinstalling, thought i would try on centos and see if it worked ok, now reinstalling Ubuntu

---

### Post by Nixforce on 2011-06-17
I ran the lspci -nn and the wireless LAN controller shows as 

Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless Lan Controller [10ec:8185] (rev 20).


does this help?

Thanks

Glenn

---

### Post by chili555 on 2011-06-17
It is supposed to work with rtl8180. Please detach the ethernet cable, if any and do:```
sudo modprobe rtl8180
iwconfig
```Do you now see networks in Network Manager? If not, post:```
rfkill list all
dmesg | grep 818
```Thanks.

---

### Post by Nixforce on 2011-06-19
Thanks! I have changed it to Ubuntu 11.04 desktop 64 bit.. Its running nicely.. 

only problem is its not connecting to the wireless even though it shows the wireless network..

I can see the network, and it asks for the "Authentication required"

But in the router control panel, which WPA do i? 

WPA (TKIP), WPA (AES), WPA2 (TKIP), WPA2 (AES), WPA2 (Mixed) which of these does Ubuntu support?

---

### Post by chili555 on 2011-06-19
Some of us here have trouble with WPA and WPA2 mixed. Without trying it, we'd have no way to know if your card and driver combination do or do not have trouble. It is mainly needed if you have older equipment on the network that doesn't support WPA2.

TKIP is the older protocol; AES is the newer. According to Wikipedia:```
AES is the first publicly accessible and open cipher approved by the National Security Agency (NSA) for top secret information 
```Therefor, I suggest WPA2-AES.

Since this is a server, are you running without a graphical interface; i.e. Gnome, Unity, et al? If so, you won't be using Network Manager. Do you need some guidance setting up /etc/network/interfaces?

---

