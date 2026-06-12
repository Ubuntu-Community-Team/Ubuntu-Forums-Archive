---
title: "Strange oddity when using projector"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by mbobak on 2007-01-17
I wonder if anyone can help.  I have a Ferrari 1000 laptop, running Ubuntu 6.10.

I've got every multimedia codec under the sun installed and working.  (Thanks, Automatix!)

So, I can watch videos, play DVDs, even encrypted ones, etc.  No problem.

So, I plug my VGA out into my BENQ PB8230 projector, and, voila!, no problem, I see my display on the projector, no problem.

But, when I try to play a video image, I can see the video display on my laptop screen, but on the projector, it's blank.  To be clear, on the projected image, I can see my desktop, menus, background, etc.  Everything works.  When I start totem (or mplayer), and try to watch a dvd or mpg, or avi, etc, it plays fine looking at my laptop screen.  When I look at the projected image, though, I see all my menus, backgrounds, programs, etc, but my video player's window, where the movie is displayed, I see a blank black box.  This is really weird.  I can see playback on the laptop screen, but not the projected image!

Further, if I open a web browser, and go to YouTube, I can see videos there, and they come up just fine on both the laptop screen and the projected image.  But, anything played via mplayer or totem, or vlc for that matter, fails to display on the projector.

This makes no sense to me.  The VGA out is somehow different from the laptop's LCD?

Anyone seen this behavior before?  Any clues on how to fix it?

-Mark

---

### Post by mbobak on 2007-01-17
Bump.....?

---

### Post by mbobak on 2007-01-18
FYI:

I posted similar question in AVSForum.com on the HTPC - Linux chat forum, and got an answer there.

Using the XVideo overlay extension seems to work only with the primary display, i.e., the laptop screen.  Switching to X11 (using mplayer -vo x11) solved the problem.

-Mark

---

