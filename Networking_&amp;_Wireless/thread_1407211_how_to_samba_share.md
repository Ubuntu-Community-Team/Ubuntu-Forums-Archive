---
title: "how to samba share??"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by jamoncillo on 2010-02-15
HI. I have karmic on my laptop, and I can't access my windows network.

I have had previous versions of ubuntu and managed to configure samba. However, since my last reinstall, I can't get it to work. 

Thanks

---

### Post by jamoncillo on 2010-02-15
BTW, when trying to access my network I get the error 'Failed to mount. Unable to retrieve share list from server'

---

### Post by axelsvag on 2010-02-15
There is numerous suggestions on the forum the most thourough is this. If you try the suggestions there, you get rid of the first hurdles.
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

I have the same problem as you but have not found the right solution yet though.

Sometimes I have solved the problems do a complete reboot of the network. First shut down every computer connected to the router. Then shut down the router completely. Wait 15 minutes, restart first the router and then restart every computer. Then sometimes all network services is back.

---

### Post by jamoncillo on 2010-02-18
yeah, nor have I. I don't know really what's going on, since my Linux Mint notebook has no problem coming and going as it pleases all over the network.

Also, because of this samba thing, I can't share files between karmic and my virtual xp on VirtualBox =( 
altought I can do it if I access through my 2wire system page... but only from xp to karmic, not viceversa.

I'll give a try the configuration described on your link, specially the part concerning UFW ;)

---

### Post by jamoncillo on 2010-02-20
tried everything in the link without success, still can't access my samba share =(

---

### Post by pdc on 2010-02-21
would any of this be of any help?

[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)

---

### Post by dmizer on 2010-02-21
Try this:
[http://ubuntuforums.org/showpost.php?p=8854628&postcount=346](http://ubuntuforums.org/showpost.php?p=8854628&postcount=346)

If that doesn't work, try this:
[http://ubuntuforums.org/showpost.php?p=8848476&postcount=344](http://ubuntuforums.org/showpost.php?p=8848476&postcount=344)

---

### Post by jamoncillo on 2010-02-28
uhm.... I hate when things on Linux seem to just fix themselves, hahaha. I have access to my windows computers already.

I think it was DMZ on my router. I DMZed my notebook to get my webcam running in Emesene (still no luck, but works great in Skype). I just gave it regular access and Bam! suddendly I could share my files

I'll try later with my Mint computer and let you know if it works =)

---

