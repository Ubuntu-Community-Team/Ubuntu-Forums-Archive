---
title: "Intel 5100 + Jaunty + eduroam"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by Xkper on 2009-04-27
Hi...
I'm having a problem connecting to eduroam through my laptop. Even the guest-eduroam I can't connect.
I ran the command "iwlist wlan0 scanning essid eduroam" and it doesn't detect eduroam network only guest.

I tryed with network-manager, wicd, a script given by my university and even by hand and nothing works.

Does anyone had the same problem? 

Regards.

---

### Post by ilhamwk on 2009-04-28
Yes, I encounter the same problem. I've filed a [bug report]("https://launchpad.net/bugs/360444") at launchpad, but no replies so far (probably because it was near Jaunty's release). Other bug reports regarding this matter on launchpad haven't been completely resolved, AFAIR.

---

### Post by Xkper on 2009-04-28
I solved the problem by installing this packages:


linux-backports-modules-jaunty-generic_2.6.28.11.15_i386.deb
linux-backports-modules-2.6.28-11-generic_2.6.28-11.12_i386.deb
linux-backports-modules-jaunty_2.6.28.11.15_i386.deb

Now I have no problems, wireless + eduroam works 100%

---

### Post by ilhamwk on 2009-04-29
Thanks, but that update doesn't work on my laptop. I still get the same symptoms.

---

