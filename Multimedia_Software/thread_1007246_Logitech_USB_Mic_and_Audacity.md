---
title: "Logitech USB Mic and Audacity?"
date: 2008-12-10
forum: Multimedia Software
---

### Post by fiona-conn on 2008-12-10
Hi, folks. 

I'm having a few issues with my Logitech USB mic. This, I realize, is nothing new -- I did a search on the forum, and checked the settings in Audacity, as well as trying out the advice given in one thread (AUDIODEV=/dev/dsp1 Audacity), to no avail. 

Thing is, my microphone works fine in the Sound Recorder program. So I *know* that it's being recognized, and that my machine can receive input from it. 

But when I try to record in Audacity, I get: "Error while opening sound device. Please check the input device settings and the project sample rate."

I'm rather puzzled by this. This comes up regardless of if I use 44khz stereo with 32bit float, or the mono equivalent.

EDIT :: Oh! One thing I forgot to add! I'm running Ubuntu 8.10, if that's any help.

Any ideas?

Thanks for your time,

~Fiona.

---

### Post by fiona-conn on 2008-12-10
*Gentle bump...*

---

### Post by ufugu on 2009-01-08
These are the steps I took to get it fixed. I'm not sure if they are all necessary, but now I have Audacity working with my Logitech USB:

1) Add "killall pulseaudio" command to your Sessions to disable Pulse Audio.  Log out and log back in, your new session will have Pulse disabled and revert to ALSA by default. (For me this clears up a lot of sound issues in general.)

2) Open Synaptic, install the following:
audiooss
aoss

It is my understanding that Audacity uses OSS for sound, and these make ALSA emulate OSS in some way that makes Audacity happy.

3) In Audacity, go to "Edit > Preferences > Audio I/O" and select "ALSA : Default" for playback and your USB mic for recording.

Hope this helps!  And if there is someone here who can explain WHY this fix worked for me that'd be great.  Sound on Linux is kind of a mess :confused: ;)

---

