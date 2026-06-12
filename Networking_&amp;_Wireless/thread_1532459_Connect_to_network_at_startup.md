---
title: "Connect to network at startup"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by kornfan71 on 2010-07-16
Hello all,
I have a wireless network adapter that I finally got working with Ubuntu 10.04, but now I have a question. Is it possible for the network adapter to connect to my network at startup, rather than waiting for NetworkManager to do it?
I was able to do this in 9.04, but since Ubuntu started using upstart, I have no idea what to do.
Help?? :confused:

---

### Post by auroraa9420 on 2010-07-16
> **kornfan71 said:**
> Hello all,
I have a wireless network adapter that I finally got working with Ubuntu 10.04, but now I have a question. Is it possible for the network adapter to connect to my network at startup, rather than waiting for NetworkManager to do it?
I was able to do this in 9.04, but since Ubuntu started using upstart, I have no idea what to do.
Help?? :confused:


yea i had the same problem today, just the problem is i have 2 machines connected to my routher (windows and linux)

the windows machine resives internet normaly but i cant even connect to my routher with the linux machine (cant see it on the routher ether :S)

---

### Post by kornfan71 on 2010-07-16
I appreciate the response, unfortunately I don't think you got my meaning...
My adapter connects just fine, I just want to know if it is possible to connect during the boot sequence (i.e. before I log in).

Thanks for the response, though. ;)

---

### Post by Iowan on 2010-07-16
This is probably only half an answer, too. The "Available to all users" option *should* enable networking before login, but I'm not sure if it can/will log into a network...

---

### Post by kornfan71 on 2010-07-17
Thanks for the response lowan.
Unfortunately, that didn't work. I found a tutorial once about getting networking up at the login screen, but I can't seem to find it. However, I don't think it'd do me much good, since I have Ubuntu automatically log me in now.

It seems like there must be some upstart script that could accomplish this seemingly simple task. :?

---

### Post by kornfan71 on 2010-07-18
Bah! I was just browsing the forums and found the answer (don't ya just hate that?):
/etc/network/interfaces
I just added:
```
auto ra0
iface ra0 inet dhcp
wpa-conf /etc/wpa_supplicant.conf

```
And then I made an appropriate wpa_supplicant.conf file, and all appears to be well. *sigh*


Thanks for your help, though! :D

---

