---
title: "Flashing line at the bottom of my screen"
date: 2009-06-27
forum: Mythbuntu
---

### Post by jonno on 2009-06-27
Not even sure how to search for this one.

I'm running Mythbuntu 9.04 on an AMD64 system with on-board Nvidia 6150 graphics using the Nvidia drivers (currently v.180.44. My tv is a CRT so the resolution is not great.

I'm having issues with a line of black/white stripes along the bottom of my screen.
If I run at 1024x768 then the line is always there (on the desktop and in Mythv and Boxee). Overscan settings make no difference. If I use the Nvidia settings manager to change to 800x600 then it disappears for the duration of my session but when I reboot it reappears. If I go into the Nvidia setup and switch from 800x600 to something else and back it goes away again.
I could live with resetting this when I reboot which isn't very often but in Boxee the line is there all the time (even 800x600) and when doing something like changing menus or playing video it starts flashing which is really annoying.

Does anyone have any idea what is causing this or how to get rid of it? I've tried messing with the video overscan settings in the Nvidia settings and in Boxee.

---

### Post by tallac on 2010-04-22
I am having the same issue.  Any solutions?

---

### Post by jbman on 2010-04-22
I have been seeing it as well. I am using a onboard 8200 with VDPAU and the slim setting. I thought it must have been BOB X2 doing it.

---

### Post by Lepy on 2010-04-22
I have a machine with an 8200 that has never experienced a flashing line problem. It did have a problem with little white dots that would clutter the screen at times, but this was the result of a suboptimal resolution.

Any errors or warning in your /var/log/Xorg.0.log?

---

