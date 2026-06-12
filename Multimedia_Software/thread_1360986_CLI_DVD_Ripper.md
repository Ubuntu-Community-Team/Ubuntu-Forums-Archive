---
title: "CLI DVD Ripper?"
date: 2009-12-21
forum: Multimedia Software
---

### Post by clancymf on 2009-12-21
I have been using handbrakecli for quite some time now and have written a small script so that when i insert a disc it as for the title and then does its thing.

However lately the movie chapaters have been out of order.  I was hoping to find a command line tool to decrypt and then use handbrake to encode.  

Any ideas?

Thanks

---

### Post by JohnAStebbins on 2009-12-22
Out of order chapters is pretty much always a result of picking the wrong title to encode.  Newer discs have been adding lots of dummy titles that are the same length as the real title.  You have to figure out which is the real title and tell handbrake.

You can find this by playing the dvd in vlc, selecting the "play" option in the dvd menu. then, after the main feature starts playing, look at vlc's navigation menus to see what title actually is playing.

---

### Post by clancymf on 2009-12-23
Wow, didnt know.. Thanks for the tip and saving me the headache of trying a whole new mess of tools!

---

### Post by SuperSonic4 on 2009-12-23
You may also get away with specify the longest title with -L

---

### Post by clancymf on 2009-12-23
Yeah thats what I have it set for and Im thinking that the dummy titles are just slightly longer.

---

