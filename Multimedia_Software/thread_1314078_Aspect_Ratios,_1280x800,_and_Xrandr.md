---
title: "Aspect Ratios, 1280x800, and Xrandr"
date: 2009-11-04
forum: Multimedia Software
---

### Post by Inaia on 2009-11-04
EDIT: Solved. Took 3 hours, but I finally fixed it....for whatever reason, it suddenly added it to 'xrandr'.

I have a full 16:10 ratio monitor on my laptop, supports up to 1440 x 900, but for whatever reason it's showing every resolution BUT 1280 x 800, and using 'xrandr --newmode' command along with every variation of 'modeline "1280x800"' that I can come up with is resulting in the following error:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  25
  Current serial number in output stream:  25

Any help with this would be appreciated, I'm running an Acer Aspire 9410 with Mobile Intel 945GM.

---

