---
title: "Dvi &gt; Vga"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by bestial on 2006-09-29
Yesterday I bought myself a DVI to VGA-cable for my newly invested HD-tv. I were under the influence that this cable only should be put in to the DVI-output on my videocard then into the TV, but no! The cable shows the bootup on my tv, but as soon as it turns into the username/password-screen in Gnome the tv turns blank, no picture.

I've tried to lower my resolution to 640x480 but that didn't work either, to that I probably should add that I where on 75hz, cause Ubuntu wouldn't let me to lower it to 60hz.

My computer-screen (a Sony LCD-monitor) is plugged into the VGA-port and works just fine, so my question is, do I need to add the DVI-port to xorg or is it just a resolutionproblem?

I hope you guys understand what I'm saying. :)

---

### Post by pseudonym on 2006-09-29
Do you have an nvidia video card? You need to edit xorg.conf to use the tv-out. the ubuntu howto is [here]("http://www.ubuntuforums.org/showthread.php?t=98456&highlight=tv-out").

---

### Post by bestial on 2006-09-29
Yeah, I got a nVidia-card, but actually, DVI > VGA shouldn't really counts as "tv-out" right, cause if I want to use my HD-tv as a second screen with a DVI-cable shouldn't it just.. work? ;D

---

### Post by pseudonym on 2006-09-29
Oops! yes, of course. it's [dual monitors]("http://www.ubuntuforums.org/showthread.php?t=240150&highlight=monitors") you want, not tv-out :)

---

### Post by Izuil on 2006-09-29
Add```
Option "UseDisplayDevice" "DFP"
``` in xorg.conf

EDIT: or this might not help at all... when it goes black try ctrl+alt+backspace.

If it doesn't help then you might need to replace DFP with something else not sure what though...

---

### Post by bestial on 2006-10-01
Where should I put that line? 

Cause adding just one line and make it work suits me better then _a lot_ of lines to get a dual screen. :D

And about that, I don't really need dual screen literally, it works just fine with a clone.

---

