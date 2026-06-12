---
title: "Monitor timing issue?"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by gibsonc on 2008-02-03
Hi all

I have just installed 7.10 on a G33 based motherboard with onboard VGA - I believe the chipset is therefore a X3100. The monitor is a 22" WXGA LG L222W. I have applied all current updates.
Everything works fine:

intel driver
1680x1050@60/75Hz @ 16M

However, the left side of the screen is chopped off - that is, if you move the mouse left, it disappears. The other three sides are constrained correctly. No amount of twidling of the monitor can fix it. Moving the mouse off screen results in 'ghosting' on the LCD.

I have added modelines using both the cvt and gtf tools (which respond with differing values) for both 60 and 70Hz refresh rates. No difference is experienced.

Is there something else I am missing?

Kind Regards
Craig

---

### Post by gibsonc on 2008-02-03
Update: No amount of twiddling the modelines works, however running grandr (xrandr) and choosing the 60Hz refresh rate option fixes the problem immediately. When starting grandr however, it always says the current refresh rate is 59.9 even though the modelines are built based on a 60Hz refresh rate!

Oh well....quick fix, run xrandr on startup or something crude like that....

---

