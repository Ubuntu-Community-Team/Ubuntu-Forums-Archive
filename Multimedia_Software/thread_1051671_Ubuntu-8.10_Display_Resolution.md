---
title: "Ubuntu-8.10 Display Resolution"
date: 2009-01-27
forum: Multimedia Software
---

### Post by huzefa_from_kuwait on 2009-01-27
Mine is Ubuntu 8.10, upgraded a month back from 8.04.
Screen size is 15" but widescreen.
The maximum resolution UbuntU detects is 1280x768
Can I make it to detect 1440x900.

I have tried almost everything I could including manually entering xorg.conf file entries. But still no success.

I would be really appreciated if anyone could give me a workaround for this.

Thanks.

---

### Post by mikewhatever on 2009-01-27
Can you please post the output of <xrandr -q> without the brackets.

---

### Post by huzefa_from_kuwait on 2009-01-27
Here it is,

Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x768+0+0 (normal left inverted right x axis y axis) 305mm x 183mm
   1280x768       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9

---

### Post by mikewhatever on 2009-01-28
Are you sure that 15" screen can do 1400x900? Some high end notebooks may have such resolution for 15", but it's quite uncommon.

---

### Post by huzefa_from_kuwait on 2009-01-28
I have a dual boot with Sun Solaris 10 and also with Windows 2000.
I am getting 1440x900 in both of them.
Infact the screen output is seamless at this resolution, I suspect it was built for this resolution only (1440x900).

---

