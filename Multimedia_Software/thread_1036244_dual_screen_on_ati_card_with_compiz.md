---
title: "dual screen on ati card with compiz"
date: 2009-01-10
forum: Multimedia Software
---

### Post by DakoCwerf on 2009-01-10
i have asus laptop that i use as primary screen with 1280*800 resolution. my secondary monitor is samsung 22" that supports 1680*1050 resolution. i want to be able to run extended screen (2960*1050) with compiz effects on. i tried 2 different solutions but none of them gives me desired result.

[LIST=1]
[*] i tried to make a big screen with aticonfig tool
Outcome: i have screen of size 1280*800 + 1280*800 and compiz is working.

[*] i removed my video driver and used xrandr with clean xorg.conf file
Outcome: i have extended screen with resolution 1280*800 + 1680*1050 and compiz doesnt work.
[/LIST]

need help in 2 directions please.
[LIST]
[*]how to make big screen with different resolution on my monitors
[*]how to run compiz (or use fglrx driver) with randr 1.2. [or how to be able to run texture_from_pixmap without fglrx]
[/LIST]

specs:
ubuntu 8.10 interpid, ati radeon hd3400, asus m51vr laptop.

can post any logs/conf if you need them. have all of the tries backed up :)

thanks.

---

### Post by markbuntu on 2009-01-10
Did you try using the Catalyst Control Center to set the screens when you were using fglrx?

---

### Post by DakoCwerf on 2009-01-10
i believe its does the same thing as aticonfig but i just purged xconf and made dual with amdcccle - and it sets double width of the primary display as an output (ie i get 2560*800) and i cant change that value. so the same thing here :\

also when i restart x it doesnt save (looks like it doesnt change xorg.conf) but its another issue and is not important.

---

