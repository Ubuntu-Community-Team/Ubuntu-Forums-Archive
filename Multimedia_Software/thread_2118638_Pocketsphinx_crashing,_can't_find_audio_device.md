---
title: "Pocketsphinx crashing, can't find audio device"
date: 2013-02-21
forum: Multimedia Software
---

### Post by Robing Goodfellow on 2013-02-21
I've tried to get help for this over in the CMU pocketsphinx forums to no avail.

I'm running a fresh install of Precise on a 64 bit HP G62 laptop. I had pocketsphinx running on the previous installation of Precise. Now, under the new install, every time I launch pocketshpinx, it crashes. Here's the error message:

FATAL_ERROR: "continuous.c", line 246: Failed to open audio device

I'm running on a plug mic, nothing fancy, and I know it's working, if I go into sound input I can see the levels change when I speak into the mic.

I have searched the forums and the web and tried numerous solutions such as install oss_compat among other things. This I did, no joy, Nikolay (CMU support guru) said, when I told him I had installed oss_compat: "Beside installing the package you need to probe the kernel module to create the device"

He could be right. He's a pretty smart if rarely clear and helpful guy. I'll admit it, I've only been using Linux for 2 years now and I have no idea how to probe the kernel. Can I get some guidance?

I already read and did everything in the (outdated) pocketsphinx FAQ, so if this doesn't fix it, I'm in a bind. Any ideas? 

The thing that kills me is it functioned (as opposed to worked well, speech rec is a bytch) on the previous install. Now, not so much pretty good.

regards, Richard

---

### Post by Robing Goodfellow on 2013-02-22
Got some help over on the cmusphinx freenode irc and resolved it. Here's the fix:

installed pulseaudio:
```
sudo apt-get install libpulse-dev
```

then reinstalled sphinxbase:
```
cd sphinxbase
./configure
make clean all
sudo make install
```

and it now works.

regrads, Richard

---

### Post by aseemb on 2013-06-01
Thanks for sharing Richard! That solved the problem for me too (on 12.04).

---

### Post by imohindra on 2013-06-05
I need help with the pocketsphinx application.

I am using the 12.04 version and have been trying to make pocketsphinx work for nearly 10 hours now..
I have tries all possible operations. I have no oss modules loaded 
I have tesed my mic and speakers and all work fine. 
I have a "Correct" formatted audio file that I used, its basically the one that comes withthe package that is /test/data/cards/001.wav.

I have installed libpulse-dev as well ...I am trying to run the pocketsphinx with the following:

1) padsp pocketsphinx_continuous

ERROR: It says audio device not found

2) padsp pocketsphinx_continuous -infile /pocketsphinx-0.8/test/data/cards/001.wav
ERROR: Failed to calibrate voice activity detection

[I have installed all required alsa-oss wrapper plugins too but no respite.]
3) aoss pocketsphinx_continuous
ERROR: Failed to calibrate voice activity detection.

4)aoss pocketsphinx_continuous -infile /pocketsphinx-0.8/test/data/cards/001.wav
ERROR: Failed to calibrate voice activity detection.

I am in real need of help with this.
Please help me with this position. I seem to be stuck. And stuck bad!!!

---

