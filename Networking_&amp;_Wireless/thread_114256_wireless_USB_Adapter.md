---
title: "wireless USB Adapter"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by steunzool on 2006-01-08
Hello,

I want to install ubuntu but my wireless USB-adapter isn't working when I try to use the ubuntu live-CD.  

It's a 802.11g 54 Mbps USB Adapter
Model: USR805422
From USRobotics.

Can I get it to work or will it work in the normal installation?

thanks in advance

Jona

---

### Post by Poppalarge on 2006-01-09
It will work after a fresh new installation and after you install ndiswrapper (and wpa_supplicant if you need wpa encryption).

I have the same usb-dongle and it used to work great, but somehow something went wrong and I can't connect to my wlan anymore. It can see my network (and all other wireless lans in my vicinity) but my notebook can't obtain an ip from my router. I'll look into it when I have some free time and I'll keep you posted.

---

