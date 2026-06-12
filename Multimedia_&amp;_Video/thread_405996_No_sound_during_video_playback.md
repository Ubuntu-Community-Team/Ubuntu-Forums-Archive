---
title: "No sound during video playback"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by the_stranger on 2007-04-10
When I installed Ubuntu I had no sound at all. After some tinkering around I realized that if I go to System >> Preferences >> Sound and then change all the options from Autodetect to NVidia nForce2 - IEC958 then I was able to hear the test sounds. I thought I was done and I was relieved when I was finally able to hear audio during music playback. However, it wasn't long before I realized that video playback was still muted. Playback of oggs or mp3s is fine, but I do not get any sound during any sort of video. This includes video clips I downloaded from various websites and even embedded stuff such as YouTube. Actually audio doesn't work at all in any browser. Websites that I know have sound playing in the background come off completely silent. 

I have Ubuntu installed on an old laptop I have and everything works fine there. I installed the exact same packages on both systems so I'm pretty sure the problems on my desktop aren't codec issues. 

If anyone knows what the root of the problem is I'd appreciate the help in figuring this thing out. And if not can anyone recommend a cheap sound card that is guaranteed to work under linux?

---

### Post by the_stranger on 2007-04-10
bump

---

### Post by the_stranger on 2007-04-14
Anybody? Anybody at all?

---

### Post by anthonyesau on 2007-04-14
I have a similar problem posted [**here**]("http://ubuntuforums.org/showthread.php?t=408914").  In Synaptic Package Manager find whether you have libsdl1.2debian-all, libsdl1.2debian-alsa, libsdl1.2debian-oss, or something similar and try installing one of the others.  For example: if you had libsdl1.2debian-alsa try installing libsdl1.2debian-all.  Then restart the computer and see if you get any sound.  This worked for a little while for me.  Good luck.

---

