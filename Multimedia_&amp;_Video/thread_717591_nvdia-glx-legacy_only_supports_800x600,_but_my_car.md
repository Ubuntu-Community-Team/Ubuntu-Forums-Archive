---
title: "nvdia-glx-legacy only supports 800x600, but my card should do better"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Michl on 2008-03-07
On a desktop running Gutsy with a VE510+ monitor which
supports 1024x768 resolution.
The video card is a Viper V770 with a NVIDIA RIVA TNT2
chip set that supports 3d up to resolutions higher than 1024x768.
(No problem in Windoze).

But when I install the nvidia-glx driver (I have installed it
in many different ways, including just enabling the
restricted driver in Gutsy), the highest resolution
available is 800x600.   How can I change that?

By the way, I also had this problem in Feisty.

Thanks,
Michael

---

### Post by Michl on 2008-03-07
Ok, answered my own question, mostly.

FOund 
FixVideoResolutionHowTo
in community documentation.

Edited xorg.conf adding the vertical and horizontal ranges
per directions.   But that didn't work (put xorg into failsafe mode)
The output from
ddcprobe | grep monitorrange
was wrong, it seems, and so instead I went with the
specs given by the manufacturer.  

So that worked and now I have the nvdia driver and
acceleration.  There is a fly in the ointment.  When
checking screensavers, an image is left like a haze
in the upper right corner.  Then when I try to restart
xorg with ctrl Alt Backspace, I get past login but
nothing loads after that.  I have to restart the computer
and everything loads properly.

---

