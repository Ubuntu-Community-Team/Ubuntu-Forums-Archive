---
title: "Can't figure this one out!!!!!!!!"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-03-08
I removed my WUBI install and did a side by side install. I downloaded all of my updates and programs etc via a wifi connection at the library. At home I only have dialup. I have a USR USB modem. I've configured Gnome Network Administrator, I've configured wvdial.conf , I've configured pppconf and I've configured Gnomeppp. I did just like before. I click on connect and it connects. Looking at the details it tells the IP I'm connected to and theassigned IP. The issue is when you look at the send and receive data rate it's 0. The sent and receive packets are low. Firefox just keeps going round & round sayiny looking up .......
The firewall is not enabled.

Please help!!

---

### Post by Silvertones on 2010-03-08
The modem works in windows so it's not faulty. If I try Synaptic it thinks it's connected but no data flows.

---

### Post by Iowan on 2010-03-08
I suspect it's something else (but dunno what), but can you ping internet by IP address (74.125.95.147)?

---

### Post by Silvertones on 2010-03-08
> **Iowan said:**
> I suspect it's something else (but dunno what), but can you ping internet by IP address (74.125.95.147)?

I'll give it a try.
This is really discouraging. I uninstall the Wubi and do a proper install and can't use it. It works perfectly at a wifi spot with my Belkin card. You know with the new install it updated to v 20 . I did try 14 and was the same. I have set this up over and over using the same instructions. It's really odd that it does connect to my IP gets IP address etc but when you look at the sent & receive packets it's like 2 & 4

---

### Post by Silvertones on 2010-03-08
no success with ping. Looking at the details in gnome ppp it's stays mostly at idle but will flip quickly to receive and back.

---

### Post by Iowan on 2010-03-08
Gateway setting kosher (**route -n)**?

---

### Post by Silvertones on 2010-03-09
all that shows is the wlan Iface

---

### Post by Silvertones on 2010-03-09
Found the answer deep in the bowels of documentation. My question now is " did version 20 mess this up for everyone with dialup"?

```
gksudo gedit /etc/ppp/options
```

Add this line and save:

replacedefaultroute

---

