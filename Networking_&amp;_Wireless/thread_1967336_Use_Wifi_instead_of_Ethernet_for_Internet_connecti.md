---
title: "Use Wifi instead of Ethernet for Internet connection"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by zouhair on 2012-04-28
Hi,

I'll try to explain my problem as clear as I can.

I get my Internet connection from Wifi (renting a room), but I have three computers (mac, win and linux) in my room.

I have those three computers on a local ethernet LAN (makes sharing files and using synergy much faster).

Now my problem, if I connect over wifi on my Ubuntu comp, everything works perfectly but as soon as I connect my Ethernet cable to it I lose my Internet connection as Ubuntu tries to get it from the Ethernet by default not from the Wifi card.

Now I want to tell Ubuntu to use the Wifi for Internet connection by default, it is easy to do on Win and Mac but I can't find a solution for Ubuntu to save my life.

Anyone has any idea how to do that?

Ubuntu 12.04 LTS
Linux heronz 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 athlon i386 GNU/Linux

Thanks

---

### Post by zouhair on 2012-04-28
bump

---

### Post by zouhair on 2012-04-28
Yay, this command worked :

sudo ip route replace default via 192.168.1.1 dev wlan0 proto static

---

### Post by Rayaz on 2012-08-17
Am in the same boat, but your solution doesn't work for me.

Any pointers?

Regards

---

### Post by rukiaEnix on 2012-08-17
I think you will find your solution here: [http://superuser.com/a/217510](http://superuser.com/a/217510)

---

