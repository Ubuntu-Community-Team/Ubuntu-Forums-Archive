---
title: "Broadcom 4312 trouble"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Megajoshthebest on 2011-08-08
Hi guys, I was wondering why won't my netbook access some pages (specifically facebook) using wireless, but I can access on LAN. Its a Compaq Mini 110 with Ubuntu 11.04 and Windows 7 dual boot with Broadcom 4312 wireless card. I can open other web pages, its just that certain pages such as facebook show the waiting for [www.facebook.com](www.facebook.com), I can get past the login page, but when it asks for device authorization, it just fails, and when it does slip, I can't open anything except for the news feed. Help would be appreciated, thanks :KS

---

### Post by Megajoshthebest on 2011-08-10
anyone?

---

### Post by Megajoshthebest on 2011-08-11
It only happens on facebook and when I'm on wireless, it also wont work on ANY browser at all. I can only access it in private browsing in opera and chrome, but can't get past the login screen, normal browsing wont even open the page

---

### Post by TBABill on 2011-08-11
Facebook is heavily reliant on Flash. Have you tried to install ubuntu-restricted-extras and see if that helps? It could be a codec issue with flash or java that's not working. You can also try to install Sun Java Plugin by enabling the partner repo in your software sources, then doing an apt-get update, search for Sun Java and mark the plugin for installation. It'll pull in dependencies.
 
I would suggest first installing restricted extras, then sun java. Restricted extras pulls in lots of codecs, but it also installs open source java. It's not as good as Sun Java and doesn't work on all sites, but you need the rest of the restricted extras packages. 
 
I'm doubting it's the wireless. I have the same chipset in two laptops that work fine with Facebook, but without the extra codecs it's a bear of a site to deal with.

---

### Post by Megajoshthebest on 2011-08-14
TBABill, thanks for the reply, unfortunately, it didn't work. But, I tried Firefox using wine and BOOM! it worked. Facebook opens correctly, but I wonder why it doesn't work with linux browsers, even empathy, and sometimes with other pages, I too get an error. Can anyone solve this?:confused:

---

### Post by Megajoshthebest on 2011-08-14
PS: IT DOESN'T WORK AGAIN! Grrr, I CAN OPEN FACEBOOK USING LAN, BUT NOT WHEN ON WIRELESS. It also doesn't work on Firefox via Wine. :(

---

### Post by Megajoshthebest on 2011-08-20
anyone?

---

