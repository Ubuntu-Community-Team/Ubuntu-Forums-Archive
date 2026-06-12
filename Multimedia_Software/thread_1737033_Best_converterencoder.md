---
title: "Best converter/encoder?"
date: 2011-04-22
forum: Multimedia Software
---

### Post by abeam on 2011-04-22
I'm looking for something like the Windows program, SUPER; so essentially I want something that will do everything from .mp3 to .mkv. Any suggestions?

---

### Post by surfmonkee on 2011-04-23
i had the same issue when i switched to ubuntu.

i was determined to get my head around the best encoder on the planet (imo)

**[COLOR="Blue"]ffmpeg [/COLOR]**

 its genius.  there is a graphical user interface for it too but i wanted to begin learning command line coding so i built my own by following this tutorial.

[http://pasindudps.blogspot.com/2010/12/compiling-ffmpeg-in-ubuntu-1010.html](http://pasindudps.blogspot.com/2010/12/compiling-ffmpeg-in-ubuntu-1010.html)

there is also a front end available in the software center called winFF

google will be your friend, there are a zillion tutorials available.

i am a relative n00b so to begin with it was a bit of a nightmare but now i can churn out content for my psp in seconds!

---

### Post by shantiq on 2011-04-23
Was a big fan of super too  :KS:KS

**soundconverter and soundkonverter** are both very good and in your synaptic they will converter from video to audio and from audio to audio soundkonverter is the best of the two closest to super

=================================

also if command line is cool with you you could try [this way]("http://ubuntuforums.org/showthread.php?t=1609760")   cd to the directory where your files are first

and modify as you go along

you mention mkv    an example would be for flv

```
for f in *.flv; do ffmpeg -i "$f" -ab 128k "${f%.flv}.mp3"; done 
```


then for mkv

```
for f in *.[COLOR="Red"]mkv[/COLOR]; do ffmpeg -i "$f" -ab 128k "${f%.[COLOR="Red"]mkv[/COLOR]}.mp3"; done 
```

---

