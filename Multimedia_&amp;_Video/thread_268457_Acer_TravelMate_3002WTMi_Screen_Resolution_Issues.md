---
title: "Acer TravelMate 3002WTMi Screen Resolution Issues"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by om3ga on 2006-09-30
Hi,

I have an Acer TravelMate 3002WTMi, which I recently installed Ubuntu on, it works great (it even detected my external soundcard!), but for some reason it doesn't want to let me use a screen resolution of 1280x800, instead it forces me to use 1024x768 on a widescreen monitor (ugh!). I have tried editing /etc/X11/xorg.conf and have tried using 915resolution (and 855resolution as a crazy last resort!), and none worked.

If anyone has any ideas how I could do this, I will be really grateful!

Thanks,

-Ben

---

### Post by tseliot on 2006-09-30
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by Jorge on 2006-10-06
I have the same laptop model. I use this as a reference:

[http://www.karinsche.de/acertm3000.php  ]("http://www.karinsche.de/acertm3000.php")

But I change the mode to 54.

This is my 915resolution file:

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=54
#
# and set resolutions for the mode.
#
XRESO=1280
YRESO=800
#
# We can also set the pixel mode.
# Please note that this is optional,
# you can also leave this value blank.
BIT=

```

I hope it helps

---

### Post by kmldqj on 2006-10-06
I have a TravelMate 3002 too. You need to edit /etc/default/915resolution and set MODE to 54, do not use the default AUTO.

---

