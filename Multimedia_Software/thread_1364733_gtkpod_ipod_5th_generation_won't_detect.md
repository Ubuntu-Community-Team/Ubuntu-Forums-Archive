---
title: "gtkpod ipod 5th generation won't detect"
date: 2009-12-26
forum: Multimedia Software
---

### Post by GeeK_KolA on 2009-12-26
Hello! I have a small problem lately that I can't seem to overcome so I've been looking through the forums...can't seem to find a solution for me, so im posting this. Anyway, I've been using my iPod with Amarok for while to for music. Well, I've been importing my DVDs with Handbrake to put movies on my iPod as well. I recently downloaded gtkpod, and so far my ipod has been detected by it only once, and I was able to put one movie on my ipod. Well I imported some more movies...and went to load my ipod in gtkpod...it doesn't recognize it now. Does anyone have an idea why it would do work only once and not anymore? Everything else works just fine still, my amarok works fine. I just can't seem to figure this one out. Thanks!

And excuse my horrid spelling and what not....im out of coffee and i don't normally use forums O.o

---

### Post by bowens44 on 2009-12-26
This is kind of a clunky solution but it works for me....

1. with the ipod not plugged into the PC go to a terminal and issue the following command:

 killall -9 nautilus

then plugin the ipod, wait about 60 seconds, hit Alt F2, type in 'nautilus' without the quotes, click on run. after this, launch the app that you want to have accessing your IPod. It should see it now.

got this info from here:
[http://luisgmarine.blogspot.com/2009/12/fix-ipod-detection-in-ubuntu-910.html](http://luisgmarine.blogspot.com/2009/12/fix-ipod-detection-in-ubuntu-910.html)

---

### Post by GeeK_KolA on 2009-12-28
Thanks for the input dude...but I figured out my problem. Genius that I am didn't realize that the directory I assigned to my iPod was in lower case and my iPod's name is all CAPS. <.< ...he...he he...*pats self on back* lmao. But now I have a new problem...some of the videos that I ripped from my DVDs (mainly the widescreen DVDs) don't fit properly on my iPod's screen. About 20% is cut off from each side. I guess I gotta do even more research O.o......blah. But again, thanks dude.

---

