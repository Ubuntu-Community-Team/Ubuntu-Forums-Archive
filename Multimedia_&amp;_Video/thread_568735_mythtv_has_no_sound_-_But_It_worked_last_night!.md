---
title: "mythtv has no sound - But It worked last night!"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by cdfccf on 2007-10-06
Hello everyone,

first let tell everyone that I am a complete NOOB when it comes to Linux!

 I picked up a non-working   IMAC G3 computer for $10 from the classifieds, and managed to get it back up and on its feet using Xubuntu (easier on older computers with less resources)

That was it for me. I think that I am hooked on Linux and at least to this point on specifically on Ubuntu!

Anyway, enough babbling. My current problem is that I have installed Ubuntu "feisty" on my desktop unit. ( HP A6230N, AMD Athlon 64X2 5600+ 2.8Ghz, 3GB Ram, 400GB HD) after sucessfully installing "feisty" I attempted to  install MythTV. 

I thought that I had it successfully installed, (thanks for the Install instructions S.D. Plisskin)
Last night I was watching Live TV using MythTV I was able to rewind and FF live TV and record to HD) this morning however, upon firing up MythTV, I get the picture, but no sound.

any ideas?

---

### Post by derby007 on 2007-10-06
I have the same problem, I had sound working & then like magic it dissappeared......dog gone mythtv :(

I see alot of unanswered post with regard to sound in mythtv not working.

So, try this, and let me know if it works, as I can't try it till I get home tonite.

Shutdown 'mythbackend', then go into 'mythtv-setup', change audio-device to /dev/dsp1 (from  /dev/dsp), then restart 'mythbackend', and go back into 'mythfrontend' & see if it works.....

I got this 'mythtv-setup' help on a web site: 
"The audio device should be set to the audio device of your TV tuner card, not the audio device of your soundcard. If you are using ALSA with OSS emulation (most likely, you are), then your soundcard is using /dev/dsp, and your tv card will use the next available device -- /dev/dsp1. So, change audio device to /dev/dsp1. 

Audio sampling rate limit is the kHz at which to record audio. Please note that some TV tuner cards *must* have this set to a specific setting or audio will not record properly. If unsure, leave it set to the default option of (None) for now, and you can always come back and change it later. 

The 'do not adjust volume' option would affect watching Live TV. 

For default input, a lot of TV tuner cards have more than one input device to record and display video from. If you are using a coaxial cable (cable TV), then set this to "Tuner" or "Television" (whichever is available). 
Save your settings when finished, and exit back to the main menu"

---

