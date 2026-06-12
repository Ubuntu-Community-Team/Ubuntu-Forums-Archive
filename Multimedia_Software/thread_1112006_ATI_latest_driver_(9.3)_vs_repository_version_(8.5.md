---
title: "ATI latest driver (9.3) vs repository version (8.54.3)"
date: 2009-03-31
forum: Multimedia Software
---

### Post by surfdoc on 2009-03-31
Hi,

I was wondering if anyone had any experience with the latest ATI driver from their website(9.3). The repository one (presumably xserver-xorg-video-ati) works ok for me, but I get the usual compositing - video flicker problem. It's not bad enough for me to want to meddle - unless I know it's going to improve anything

Cheers

kubuntu intrepid
ati radeon hd 3400

PS does hibernate/sleep work with this driver?

---

### Post by markbuntu on 2009-03-31
The repository version is basically a pre release version of the 8.11 driver I think. I am using the 9.2 driver right now in Intrepid and the compositing and flickering problems are gone. 9.3 is even better I have heard so I will be going to it soon.

Just remember to remove completely the old driver before installing the new one or you will have problems when you get kernel updates, and read the release notes and installer instructions.

You should also update your sig, I thought you were talking about gutsy.

---

### Post by surfdoc on 2009-03-31
Cheers - definitely sounds like it's worth a try. I'll post back with my findings (might be a few weeks before I can risk messing with it though).

---

### Post by Melcar on 2009-03-31
The 9.3 is much better.  Flickering opengl apps. with Compiz is no more.

---

### Post by surfdoc on 2009-04-03
Well that was surprisingly easy. Just downloaded the installer from the ati website and ran it. Had to do a rescue boot to run aticonfig --initial -f coz of black screen though.

The flickering seems to have gone. Only one observation - amdcccle reports the driver version as 8.59.2 not 9.3. Not that I care, since its working fine now.

Cheers again guys!

---

### Post by zika on 2009-04-03
> **surfdoc said:**
> Well that was surprisingly easy. Just downloaded the installer from the ati website and ran it. Had to do a rescue boot to run aticonfig --initial -f coz of black screen though.
The flickering seems to have gone. Only one observation - amdcccle reports the driver version as 8.59.2 not 9.3. Not that I care, since its working fine now.
Cheers again guys!
9.3:version of Catalyst. 8....:version of the driver

---

### Post by iheartubuntu on 2009-04-04
> **zika said:**
> 9.3:version of Catalyst. 8....:version of the driver

Any idea if this will work in Jaunty? I miss playing Super Tux Kart :p

---

### Post by zika on 2009-04-04
> **shirteesdotnet said:**
> Any idea if this will work in Jaunty? I miss playing Super Tux Kart :p
I've asked everywhere... no answer. I doubt I will ever use ATI driver. waiting for radeon ... :)

---

### Post by Melcar on 2009-04-04
> **shirteesdotnet said:**
> Any idea if this will work in Jaunty? I miss playing Super Tux Kart :p


What kernel does Jaunty use?  9.3 only supports up to the 2.6.28 kernel.  Additionally, the 9.3 driver is the last one to support cards older than the HD2K series, so if you have one of those cards and plan to keep using newer distro releases you best start looking into the open source drivers.

---

### Post by zika on 2009-04-04
> **Melcar said:**
> What kernel does Jaunty use?  9.3 only supports up to the 2.6.28 kernel.  Additionally, the 9.3 driver is the last one to support cards older than the HD2K series, so if you have one of those cards and plan to keep using newer distro releases you best start looking into the open source drivers.
Jaunty uses 2.6.28-11-generic #40... I think the problem with Jaunty is the Xorg version ...

---

### Post by Pitboss on 2009-04-12
I've just installed jaunty, but I have problems with the fglrx driver. When I use the proprietary driver from jaunty repos - 8.600 I have problems even when maximizing windows with compiz on. The gnome-screensaver crashes all the time. And I can't get 9.3 work for me, I don't know why. I follow the steps in the wiki but it doesn't help. So if anyone is using 9.3 under jaunty, please let me know.

---

### Post by markbuntu on 2009-04-12
You cannot use the 9.3 driver on jaunty because it does not support the new xserver in jaunty The driver available from the repos is a pre-release version of 9.4 and has problems so you might want to wait a while.

---

### Post by Pitboss on 2009-04-13
> **markbuntu said:**
> You cannot use the 9.3 driver on jaunty because it does not support the new xserver in jaunty The driver available from the repos is a pre-release version of 9.4 and has problems so you might want to wait a while.

Thank you, that's a relief. Lets hope that 9.4 won't be a complete failure.

---

### Post by markbuntu on 2009-04-13
Also, the 9.4 driver does not support any rv200-500 cards so if you have a card older than the HD3xxx series you cannot use 9.4 but the open source drivers in jaunty work very well with those cards, better than fglrx did for many of them.

---

### Post by surfdoc on 2009-05-06
I did a fresh install of jaunty kubuntu 64k with the repository fglrx drivers - and apart from having to run aticonfig --initial i've had no problems. :) Sorry to hear that's not everyones experience!

---

### Post by bluelamp999 on 2009-05-06
I found that the 9.3 Catalyst driver broke suspend/resume on my Dell Latitude D810 with Mobility Radeon X300 card.

Reverting to an earlier version fixed the issue...

---

