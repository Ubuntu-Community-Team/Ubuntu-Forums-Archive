---
title: "ATI vs FGLRX drivers"
date: 2009-03-13
forum: Multimedia Software
---

### Post by tpl on 2009-03-13
Google Earth 5 will not run on my machine ( Intrepid) with ati driver on Radeon X800 card.  Splash screen comes up and then just goes away.  It DOES run with FGLRX driver .

Is there an answer?  Lines in xorg.conf? Some magic fix somewhere?

---

### Post by binbash on 2009-03-13
It is not a video driver thing.Read here and move the required files : 

[http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html](http://www.ubuntu-inside.me/2009/02/howto-install-google-earth-50-beta-on.html)

---

### Post by tpl on 2009-03-13
That is exactly how I installed GE 5 in the first place. Including that rename of libcrypto. When I installed it I was running fglrx.  Fglrx has a problem on my machine at startup, non-fatal, just requires the machine to be started twice, so I wanted to return to the ati driver.

---

### Post by steefjeqv on 2009-03-14
Hi,

There are updated xorg ati drivers made available by Tormod Volden for Ubuntu. Always make sure you install both the radeon and ati package.

Also remove all the fglrx stuff before you install the open source drivers.

[http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/") 

Greetings,
Steven

---

