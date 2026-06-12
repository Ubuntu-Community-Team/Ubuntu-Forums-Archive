---
title: "How to set 32-bit color depth?"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by Kobin on 2007-03-14
I installed Ubuntu 2 weeks ago as my first linux-dist...
I like using it so far but I am running in to this problem now:

I want to use a program that requires 32-bit color depth but I can't find a menu or anything where it is possible to choose this.
I also googled a lot on this but found no advice I could use...

Hope someone in here has a solution or idea..

---

### Post by Dr. Nick on 2007-03-15
What program specifies 32bit color?

To set the color mode edit this file as sudo

/etc/X11/xorg.conf

go to Section "Screen" and set DefaultDepth to 24

For some reason linux uses 24 instead of 32, i think 24 is the highest it'll go

look here [http://www.linuxforums.org/forum/linux-newbie/9949-how-enable-32-bit-color-mode-running-1152x864-pixels.html](http://www.linuxforums.org/forum/linux-newbie/9949-how-enable-32-bit-color-mode-running-1152x864-pixels.html)

though it looks like you ended up where they are, I dont know what to do about progs requiring 32 bit since ive never seen one

---

