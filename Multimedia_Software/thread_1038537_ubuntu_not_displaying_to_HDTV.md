---
title: "ubuntu not displaying to HDTV"
date: 2009-01-12
forum: Multimedia Software
---

### Post by Miles_Prower on 2009-01-12
So, I have this ubuntu box that I wanted to hook up to the tv. That is, use the tv as the only display. The video card (lspci calls it: Nvidia GeForce MX 4000 rev c1) has an s-video out, and the tv has two s-video ins. I connected the pc to the one on the front of the tv, set the tv's display setting to 'front', and turned the PC on. No video on the tv. The ubuntu box has the restricted drivers enabled, so I figured this would just be plug and play. Grr. I tried to edit the xorg.conf, but only managed to break it (ubuntu would only boot to low graphics mode, so I just deleted xorg.conf, renamed the backup back to xorg.conf and rebooted.) Anyone know what kind of xorg.conf edits I would need to make to get this working? Am I missing anything obvious, here?

Thanks,
Tails

---

### Post by Miles_Prower on 2009-01-13
tried this:
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

and this:
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

to get ubuntu to output a desktop to this tv:
[http://www.walmart.com/catalog/product.do?product_id=3757031](http://www.walmart.com/catalog/product.do?product_id=3757031)

I scoured google, but it doesn't seem like anyone has ever got TV out to work with this card (nvidia geforce4 mx4000). I guess I need a new video card?

Has anyone ever made tv out work with ubuntu? Is there a particular card that works well for that?

---

### Post by Miles_Prower on 2009-01-14
ECHO!

Seriously, though. I could use some help here, even if it's just some dude sayin' "no. doesn't work. shut up." That's validation of the question at least...

Please?

---

### Post by VastOne on 2009-01-15
> **Miles_Prower said:**
> So, I have this ubuntu box that I wanted to hook up to the tv. That is, use the tv as the only display. The video card (lspci calls it: Nvidia GeForce MX 4000 rev c1) has an s-video out, and the tv has two s-video ins. I connected the pc to the one on the front of the tv, set the tv's display setting to 'front', and turned the PC on. No video on the tv. The ubuntu box has the restricted drivers enabled, so I figured this would just be plug and play. Grr. I tried to edit the xorg.conf, but only managed to break it (ubuntu would only boot to low graphics mode, so I just deleted xorg.conf, renamed the backup back to xorg.conf and rebooted.) Anyone know what kind of xorg.conf edits I would need to make to get this working? Am I missing anything obvious, here?

Thanks,
Tails

Any testing I have done with my Nvidia cards and Svideo has been pathetic forcing me to use VGA (standard plugin in HDTV sets now)until I purchased a HDTV capable nVidia card...I know this does not answer your question but it does speak of my experience.  

I am now on a VGA connected to my RCA 47 inch and am very very happy with it

VastOne

---

