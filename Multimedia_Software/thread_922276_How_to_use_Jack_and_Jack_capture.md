---
title: "How to use Jack and Jack_capture"
date: 2008-09-17
forum: Multimedia Software
---

### Post by nadi001 on 2008-09-17
my aim is simple: Just play a mp3 file using Mplayer, and want to use Jack and Jack_capture to record the sound that I have heard in my speaker. I know this must can be done by using Jack and Jack_capture, but I really have no idea about how to use them tegother. I have done as the "man jackd" said: 

#jackd -d alsa -C hw:0,0

but "**** alsa_pcm: xrun of at least" will be given.
sometimes when I try some other parameters(I'm really crazy with the parameters!), mplayer can not be used, said sound card is busy.

I think the port must be set, but I don't know how to do that even after googled much.

help me,please!

---

### Post by markbuntu on 2008-09-17
The alsa-jack sink does not work for many applications but the pulseaudio-jack sink will work with almost all applications and allow you to record anything playing in your speakers through jack. You can follow my guide here if you want to give it a try:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Even if you do not want to try it, there are links in the jack section that may help with your problems.

---

