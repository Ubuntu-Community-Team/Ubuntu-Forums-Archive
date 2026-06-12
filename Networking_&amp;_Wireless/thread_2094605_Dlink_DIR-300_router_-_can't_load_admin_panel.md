---
title: "Dlink DIR-300 router - can't load admin panel"
date: 2012-12-14
forum: Networking &amp; Wireless
---

### Post by mafaldinha on 2012-12-14
Hi,
I wanted to configure a d-link DIR-300 wireless router. I've connected all the cables and wanted to load the admin panel page at the address given on the router's sticker (something like 192.168.0.1). The problem is that my browser won't load the page. The router was used before with a different config, but I reset it to the defaults by pressing the reset button for 20 sec. I have no idea what the problem might be. The internet via ethernet cable does work properly.

I have Ubuntu 12.10 64bit.

---

### Post by westie457 on 2012-12-14
> **mafaldinha said:**
> Hi,
I wanted to configure a d-link DIR-300 wireless router. I've connected all the cables and wanted to load the admin panel page at the address given on the router's sticker ([COLOR="Red"]something like 192.168.01[/COLOR]). The problem is that my browser won't load the page. The router was used before with a different config, but I reset it to the defaults by pressing the reset button for 20 sec. I have no idea what the problem might be. The internet via ethernet cable does work properly.

I have Ubuntu 12.10 64bit.

Very close. The address should be - 192.168.0.1

An easy mistake to make and I have done the same thing many times.


PS. Welcome to the Forums.

---

### Post by mafaldinha on 2012-12-14
No, no, I was writing the address from the top of my head now and made a typo. Believe me I've checked the address a hundred times...

---

### Post by westie457 on 2012-12-14
Unfortunately the best I can do here is provide a link to the manual for the router. [http://www.scribd.com/doc/18484465/DIR-300-Wireless-Router-Manual](http://www.scribd.com/doc/18484465/DIR-300-Wireless-Router-Manual)

The trouble-shooting part is on page 85 of the document, just scroll down to it.

---

### Post by chili555 on 2012-12-14
I suggest you make sure the ethernet port on your computer is connected to a *LAN* port on the router. Open a terminal and do:```
sudo ifconfig eth0 192.168.0.2 up
firefox 192.168.0.1
```Doesn't the administration page of the router open up?

---

