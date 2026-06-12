---
title: "Xonar 1.3 HDav Slim"
date: 2009-08-19
forum: Multimedia Software
---

### Post by arkania on 2009-08-19
Just recently purchased this great sound card, but unfortunately I cannot get it to work in Ubuntu.  It sounds fantastic in windows, but I really want to get it running under linux.

Has anyone had success with this?

---

### Post by jalyst on 2009-08-31
I will buy the deluxe version soon & will try to get it working. 
If I find anything out I'll let you know.

Likewise keep us all posted if you find a solution!

Cheers

---

### Post by arkania on 2009-09-04
Thanks jalyst, will do.

---

### Post by jalyst on 2009-09-21
Have a look here and this site in general
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)

I recall one of the main devs saying that there won't ever be support for hdmi on the on the hdav & hdav deluxe, only analogue. 
So that means no support at all for the slim as it's only digital....

I could be wrong though, it was a while ago and a lot of other stuff has gone through my head...

Sign up to the alsa-users mail-list
[http://www.alsa-project.org/main/index.php/Mailing-lists](http://www.alsa-project.org/main/index.php/Mailing-lists)
you can get more advice there, I think there's even an IRC channel.

I may not be getting a hdav deluxe if i can find out what's happening with the freakin Essence ST deluxe!

---

### Post by arkania on 2009-09-23
Thanks for the info Jalyst.  It would be sad if they don't support this card, it really has excellent sound quality and is a top notch HTPC solution.  

Unfortunately that means I'll have to stick with Windows for now, which I hate, but the difference in sound quality between the Asus and my onboard is a show stopper for me.  However, saying that, I'm wondering if I convert my HD audio content to FLAC (HD audio really being the reason I went to the ASUS card) and see how it sounds on my other sound card...

I'll keep an eye on the Alsa site though, hopefully they'll come up with a solution in the near future.

Thanks again!

---

### Post by jalyst on 2009-09-23
no worries, all the best!

---

### Post by groggy-froggy on 2009-10-10
I think the HDAV slim may be supported soon (maybe next Alsa release), as it uses the same processor as the Deluxe (AV200).

I think you can get HDMI, sound + video, by using your GFX card DVI output, and DVI-HDMI adapter (usually supplied with your GFX card), at least it was with mine (Nvidia GTX285) & SPDIF. Depends if you need audio via HDMI, or have a separate surround amp. Bit of a fudge, i know.

Clemens mentions this here.
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg25519.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg25519.html)

I have a HDAV1.3 Deluxe, and there is a problem with the latest Alsa drivers (alsa-lib-1.021a & alsa-driver-1.021). Sound does not work after re-boot. However alsa-lib-1.020 & alsa-driver-1.020 seem to work ok for SPDIF and Analogue audio out.

Keep an eye on the xonar driver status on the Matrix page, as there seems to be frequent changes, and the slim may be included quite soon.

You will have to update your Alsa drivers, when it is.

edit. The Essence is now supported.

---

### Post by jalyst on 2009-10-10
oh sweet, I'm getting the ST + H6 6.1 expansion card!
Dont care much about digi passthrough, I'm intending to make my htpc the AVR. 
LT will also be getting PCI digi amp card.

> **groggy-froggy said:**
> The Essence is now supported.

---

### Post by jalyst on 2009-10-10
LOL that's my email to him, forgot everything he said.

> **groggy-froggy said:**
> Clemens mentions this here.
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg25519.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg25519.html)

---

### Post by arkania on 2009-10-20
Ah, that would be sweet!  I'll keep my eye out on Alsa.

---

