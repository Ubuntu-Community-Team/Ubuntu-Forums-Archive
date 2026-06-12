---
title: "audacity help"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by captain haddock on 2007-05-15
I can record with it fine but the sound quality is bad.It sound like its coming through a tin can:(

---

### Post by josesanders on 2007-05-17
There are a number of things that could be the problem.  Are you sure that the problem is just with Audacity?  Poor sound quality is much more likely the result of bad drivers, a bad input connection or some other system-wide problem.  I recommend you try recording with a simple program like Ubuntu sound recorder:
[http://packages.ubuntulinux.org/dapper/sound/sound-recorder](http://packages.ubuntulinux.org/dapper/sound/sound-recorder)
If you have the same sound quality problem there, then you know it isn't just Audacity.

---

### Post by jackread on 2008-01-24
hey I have a similar problem...

audacity would record fine "out of the box", except for when it came to recording more than one track. I guess thats a problem with OSS drivers. I installed a beta version of audacity and compiled it using this command

```
./configure --with-portaudio=v19 --without-portmixer --program-suffix=beta && make
```

and when i run the command audacitybeta it now records and plays great.... 

except for the fact I get this high pitch background noise! 

I tried running "aoss audacitybeta" and it records without the background noise but then it just crashes when try to record  second track! any ideas?

---

### Post by josesanders on 2008-01-28
I haven't found a universal solution, but I know that a solution should exist, as I didn't have the problem using ALSA.  I did some searching, and all I've found so far is this:
[http://ubuntuforums.org/archive/index.php/t-368904.html](http://ubuntuforums.org/archive/index.php/t-368904.html)
[http://audacityteam.org/forum/viewtopic.php?f=18&t=1706](http://audacityteam.org/forum/viewtopic.php?f=18&t=1706)

Assuming that you've already seen those pages and had no success, I recommend you check your sampling rate.  Make sure that you are recording at a sampling rate that is supported by your sound card.  Maybe experiment with a few different ones.

If that doesn't work, and this is totally the wrong way to try to solve the problem, but if nothing else works and you are out of options, you could just try using a notch or low-pass filter to get rid of the sound.  It will only work well if the sound is higher in frequency than what you are trying to record.  See:
[http://dyork.livejournal.com/235522.html](http://dyork.livejournal.com/235522.html)

If you do find a solution, make sure you post it, as I don't think that anyone else has really posted a definitive solution.

---

