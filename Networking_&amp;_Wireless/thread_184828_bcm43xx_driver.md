---
title: "bcm43xx driver?"
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by dafyddhughes on 2006-05-30
Hi Folks

I've just done my first kernel recompile using 2.6.15.7 and the realtime-preemption patch and I love it, but in doing so I managed to kill my AirPort card, which works beautifully in the dapper kernel 2.6.15-23-powerpc.  Being new to all this, I'm hoping I'm not barking up the wrong tree, but my understanding is that I need to recompile with the bcm43xx module - is this correct?

Problem is, I can't for the life of me find the source for that module.  The bcm43xx page doesn't seem to have a link to it.

Can anybody offer information on where to find this module?

Thanks for any help.

cheers
dafydd

---

### Post by smylie on 2006-06-06
[QUOTE=dafyddhughes]
Being new to all this, I'm hoping I'm not barking up the wrong tree, but my understanding is that I need to recompile with the bcm43xx module - is this correct?

Problem is, I can't for the life of me find the source for that module.  The bcm43xx page doesn't seem to have a link to it.

Can anybody offer information on where to find this module?
[/QUOTE]

you're right on both counts:
- you need the bcm43xx module
- there's no link to it on the bcm page. nor is it in their svn repository (that I could find). 

however, as of 2.6.17 it'll be included in the main kernel tree. (i assume this is why they've prematurely taken it off their page?)
Anyway, I've just downloaded the 2.6.17-rc6 patch and sure enough the source files + documentation for the modules are there. Problem is, I can't for the life of me find the damned option to turn it on in menuconfig.

---

### Post by dafyddhughes on 2006-06-07
Thanks for the info.

Well.  There ya go.  I guess I'll have to see if there's a realtime patch for 2.6.17 & then maybe try that.

cheers
dafydd

---

