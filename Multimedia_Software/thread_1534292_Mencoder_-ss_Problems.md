---
title: "Mencoder -ss Problems"
date: 2010-07-19
forum: Multimedia Software
---

### Post by Kale Good on 2010-07-19
I'm trying to cut video using this command: 
mencoder -ss 43 -endpos 120 -oac copy -ovc copy beginner1.avi -o part2.avi 

The problem is this: I enter -ss 43 but it actually starts at 47. It  does start any earlier than 47 until I reduce the entry time to -ss 38.  The same problem exists for times after 47. 

-endpos will correctly end in this same ranges (i.e. it will end at 39,  40, 41 etc. when commanded to). 

Possibly useful info: 
Video was made using webcam and this command (basically): 
mencoder tv:// -tv  driver=v4l2:width=320:height=240:device=/dev/video0:forceaudio:adevice=/dev/dsp1  -ovc lavc -oac mp3lame -lameopts cbr:br=64:mode=3 -o webcam.avi 


Thanks, 
Kale

---

### Post by aeiah on 2010-07-19
[looks like a keyframe issue](http://en.wikibooks.org/wiki/Mplayer#Split.2Fsub-section_videos). mencoder probably (at least by default) goes to the nearest keyframe, which happens to be at 47s. perhaps you can make mencoder rebuild keyframes and split things exactly or perhaps you'll have to re-encode (and pipe) the video with a keyframe every second into your mencoder splitting command

---

