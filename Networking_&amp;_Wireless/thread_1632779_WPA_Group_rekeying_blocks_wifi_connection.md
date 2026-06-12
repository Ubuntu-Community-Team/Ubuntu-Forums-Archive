---
title: "WPA Group rekeying blocks wifi connection"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by aspora.isernia on 2010-11-28
Since when upgraded from 8.04 to 10.10, my wifi connection is extremely unstable: every 15 minutes I need to manually disconnect and reconnect to the network. REALLY ANNOYING!!
After many research, I (probably) found the cause: in the event history of wpa_supplicant (taken with wpa_gui) I can read the following
```
2010-11-28 19:49:25.545 WPA: Group rekeying completed with XX:XX:XX:XX:XX:XX [GTK=TKIP]
```
that seems to be related to the connection block.

What can be the cause? I can provide any log/description required...

Thanks in advance for any hint and suggestion!!

A.I

---

### Post by aspora.isernia on 2010-12-04
Bump! No idea at all? (Sorry for the noise...)

---

### Post by aspora.isernia on 2011-04-16
Just for the sake of completeness, I ended to make my wifi working with ndiswrapper.

---

### Post by rhrgbmx on 2011-06-20
Hey I have a similar problem. when I use my router with wpa passwords it stops loading web pages and I need to manually disconnect and reconnect to it however when the password is disabled it is perfect... how exactly did you fix this with ndiswrapper?

---

### Post by aspora.isernia on 2011-06-20
Hi rhrgbmx,
it was a compatibility problem with my wifi drivers. I simply installed ndiswrapper and used the graphic front end to install the windows version of the drivers, following one of the many guides on the official ubuntu documentation.
After that, I've blacklisted the wifi module with the connection problems and after the following reboot everything went perfectly.

So the solution was: completely remove the other drivers and install the windows version using ndiswrapper.

Good luck

a.i

---

### Post by rhrgbmx on 2011-06-20
I installed the ndiswrapper graphical frontend and installed the windows xp 32 bit driver and it seems to be working now, however I have two routers that share the same ssid one is right next (usually 100% connection) to me and the other at the other end of the house (usually 40% connection) and now I seem to get 70-76% connectivity it's strange but atleast its not dropping out. If I have anymore problems I will post back but so far so good.
Thanks Heaps :P

---

### Post by superduperlinuxperson on 2011-06-20
nice job. in fact it may have been conflicting drivers in the first place; you may have had two drivers, but they conflicted. blacklisting mite also fix it.

---

### Post by rhrgbmx on 2011-06-21
Oh ok how do I blacklist? because when I started my Computer this morning I needed to reinstall the driver with the ndiswrapper manager before I could find any wireless networks it's not a big deal really, but hey if I could learn something out of it why not?

---

