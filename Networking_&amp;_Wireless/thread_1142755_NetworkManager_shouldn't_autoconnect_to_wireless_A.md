---
title: "NetworkManager shouldn't autoconnect to wireless AP's"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by map84 on 2009-04-29
Hi,

At university I'm connected to their AP using NetworkManager. While at home, I'm using a 3G wireless pc-express-card. How could i disable the autoconnect to a wireless AP while I'm using my 3G-card without killing wlan with the hardware-switch and without setting every new spotted wireless AP manually to not autoconnect?

NetworkManager 0.7.1~rc4.1.cf199a964-0ubuntu2
Ubuntu 9.04 (Jaunty)

---

### Post by brunogirin on 2009-04-29
When you're at home, right click on the NetworkManager applet and uncheck "Enable Wireless". That should tell NM to not use your internal wireless but connect through alternative methods, such as your 3G card.

---

### Post by map84 on 2009-04-29
Thank you for the answer.
I thought of a more complex solution, so I didn't discovered this obvious option.

---

### Post by HumidBean on 2009-05-27
> **brunogirin said:**
> When you're at home, right click on the NetworkManager applet and uncheck "Enable Wireless".
This does work, of course, but In Ubuntu 8.04, NetworkManager would dynamically switch between ethernet and wifi as needed.  Plugging in a cable would drop wifi, and removing a cable would auto-connect to any known WAP.  In 9.04, wifi is always connected, even when an ethernet cable is plugged in.  The core problem seems to be that 9.04's version of NetworkManager lost the ability to auto-switch between interfaces, and this is what really needs to be addressed.

---

