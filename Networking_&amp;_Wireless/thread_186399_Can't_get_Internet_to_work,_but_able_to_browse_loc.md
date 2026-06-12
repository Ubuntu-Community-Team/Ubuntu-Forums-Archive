---
title: "Can't get Internet to work, but able to browse local network"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by Daiver on 2006-06-01
I'm having some trouble getting my laptop working with the wireless interface.  I was able to get everything working right out of the box with Kubuntu Flight  7, but not with the stable version of Dapper that was released today.

Basically, I can use fish://, VNC, ssh, etc. within my own home network, but I can't use the Internet.  Actually, I'm posting this using VNC and hopefully it will come out just fine.

I'm using a Toshiba M65 laptop, with a Intel 2200BG card, a Motorola WR850G wireless router and Kubuntu 6.06.

I think that I have the gateway setup correctly, pointing to the router's IP, however I just can't get Internet on it.

Does anyone have any ideas?

---

### Post by Daiver on 2006-06-02
Solved.

Do this:  sudo dhclient eth0

Make sure you're using a static IP and replace eth0 for eth1, if that's where your wireless is at.

---

### Post by stengah on 2006-06-03
T H A N K S !!! :D This FINALLY got my wireless going - was hooked up to the access point, but could not access the web. NOW I CAN!!!;)

---

### Post by Daiver on 2006-06-03
Glad to read it helped. =)

---

