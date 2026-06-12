---
title: "Flash 10 for Ubuntu 10.04"
date: 2010-05-08
forum: Multimedia Software
---

### Post by HDTimeshifter on 2010-05-08
I upgraded to Ubuntu 10.04 LTS last Sunday, but now my Flash is no longer working and when I try to download from Adobe's site, it only gives me the 32 bit version which doesn't work on Ubuntu 64-bit.  Anybody know how to get Flash (64 or 32-bit) working on my 64-bit system?

---

### Post by lidex on 2010-05-08
Download the installer from this thread:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")

---

### Post by HDTimeshifter on 2010-05-08
Thanks.  I'm up and running again after figuring out how to make it executable.  The first time it failed, but I tried closing Firefox before uninstalling/installing again, and it worked the 2nd time.  I don't know why it's still beta - 64 bit architecture (and 64-bit Linux as well) has been around for at least a couple of years now, and I don't think you can even buy a 32-bit PC these days, and even the retail ones that come with Windows come with 64-bit OS.  It's just frustrating that every new release of Ubuntu seems to break Flash.

---

### Post by lidex on 2010-05-08
> **HDTimeshifter said:**
> Thanks.  I'm up and running again after figuring out how to make it executable.  The first time it failed, but I tried closing Firefox before uninstalling/installing again, and it worked the 2nd time.  I don't know why it's still beta - 64 bit architecture (and 64-bit Linux as well) has been around for at least a couple of years now, and I don't think you can even buy a 32-bit PC these days, and even the retail ones that come with Windows come with 64-bit OS.  It's just frustrating that every new release of Ubuntu seems to break Flash.

A lot of things break flash, I wouldn't blame ubuntu. Nope, I'm thinking adobe should get the hatemail. Funny no one ever mentions them.

---

### Post by HDTimeshifter on 2010-05-08
Well, yeah, the fact that Flash 64 is still beta after 2+ years perplexes me.

But I am also getting unusual "K3B has unexpectedly quit" errors after upgrading to Unbuntu 10.04.  However, they seem to be wrong as my CDs burn ok and K3B doesn't actually quit, so I'm ignoring them even though they are annoying.

---

### Post by pudgypaw on 2010-09-24
The reason is because Adobe made agreements (possibly with Microsoft) to refuse development for Linux/Unix systems. It has resulted in some headaches and issues:

Flash technology isn't efficient on Linux servers. One can crash a linux server by opening up 10+ simultaneous requests for Flash objects. Possible security vulnerability after the crash is induced. Youtube has done a valiant effort in dealing with such issues, their sysadmins told stories of running like headless chickens, shouting explatives doing load balancing on mySQL, haha.

Steve Jobs refuses to allow Flash on iPhones and instead favors HTML5 (new markup language that handles video). Part of his reason is specifically due to Adobe policy I mentioned.

As soon as YouTube switches over to HTML5 and browsers phase out Flash, Adobe will probably go back to grinding PhotoShop, lol.

Have a look at HTML5:
[http://www.thewildernessdowntown.com/](http://www.thewildernessdowntown.com/)
(and there's no flash involved)

---

### Post by Cavsfan on 2010-09-24
Or you could install the "Flash Player "Square" Preview Release" from adobe
[[COLOR=blue]_64 bit flash from Adobe version 10,2,161,22_[/COLOR]]("http://labs.adobe.com/downloads/flashplayer10.html")

It works great for me.

---

