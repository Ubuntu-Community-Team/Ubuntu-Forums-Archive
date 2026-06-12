---
title: "Adjust monitor brightness"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by Lorian on 2006-08-28
How would I go about adjusting my monitor brightness in Ubuntu? My monitor is getting on a bit and displays too dark. I followd a calibration guide, and it said to put the contrast to max, which I did, adjust the gamma, which I did, but it also says to adjust the increase the brightness so I can see "black level A" at 2.2 on [this](http://www.normankoren.com/Gamma_black_new.png) image, but I can't see even the bottom of the line with brightness on max. Everything looks kind of washed out at the moment. So is there any way to increase the brightness within X? Cheers.

---

### Post by xyz on 2006-08-28
Hi-
I don't know what computer brand you've got; mine's a Toshiba Satellite A40 (laptop) and I run this command as root. Modifying the **0** value alters the brightness.
In fact, I've always wondered if changing *toshiba* to say *IBM* for example would alter the brightness as well! We may find out as other members post here. 
Hope this works for you, too.

echo "brightness:0" > /proc/acpi/toshiba/lcd

---

### Post by Lorian on 2006-08-28
"bash: /proc/acpi/toshiba/lcd: No such file or directory"

Unsurprising really, considering I have neither a Toshiba computer, nor an LCD. Thanks anyway though.

---

### Post by Lorian on 2006-08-28
I found a program on Google called xbrightness, but it is only for XFree86. Would changing to XFree86 so I could use that be an issue? I don't know how this stuff works.

---

### Post by xyz on 2006-08-28
How about searching Google for...**brightness <your computer brand>**? 
Possibly also on your computer brand's very own site or related forum?
By the way, it would certainly help if you told us what computer you're running...
Bye for now.

---

### Post by Lorian on 2006-08-29
It's just a Dell (ugh) desktop PC with a CRT monitor. Don't think there's anything else you need to know.

---

