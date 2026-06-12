---
title: "No sound in tvtime with AverMedia m150d"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by orion2087 on 2007-09-23
I know there are a lot of threads about this but I just can't get it working in TvTime or MythTV. I've unmuted and maxed out everything in my volume control, and when I tried the sox trick I get this response:

```
corey@HP-linux:~$ arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | sox -q -c 2 -r 32000 -w -t wav - -t alsa hw:0,0
Recording WAVE 'stdin' : Signed 16 bit Little Endian, Rate 32000 Hz, Stereo
Warning: rate is not accurate (requested = 32000Hz, got = 48000Hz)
         please, try the plug plugin 
sox: Failed writing hw:0,0: cannot open audio device

```

I'm using 7.04 x64 and an AverMedia m150d / 1500 MCE. My card also doesn't seem to have any audio out jacks on it. It does have an RCA audio set, but I think its for input. Help! :)

---

### Post by orion2087 on 2007-10-29
An update on this, I've done a fresh 7.10 install and tvtime has the same problem off the bat. 

Does no audio out on tuner = fail?

---

