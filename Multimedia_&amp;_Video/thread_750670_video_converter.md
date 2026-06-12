---
title: "video converter"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by evil107 on 2008-04-09
I've been trying  to convert a couple of  wmvs to mp4s so they work on my psp but whenever I fiind one  that supposedly works (I guess i'm just a little slow on the uptake) the converter that  I have that supposedly works is avidemux but I can't seem to get it to convert,  can someone tell me how to do it as simple as they can?

---

### Post by zombie-si on 2008-04-10
I found this in a Fedora Forum, you have to have Mplayer or mencoder installed I believe. Then type this in a terminal with your file names.

```
mencoder -vf pp=md,scale=368:-10,crop=368:208,expand=368:208,pullup,softskip,har ddup -lavdopts -ovc lavc -oac lavc -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:acodec=libfaac -af volnorm=1:lavcresample=24000 -ofps 30000/1001 -of lavf -lavfopts format=psp -o <your_new_file.mp4> <file_you_want_to_convert.wmv>
```

I haven't tried it myself but it might be worth a shot...

---

### Post by ubuntu-freak on 2008-04-10
Have you installed faac? Check out part 1 and 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and you should be fine. Install the older/stable version of WinFF though, as the new one needs to be rewritten for Gutsy/Hardy.
 
Nathan

---

