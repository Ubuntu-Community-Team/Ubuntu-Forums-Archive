---
title: "ATI x1600 refresh issue"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by skerg on 2006-06-10
Hello, I just recently installed Ubuntu and got it running without any problems, it was a little sluggish (graphic wise) so I installed the latest ATI drivers, rebooted and everything seemed fine until I moved or tried to resize a window.

This is hard to describe but the best example of the problem is when I was using firefox and tried to scroll down, only the bottom three lines would change and the bulk of the window stayed the same. However if I pressed ctrl A to select everything it would refresh and I could see where I scrolled.

Another example is when I moved a terminal over it would start cutting the window (e.g.: making the window smaller but not repainting it so the part of the window I refreshed wouldnt be visible), but I could fix it by double clicking on the terminal to make it full screen, and then double clicking again to size it down.

Any idea what's causing the refresh problems? Thanks a bunch.

---

### Post by Daniel of Sweden on 2007-01-26
Well, i don't know but i've had the same problem :( I've read some threads that say that downgrading the drivers will help solve the problem but i haven't managed to get it right :(

---

### Post by hereitcomes on 2007-01-27
i had this problem with my x1600, mine is agp for reference, 512mb memory

the solution was to change the agp aperture size in the bios to 128MB

check your motherboard manual if youre not sure how to do this, and if the option isnt there, check for a bios updat

EDIT : 
This was the post i found with the excellent help
[http://ubuntuforums.org/showthread.php?t=339316&highlight=x1600](http://ubuntuforums.org/showthread.php?t=339316&highlight=x1600)

---

