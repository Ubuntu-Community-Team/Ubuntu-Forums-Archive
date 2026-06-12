---
title: "wpa never working"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by frazerr on 2009-11-18
Hi.

when I upgraded to 9.04 - WPA encryption stopped working.
unencrypted and WEP still worked.

I found a patch, which was to install the 8.10 WPA something or other.

This last week, my WPA has stopped working again.
I have no idea why, and havent been able to find any work arounds.

When I try to connect to a WPA network it just takes minutes and then asks for the password again.

Can any one help?

Thanks in advance

Frazer

---

### Post by id10twork on 2009-11-18
Check this out [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html). Also, I can tell you that WPA does not work with many things, including Windows Vista. Some computers just don't like it. Unless you're doing some secret stuff on the Internet and are being tracked down by war drivers, WEP should be more than sufficient ;).

---

### Post by frazerr on 2009-11-18
thanks mr id10twork.

I dont think it should be so complicated.  As I said - WPA was working for me before. I dont know why it suddenly stopped.

Also, I travel a lot and need to be able to get on to any network that I visit.  So WPA is essential.

Thanks for your suggestions.

---

### Post by rlelina on 2009-11-19
> **id10twork said:**
> Check this out [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html). Also, I can tell you that WPA does not work with many things, including Windows Vista. Some computers just don't like it. Unless you're doing some secret stuff on the Internet and are being tracked down by war drivers, WEP should be more than sufficient ;).

WPA worked for me in 9.04. As soon as I upgraded to 9.10, it stopped working -- actually it connects but then disconnects after about a minute or so. So I had to fall back to 9.04. I tried running from the CD (not upgrading) to see if that worked differently from upgrading, and still WPA does not work. Unfortunately I cannot use WEP because then other computers in our home network (using USB wireless adapters) surprisingly have problems with WEP but very happy with WPA. My Ubuntu system uses Netgear WG511v1 and my router is WGR614v4.

---

### Post by rlelina on 2009-11-21
> **rlelina said:**
> WPA worked for me in 9.04. As soon as I upgraded to 9.10, it stopped working -- actually it connects but then disconnects after about a minute or so. So I had to fall back to 9.04. I tried running from the CD (not upgrading) to see if that worked differently from upgrading, and still WPA does not work. Unfortunately I cannot use WEP because then other computers in our home network (using USB wireless adapters) surprisingly have problems with WEP but very happy with WPA. My Ubuntu system uses Netgear WG511v1 and my router is WGR614v4.

WPA is working for me now with 9.10 running from CD -- I will upgrade soon. It's working now because I changed my router. Here's my working setup:
```
* WG511v1 PCMCIA card
* Linksys WRT160Nv3 with firmware v3.0.02 build 3
* security set to WPA Personal with TKIP/AES
```

---

