---
title: "Do ALL video players in linux suck?!"
date: 2009-03-23
forum: Multimedia Software
---

### Post by higashi on 2009-03-23
I'm trying to enjoy watching some videos on Miro TV . Unfortunately, (like all the other things i watch videos with such as Totem or Mplayer) , the program is extremely annoying.

whenever i move the window, the screen goes blank. i have to slightly move it a few times to get the picture back.
If something's going on in the background, it makes shapes that seem to go through the video and make certain areas blank.
If i drag a window over the video at any point, that part of the video will go blank.

Is there any way that i can fix this? Any way that i can just make my videos play with no blank-ness regardless of what's going on around them?!

---

### Post by Chemical Imbalance on 2009-03-23
try turning of Compiz to see if it fixes it,

especially if you have an intel chipset


Compiz can be very buggy in relation to playing videos and games

There are fixes and workarounds but first see if turning it off helps.

---

### Post by higashi on 2009-03-23
Yes, turning it off did help. However, I'd really rather have compiz on (having it off makes things seem slower and a lot more boring).
So, can you please tell me about these fixes and workarounds you mentioned?
Thanks.

---

### Post by Xiong Chiamiov on 2009-03-23
Although you may be frustrated, your thread title is pretty unhelpful (although I've seen worse), not to mention it indicates a question other than the one you really want answered.  You should also take into consideration the fact that insulting open-source software on a linux forum is not generally a good way to endear yourself with the locals.

---

### Post by the_hardy_kid on 2009-03-23
I had the same problem as you.
Go to terminal and type ```
gstreamer-properties
```
then go to the Video tab and change Plugin to X Window System (No Xv)

Then open a video with gstreamer, and see if it works. Did for me

---

### Post by higashi on 2009-03-23
That worked great! Thanks :D

---

### Post by inobe on 2009-03-23
:lol:

glad you got rid of the infamous black screen

---

