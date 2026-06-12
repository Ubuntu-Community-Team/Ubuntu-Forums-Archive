---
title: "sound issue in hp pavillion tx2000z running intrepid"
date: 2008-12-05
forum: Multimedia Software
---

### Post by Sarai the Geek on 2008-12-05
Hi all-
I have an hp pavillion tx2000z tablet convertible that dual boots ubuntu and vista (installed using WUBI). It is capable of making beep noises, but that seems to be about it.
I spent some time in #Ubuntu and the general consensus was that it was probably a problem with my pulse audio but no one was sure how to fix it. So far I've done the following things unsuccessfully:
1.) changed the device in the audio mixer, tested each one and finally returned it to ALSA.
2.) installed the patch to make pulse audio work with flash in firefox
3.) installed the "restricted ubuntu extras" package through the synaptic package manager.

Still, all I get is beeps. Any suggestions? I'm a bit of a linux n00b so use small words, please! ;)

---

### Post by Sarai the Geek on 2008-12-05
Oh, I also have tried disabling (not uninstalling) pulseaudio as described here: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) .

---

### Post by Sarai the Geek on 2008-12-05
*bump*

---

### Post by kqian on 2008-12-11
[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

I would check that out. I have a tx2000z, and that page got mine working. Now everything except the headphones is producing sound. 

p.s. If you ever get your headphones working can you let me know? ;-)

---

### Post by Sarai the Geek on 2008-12-13
Hmm...
Well, after some guidance from a nice guy in #Ubuntu I did get my sound working- but like you no sound to the headphones. I'm somewhat disappointed to hear that you haven't had any luck with it either. I'll keep plugging, and let you know if I ever come up with anything.

---

### Post by Sarai the Geek on 2009-03-18
I can't figure out how to mark this thread solved, but I finally did get my headsets working.

To my "/etc/modprobe.d/alsa-base" file I added at the bottom: 
```
options snd-hda-intel model=hp
```

After a restart the headsets were working perfectly!
In System>Preferences>Sound, all the boxes are set to ALSA and the default mixer track is HDA Nividia. Make sure (via the volume control preferences) that the headphone channel is on since I think it's muted by default.
And that's it!

I had rather forgotten what it was like to enjoy my music, movies, etc without sharing it with the world. ;)

---

