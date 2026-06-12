---
title: "fixing overscan/cropping on plasma TV"
date: 2011-11-07
forum: Multimedia Software
---

### Post by mjlush on 2011-11-07
I just picked up a D2 Plug server (with Ubuntu loaded) and tried to use it with my plasma TV
everything worked fine however the edges of the GUI were cropped off screen 

First I had a poke round the TV options to re-centre display
then I hunted through the net to 

a) find out what the problem was called (overscan)
b) find out what xorg.conf / xrandr settings I needed to fix it 

I eventually stumbled on a hint it may be the TV after all and had another look 

on my Panasonic P42G-10B 

It was Menu -> Other Settings -> Picture Overscan (Off)

Hope this helps!

--
Michael Lush
NPC Rights activist | Nameless Abominations are people Too!

---

### Post by voicesinthefan on 2011-11-11
Helped me!  Kind of, I have a Sony Bravia LCD and this post made me go look around my TV for some more options.  I just started using my ubuntu laptop to output video to my TV.  I did remember adjusting overscan on my windows PC with nvidia card output, so began looking how to do this on ubuntu.  

"Settings" -> "Screen" -> "Display Area"

And found a setting that no longer cropped my laptop screen.

---

