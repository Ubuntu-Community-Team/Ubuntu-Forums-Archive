---
title: "No Wireless on AAO after update today!!!!"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by stoopid_noob on 2008-12-20
I am about to lose my mind?!?!?! What kind of OS is this?! haha 

It took me two days to get the wireless working, I do an update and it completely renders the netbook useless again! 

Under Hardware Drivers there is no driver anymore. I went through everything that I changed before to get the wireless working. I noticed that under the madwifi tools ath5k was blacklisted now so I put a # in front of it to null it out. Rebooted and figured that would be it. 

What the heck! Anyone else? I mean I hate Windows as much as the next guy, but at least it works most of the time.

---

### Post by wwusnobrdr on 2008-12-20
Hey noob I had the same problem as did many people.  Was it a partial upgrade you did?  The backports package for the kernel did not get released until today, so try and update to install that for your kernel.  If that does not work you can install compat-wireless, instructions here [http://wireless.kernel.org/en/users/Download#Wheretodownload](http://wireless.kernel.org/en/users/Download#Wheretodownload) .

---

### Post by stoopid_noob on 2008-12-20
Awesome! Thanks man!

---

