---
title: "x264 stuttering"
date: 2008-06-11
forum: Multimedia Software
---

### Post by mailbox on 2008-06-11
First, a little background to help explain the prolem:
I got a bunch of DVDs for my birthday, and I'd like to rip them to my computer so that I don't have to switch out discs every time I want to watch a movie.
Originally, I used *vobcopy -l* to rip them as single .vob files, but each one is somwhere between 4 and 7 gigs, not to mention *Return of the King*, which clocks in at just over 13 gigs, once I cat'ed the two halves togetcher.
I began to use the script below (figure one, taken from [http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)) to convert them in to x264 + ogg inside a mkv, and it worked fine for *12 Monkeys*, *28 Days Later* and *Shaun of the Dead*, but *28 Weeks Later* is giving me severe problems: the output looks as if it is stuttering.
It's not lagging, as if my machine were too slow to play it, but it seems as if it is outputting frames in a pattern like *3 1 2 6 4 5 9 7 8* or *4 1 2 3 8 5 6 7*. The video seems to be moving backwards and forwards very quickly, but still goes more forward than backwards.
I would upload a small sample, but when I tried to use avidemux to clip it, I got the following (attached) result.

I'm stumped here, and would appreciate any help you could give me.



Figure One (just the video conversion, audio isn't giving me a problem):```
# first pass
mencoder -v\
         title.vob\
        -vf crop=716:448:2:18,harddup\
        -ovc x264 -x264encopts subq=5:frameref=5:me=umh:8x8dct:partitions=all:bframes=3:b_adapt:b_pyramid:weight_b:threads=2:pass=1:psnr:bitrate=1200\
        -oac copy\
        -of rawvideo\
        -o title.264

# Backup in case something goes wrong
cp title.264 title.firstpass.264

# Second pass
mencoder -v\
         title.vob\
        -vf crop=716:448:2:18,harddup\
        -ovc x264 -x264encopts subq=7:frameref=8:me=umh:8x8dct:partitions=all:bframes=3:b_pyramid:threads=2:pass=2:psnr:bitrate=1200\
        -oac copy\
        -of rawvideo\
        -o title.264
```

---

### Post by mailbox on 2008-06-11
If it helps (and even if not; I'm going to tell you anyway), I'm running this on two cores, and have already tried to use threads=1 for only one core, but the same exact problem occurs.

I have just noticed the same problem with *Dancer in the Dark*, which appears to be interlaced, while *28 Weeks* does not.

---

