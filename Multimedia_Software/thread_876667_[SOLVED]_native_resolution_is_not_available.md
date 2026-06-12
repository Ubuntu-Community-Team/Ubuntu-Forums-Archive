---
title: "[SOLVED] native resolution is not available"
date: 2008-08-01
forum: Multimedia Software
---

### Post by Seks on 2008-08-01
hi, I can't seem to get 1680x1050 on ubuntu (it works in windows), the best I have is 1600x1200

There are a bunch of available resolutions but not that one, even in XP I had to create a "custom timing" to use it. But that option is not in nvidia-settings, so I'm pretty lost. I tried adding modelines but it didn't seem to do anything. 

The monitor is an acer al2216w connected via DVI-D, which might be an issue. The xorg log reports it tries all the custom resolutions in xorg.conf but none "validate" and it forces into 1600x1200, which isn't terrible but there is noticeable quality loss compared to xp.

Does anyone know if I was just doing the modelines thing wrong or if there is something else? thanks

---

### Post by Seks on 2008-08-01
FIXED!

Added 	

Option "ModeValidation" "NoMaxPClkCheck"

to the screen section and deleted all the various modelines I was trying, and now the resolution works!

Funny how the solution is usually something simple like that :popcorn:

---

