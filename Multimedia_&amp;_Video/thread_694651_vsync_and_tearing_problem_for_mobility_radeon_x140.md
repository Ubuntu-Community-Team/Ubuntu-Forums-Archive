---
title: "vsync and tearing problem for mobility radeon x1400 on dell 6400"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by spandanj on 2008-02-12
Hi, 

There is an incredible amount of vsync/tearing going on when i watch videos on ubuntu - to the extent that it makes the movie unwatchable....

on my laptop, compiz works - everything works - except this tearing/vsync in video playback on all players including vlc, totem-xine, and mplayer.

can someone please give a solution (if there is one) to removing the video tearing...BTW i am using watever restricted video driver that ubuntu installed - I dare NOT install new drivers from ATI on my own. and I suppose that ubuntu would update the drivers for new ones when they come out, right?

-spandan

---

### Post by spandanj on 2008-02-13
why won't anybody post  solution to this????


somebody - help me. i really wanna watch that movie. before the end of this decade.

-spandan

---

### Post by zapho on 2008-02-14
I'm having the same problem. 
I've an inspiron 6400 with an x1400 ati card. I've just installed Gutsy. 

The ATI drivers are working fine (no need for xgl!) and even multiple monitors is working (although I haven't tried the TV out yet).

I get tearing on video play back too, on both XV and opengl rendering (using VLC). Infact,XV is completely unwatchable. Opengl is far better but there's still tearing. 

I haven't gotten around to reinstalling the ati drivers myself, planning on that later. 
I think it might have something to do with the monitor refresh rates.

---

### Post by spandanj on 2008-02-15
Yes, 

I agree. it has something to do with refresh rate of monitor vs. video playback - and that is what i keep reading - howwever, no solution. i am not an expert myself. so, i ll have to wait this out....until SOLVED (WHENNNNN????)

i get 720p to enjoy the video - but, what's the point - it tears...

Linux community please respond...help.

don't make me buy a mac....

-spandan

---

### Post by disturbedite on 2008-02-15
well, this is a bit unrelated, but a bit relevant too.

i know that in games one should not use vsync unless it is really necessary, as it usually slows down the game.

don't know if this helps any, but just thought i'd throw my hat in here...

---

### Post by Insane1 on 2008-02-15
Actually, from what I know, the restricted drivers are using some pretty old drivers. If you want the latest I believe Envy is a good choice to use to install them (Quite easy to use). However my ATI x1400 gets this video tearing regardless of driver. At least when compiz is on...Try watching the videos with Compiz off. X11 video output (Easiest to set in VLC) should work fine with Compiz on, but it won't fullscreen as nicely as something like OpenGL (in my personal opinion).

This is the only fix I've managed to find in my search.

---

