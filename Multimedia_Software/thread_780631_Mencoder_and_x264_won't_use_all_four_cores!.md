---
title: "Mencoder and x264 won't use all four cores!"
date: 2008-05-03
forum: Multimedia Software
---

### Post by ASULutzy on 2008-05-03
I'm ripping a DVD, and I can get mencoder to use 1 or 2 cores, but it won't take advantage of all 4!

If I don't give it a threads= it rips at about 45 fps. If I give it threads=4, or threads=8, or threads=auto it rips at around 80 fps (Should be doing about .9 * 45*4) top also shows me only getting to 200% CPU usage, not 400%. And system monitor never shows all 4 cores anywhere near 100%.

Please help! Have an Intel Quad Core Q600
```
mencoder -v\
         title1.vob\
        -alang en\
        -vf crop=720:352:0:66\
        -ovc x264 -x264encopts threads=auto:subq=4:bframes=4:b_pyramid:weight_b:pass=1:psnr:bitrate=1400:turbo=1\
        -oac copy\
        -ofps 24000/1001\
        -vobsubout subtitles -vobsuboutindex 0 -slang en\
        -o /dev/null

``` was the command I used to rip (after dumping the vob to hard drive)

---

### Post by disturbedite on 2008-05-03
i think one has to specify/enable 4 core support when compiling mencoder.

---

### Post by ASULutzy on 2008-05-03
That's weird... I guess I'll go grab the source then

edit: Anyone know a guide on how exactly to specify using 4 cores during compilation?

---

