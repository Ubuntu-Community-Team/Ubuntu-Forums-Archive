---
title: "Fullscreen 'out of range' error"
date: 2008-08-05
forum: Multimedia Software
---

### Post by davosmith on 2008-08-05
My desktop loads up fine, but whenever I try to launch a fullscreen game, my LCD monitor complains that the refresh rate is out of range.

This occurs with games using SDL and with DirectX games running under Wine.

My xorg.conf file was hand-crafted by me (to get my TV-out working correctly) and I have hard-coded into it the refresh rates that my monitor is capable of (straight from the manual), but the refresh rates that these games are attempting to use are outside the limits I have specified.

Any ideas? Is there any way to tell SDL/Wine+DirectX what refresh rates they are allowed to use?

If it helps, my video card is an NVidia FX5200 and my monitor an Iiyama ProLite E435S

---

### Post by akvilio on 2010-05-09
Actually i have the same problem.
I'm using ubuntu 10 and i tried, just for fun, installing Rise Of The Triad and Free Doom, but i get the same error when the fullscreen mode kicks in.
I recall that i had the same thing on Windows XP. 
The solution was to get into the files of the game (It was Quake 2 or 1)
and set the game so it will start in windowed mode, then of course it can be changed to fullscreen with lower resolution.
I wonder if there a method here too.

---

### Post by davosmith on 2010-05-09
I did eventually solve this properly (I can't remember who helped me out), you need to edit xorg.conf, find the 'modes' line and change the resolution that is causing problems from (for example) '800x600' to '800x600_60' (where the '_60' is the refresh rate to run at - in this case 60Hz).

Hope this helps someone else out there.

---

