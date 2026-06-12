---
title: "Pages with multiple flash videos are unplayable with firefox, please help"
date: 2009-01-09
forum: Multimedia Software
---

### Post by Axx83 on 2009-01-09
Pages like this one:
[http://linuxiana.blogspot.com/2009/01/i-migliori-spot-su-linux.html](http://linuxiana.blogspot.com/2009/01/i-migliori-spot-su-linux.html)

are absolutely unplayable on my intrepid installation with intel video card.

When I try to open a page like this the system slows down terribly, firefox becomes nearly unusable, if I manage to open the page the videos are laggy, out of synch, choppy, and it's definitely not an internet issue. Scrolling is out of question.

I tried following this bug:
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)

but applying the modifications in xorg doesn't solve the bug at all.

With compiz on or off the problems is absolutely the same, unfortunately.

My computer is a Thinkpad X60s with intel video, intel duo cpu and 1000m of ram, thanks.

please help

---

### Post by zim2dive on 2009-01-09
> **Axx83 said:**
> Pages like this one:
[http://linuxiana.blogspot.com/2009/01/i-migliori-spot-su-linux.html](http://linuxiana.blogspot.com/2009/01/i-migliori-spot-su-linux.html)

are absolutely unplayable on my intrepid installation with intel video card.

When I try to open a page like this the system slows down terribly, firefox becomes nearly unusable, if I manage to open the page the videos are laggy, out of synch, choppy, and it's definitely not an internet issue. Scrolling is out of question.

I tried following this bug:
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)

but applying the modifications in xorg doesn't solve the bug at all.

With compiz on or off the problems is absolutely the same, unfortunately.

My computer is a Thinkpad X60s with intel video, intel duo cpu and 1000m of ram, thanks.

please help

Not sure which GPU you have, but my reading of [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094) suggests Intel GPUs are hosed with Intrepid.

(I was looking for an alternative to my nvidia 8200 which is hosed with full-screen flash).. looks like the grass isn't very green for many IGPs.

---

### Post by timcredible on 2009-01-09
that's just too much flash.  unfortunately, flash is a huge cpu hog and there's just too much flash on that page.

---

### Post by Axx83 on 2009-01-09
> **timcredible said:**
> that's just too much flash.  unfortunately, flash is a huge cpu hog and there's just too much flash on that page.

Well ok my cpu is not stellar it's a intel core duo L2400 at 1,6 ghz but so far has never given me problems, and I guess that page would run on windows xp...but I can't check since I don't have windows installed.

Anyway thanks for the tip

---

### Post by zim2dive on 2009-01-09
> **timcredible said:**
> that's just too much flash.  unfortunately, flash is a huge cpu hog and there's just too much flash on that page.

I dunno.. I can look at that page just fine on my HP laptop (Windows XP) with Intel 965 graphics and 2GHz T7300 processor.  Firefox is at 35%.

so it seems more a linux version of the driver issue than the hardware itself.

---

### Post by Axx83 on 2009-01-09
> **zim2dive said:**
> I dunno.. I can look at that page just fine on my HP laptop (Windows XP) with Intel 965 graphics and 2GHz T7300 processor.  Firefox is at 35%.

so it seems more a linux version of the driver issue than the hardware itself.

What I tought, maybe it's strictly linux flash related, but it could also be linux intel video related or ubuntu firefox related.

---

### Post by theozzlives on 2009-01-09
> **Axx83 said:**
> Pages like this one:
[http://linuxiana.blogspot.com/2009/01/i-migliori-spot-su-linux.html](http://linuxiana.blogspot.com/2009/01/i-migliori-spot-su-linux.html)

are absolutely unplayable on my intrepid installation with intel video card.



Played fine on my intel card, must be your Flash.

---

### Post by Axx83 on 2009-01-09
could you give me your specs ? Thanks

---

### Post by dazer26 on 2009-01-09
That page and all flash is pretty slow for me using Kubuntu 8.10 with both firefox and Konqueror.  I have a dual core amd, and Nvidia 8600gt card.  I dual boot with Win Xp and all flash runs fine.  I'm pretty sure it's a problem with the linux version of the proprietary flash.

---

### Post by Axx83 on 2009-01-09
I simply installed flashplugin-nonfree on a quite fresh installation of intrepid, with a very very common video card for notebooks and a common cpu.

---

### Post by zim2dive on 2009-01-09
> **theozzlives said:**
> Played fine on my intel card, must be your Flash.

What version of Ubuntu? (if you read the bug report I linked to you'll see performance under Intrepid is greatly reduced vs Hardy)

---

### Post by AnRa on 2009-01-09
You may find this add-on useful: [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433).

---

### Post by Axx83 on 2009-01-10
I installed it, it may be useful but that's just bypassing the problem, I wanted to watch those videos not avoid them...

---

