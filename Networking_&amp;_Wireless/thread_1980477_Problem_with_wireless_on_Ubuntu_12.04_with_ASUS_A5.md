---
title: "Problem with wireless on Ubuntu 12.04 with ASUS A53SV"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by adraniel on 2012-05-15
Good. I have no problem to connect to my wifi network but to be sailing there are times when it gets really slow, I fall, but my network gets slow and takes too long to connect, I have to give several times a page. Here a screenshot of my wireless connection: [http://i.imgur.com/wc2Hz.png](http://i.imgur.com/wc2Hz.png)

I have a ASUS A53SV. Intel Centrino Wireless 1000.

---

### Post by nothingspecial on 2012-05-16
*Thread moved to **Networking & Wireless**.*

---

### Post by cyboreal on 2012-05-17
can you post some more diagnostic information when you are having the network problem? Post the output of `lspci`, `ifconfig`, `lsmod`, `sudo rfkill list all`, and the last relevant lines from `dmesg`.

---

### Post by adraniel on 2012-05-17
> **cyboreal said:**
> can you post some more diagnostic information when you are having the network problem? Post the output of `lspci`, `ifconfig`, `lsmod`, `sudo rfkill list all`, and the last relevant lines from `dmesg`.


I've solved with Option 2 of this page:
[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

Thanks.

---

### Post by adraniel on 2012-05-17
Is that comment would be good solution?

---

