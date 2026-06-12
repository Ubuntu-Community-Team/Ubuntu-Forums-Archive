---
title: "Network is Slow"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by Mosaab on 2009-07-23
How can I change the wlan0 speed to 100MB ?

currently its working on 10 only .. and it makes file transfer really slow !

---

### Post by Brandon Williams on 2009-07-24
What type of wireless card have you got? Is it a wireless N card? And all of your hardware is wireless N? The only way you can get the speed you're looking for on wireless (assuming you mean 100Mbps, not 100MBps) is with wireless N hardware.

If you tell us what kind of wireless hardware you have, we might be able to verify whether it is known to work well under Linux and tell you whether there are any tricks for getting it to work better.

---

### Post by Mosaab on 2009-07-24
thanks for the reply ... this is my network card :

```
mosab@mosab-laptop ~/Desktop $ lspci | grep lan
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

---

### Post by jocko on 2009-07-25
> **Mosaab said:**
> thanks for the reply ... this is my network card :

```
mosab@mosab-laptop ~/Desktop $ lspci | grep lan
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```
As it's a wireless A/B/G the maximum is 54 Mbit/s, so you'll never get it to run at 100 Mbit/s, you would need a wireless N card and a router that supports wireless N to be able to get any higher than 54.
Make sure your router is set to use either the "mixed" or "wireless G only" wireless mode (check your routers manual on how to access it's settings).

---

### Post by Mosaab on 2009-07-25
I have a linksys router and its set to mixed mode, how can I change my wireless card to 54 Mbps at least ?

---

### Post by Mosaab on 2009-09-02
some guys in the forum suggested this :

sudo wiconfig wlan0 rate 54M 

after than I check it by the command iwconfig ... and its really changed to 54 .. but when i try file sharing its still very slow ... like 500 K/s

---

### Post by jnorthr on 2009-09-02
Try re-positioning your kit. If the pieces of your network are near electric lines or major metal structures like inside your walls, etc., it may improve speeds to do this. Microwave cookers, etc. can play havoc with your speeds, also other users in adjacent areas or buildings that use wireless may also interfer with your own kit, but that's something you can't control.

---

### Post by Mosaab on 2009-09-02
thanks for the reply .. but I dont think this is the problem cause the signal strength is 92 % ... I think this number determines if I have this problem or not .. am I right?

---

