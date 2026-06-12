---
title: "Wireless network stops working after a while."
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by lovabill on 2011-08-19
I have a wireless network using this driver:

Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter

and everything works fine for some time. After a few hours or maybe less (if I push bandwidth to the limit) the Internet freezes. I can't even ping my router. If I disconnect and reconnect either the device or the connection via network manager , it does work for a minute only and then freezes again. If I restart Ubuntu entirely, it works again. But for a while...

It works 100% in Win7 and I have no problem at all there. But I am very annoyed that I cant have reliability in Ubuntu. I want Ubuntu as default.

It has something to do with drivers or an inner variable or buffer or something.

At least, is there any way to reset my network connection without rebooting the OS? 

I tried sudo /etc/init.d/networking restart but it gives me:
Ignoring unknown interface wlan0=wlan0.

Any other suggestion?

---

### Post by jfed on 2011-08-19
Do have/need any proprietary wireless card drivers installed?

System>Administration>Additional Drives

---

### Post by lovabill on 2011-08-19
No additional drivers are available.

PS.: I changed MTU from 1500 to 2272 and things seem to go smoother now. But it froze again after a longer while this time.

PS2: I finally changed my wifi adapter (!!!) and now everything is fine. Hopefully the old one is ok for my father's windows system so everybody is happy now. TP-LINK seems to work 100% with Linux.

PS3: Also this thread is solved (somehow).

---

