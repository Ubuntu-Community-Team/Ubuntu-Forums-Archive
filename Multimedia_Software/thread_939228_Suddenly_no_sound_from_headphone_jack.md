---
title: "Suddenly no sound from headphone jack"
date: 2008-10-05
forum: Multimedia Software
---

### Post by liquistin on 2008-10-05
[SOLVED]

I installed Ubuntu a few days ago and everything has been working great.

Yesterday I installed mpd and got it working, but after this there was no sound from the headphone jack.
When I open 'alsamixer' the headphone channel exist, but it's impossible to set it to anything.
After browsing some forums I tried to add:
> options snd-hda-intel model=3stack
options snd-hda-intel model=auto position_fix=1 enable=yes
into the alsa-base file, but it's still not working.

I've browsed different forums, but can't find any solution to my problem.
I found some treads about missing the sound from the headphone jack, but those treads didn't help me with my problem. Possibly just incompetence, but anyway..

Soundcard:HDA nvidia, realtek alc861-vd..
I got the 1.0.0.16 version of alsa.. can somebody help me with this. My experience with linux is limited..

---

### Post by markbuntu on 2008-10-06
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

