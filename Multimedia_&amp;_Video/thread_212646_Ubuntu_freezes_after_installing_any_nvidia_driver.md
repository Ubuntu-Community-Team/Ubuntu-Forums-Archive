---
title: "Ubuntu freezes after installing any nvidia driver"
date: 2006-07-10
forum: Multimedia &amp; Video
---

### Post by Amorphous_Snake on 2006-07-10
I have a GeForce 4 MX 440. Whenever I install any driver for it, from any source: Automatix, Easy Ubuntu, legacy driver or the latest normal driver, the system would then freeze when I use some programs like Firefox.

I have seen people complaining about this problem when they run a screesaver or something graphical, but this didn't happen to me. I tried running screesavers and they worked fine.

The nvidia driver was the only thing that I installed, so I don't thing it's a conflict from any other program.

The freezing happen on visiting web sites.

The problem happened when I was trying another distro: OpenSUSE 10.1, again after installing the drivers.

I am a Linux newbie and I have asked this question many times under the Beginners' forum, but no one could help me.

I have Ubuntu 5.10.

Note: I have posted this before under the Ubuntu 6.06 forums by mistake. I hope the moderators delete it.

---

### Post by sethmahoney on 2006-07-12
I was using the geforce 6200 and had the same problem - it turned out to be an incompatability between the 6200, my chipset, and the nVidia drivers.  Faced with either using the open source drivers that don't support 3d acceleration or freezing issues with the proprietary driver, I pulled out the card and now I'm using my computer's integrated ATI card with no problems.  Anyway, you might check for more info around here:

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

or consider buying a new card.

---

### Post by RJARRRPCGP on 2006-07-12
I have been getting wording that Nvidia is better than ATI in Linux. 

I'm surprised that you aren't having major issues with the ATI!

I gotten wording that ATI driver configurations are a nightmare!

Appears to be fine with my GeForce 4 Ti 128 MB.

---

### Post by sethmahoney on 2006-07-12
The bug that I experienced only occurs with certain chipsets and certain nVidia cards.  Otherwise their drivers are pretty good (I had no problems on my previous computer).  But I had absolutely no problem with the ATI driver either, so it seems to me as if ATI support is maturing nicely.

---

### Post by RJARRRPCGP on 2006-07-13
> **Amorphous_Snake said:**
> I have a GeForce 4 MX 440. Whenever I install any driver for it, from any source: Automatix, Easy Ubuntu, legacy driver or the latest normal driver, the system would then freeze when I use some programs like Firefox.

I have seen people complaining about this problem when they run a screesaver or something graphical, but this didn't happen to me. I tried running screesavers and they worked fine.


If a crash only occurs when running something very graphical, even when not OC'ing, you likely have a bad video card. Sorry. :( 

The problem also may be because of the video card overheating or there's a compatibility problem between the motherboard and the video card.

---

### Post by Amorphous_Snake on 2006-07-18
Problem solved. Thanks to TSELIOT.

Just add:

Option "NvAGP" "0"

in your /etc/X11/xorg.conf and you can download any driver that you want.

This saved my day. Now I am using Ubuntu 6.06 and I am back in the game!

---

