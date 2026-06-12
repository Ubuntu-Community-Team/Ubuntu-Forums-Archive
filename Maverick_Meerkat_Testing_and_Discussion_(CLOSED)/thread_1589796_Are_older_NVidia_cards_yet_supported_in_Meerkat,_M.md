---
title: "Are older NVidia cards yet supported in Meerkat, Maverick?"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TBerk on 2010-10-06
I was trying out the beta 10.10 w/ my older Nvidia FX5200 and it couldn't run in anything but low graphics mode.

I rolled back to 10.04 for now, but just downloaded the Release Candidate .iso; but is it just  waste of time until I invest in a later day video card? (or find another chipset/vendor bd in the surplus pile...).


TBerk

ps- I forgot to separate my tags w/ commas...

---

### Post by mc4man on 2010-10-06
take a look in Additional Drivers, if you see the 173 driver listed then install and see how it goes. (should be there

---

### Post by demetrisk on 2010-10-07
@TBerk

Nvidia has updated its 173 driver to support xserver 1.9, and now the updated driver is in Maverick too.  It was added three days ago:

[https://lists.ubuntu.com/archives/maverick-changes/2010-October/008724.html](https://lists.ubuntu.com/archives/maverick-changes/2010-October/008724.html)

[https://lists.ubuntu.com/archives/maverick-changes/2010-October/008726.html](https://lists.ubuntu.com/archives/maverick-changes/2010-October/008726.html)

I don&#8217;t think it is included in the 10.10 RC ISOs, but it is in the repo and you will get it if you upgrade from 10.04.

(I have an exact same card as you, FX 5200, I upgraded to 10.10 from 10.04 a couple of days ago, and everything works fine.)

---

### Post by TBerk on 2010-10-07
Well then, as they say HooRa!  

I'll give it a try this weekend....

Thx to the bot of you.


TBerk

---

### Post by kumaryu on 2010-10-07
The driver version you need is Nvidia-173 (173.14.28 ). As noted above, this is now the current package in the repositories for Maverick but was not  included with RC iso.

Nvidia-173 is for the following: 
GeForce 5 FX series: FX 5900 Ultra, FX 5200 Ultra, FX 5100, FX 5900XT, FX 5900, FX 5950 Ultra, FX 5200LE, FX 5900ZT, FX 5700 Ultra, FX 5600XT, FX 5800 Ultra, FX 5700, FX 5700LE, FX 5200, PCX 5900, PCX 5750, FX 5600, FX 5600 Ultra, PCX 5300, FX 5700VE, FX 5800, FX 5500


I understand that we are still waiting for an update to -96 drivers for compatibility with Xorg Xserver 1.9. The cards affected are:
GeForce 4 MX series
Quadro NVS series
Quadro 4 Go series
Quadro 2 Go series
GeForce 4 Ti series
GeForce 2 series
Quadro 2 MXR series

Would be interested to hear the experiences with/workaround for those cards.

---

### Post by cascade9 on 2010-10-07
96 drivers are goign to take a while... 

> 09-30-10, 10:22 PM 			 			

@luk1don: I haven't forgotten about 96.43.*, I just haven't had much time to work on it lately. I'm hoping to get started on xserver 1.8 support soon, and xserver 1.9 support shortly thereafter.

[http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5](http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5)

BTW, I'm sure I've seen an nVidia staffer say that the 71.xx drivers will never get an xorg 1.9 version.

---

### Post by eyelessfade on 2010-10-07
> **cascade9 said:**
> 
BTW, I'm sure I've seen an nVidia staffer say that the 71.xx drivers will never get an xorg 1.9 version.

71.86.14 was released 2010.08.04. So at least they got newer kernel support. Would be fun if they supported xorg 1.9 as well.

Windows legasy drivers only exist for windows 2003 server and older, so at least nvidia products have 7 years more support then windows ^^

---

