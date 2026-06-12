---
title: "Trying to Make a Wireless Access Point"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by dragonfellow17 on 2009-05-27
I think I'm doing this right but I can't get firewall to work because it says the my wlan0 is not ready. So how can I make it ready? When I do ifconfig it only shows lo and eth0. Also do I need 2 NICs and a wireless card to do this or can my eth0 share both the wireless and use the internet?

---

### Post by superprash2003 on 2009-05-27
you can bring down wlan0 and it hopefully will not show that error.. type sudo ifdown wlan0 in your terminal

---

### Post by dragonfellow17 on 2009-05-27
It says
ifdown: Interface wlan0 not configured.

---

### Post by superprash2003 on 2009-05-28
will you be using wlan0?

---

### Post by dragonfellow17 on 2009-05-28
Yes, It will be for the access point for the wireless.

---

### Post by superprash2003 on 2009-05-29
ok , give wlan0 a static ip , that should fix the problem..[http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

