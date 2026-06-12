---
title: "Trying to record with audacity"
date: 2009-06-19
forum: Multimedia Software
---

### Post by newIsle on 2009-06-19
Hey all,

I've been trying to record some audio with audacity from FireFox as it plays...(not stealing, from an open source "Philharmonia orchestra site"..check it out)... I'm trying to record through the headphones into the mic jack..(through the output into input jacks)

anyway my problem is I cant distinguish between all the options in the alsaMixer... in the record tab theres six option for volume levels, capture 0, 1, 2, also Mux 0, 1, 2.. (also by default the little mic icons are all disabled by default whenever i open the alsa mixer,.. every time)

Then in the options tab of the mixer there are more options like,

IEC958 playback source;--1)Digital playback, 2) ADAT, 3) Analog Mux 1,2,3

*Digital Input Source;--1)Digital mic 1,2)Digital Mic 2, 3)Analog inputs

and finally; three separate of this option;

Input source;-1)mic, 2)front mic, 3)line

there are three jacks at the front on the notebook two for headphones and one for a mic

I should mention that there is a mic that works when I use skype, but i dont know if thats called the front mic or digital mic,, theres alot of options here that i dont quite understand

I'm running Jaunty 9.04 on Inspiron 1525 n series, kernel is 2.6.30rc
the audio device is listed as ;
82801H (ICH8 Family)HD audio controller STAC9200 Codec, Sigmatel 9205

i'm not sure what the problem(actually i do, its me) but I'm guessing it the settings, and what devices i choose to do the recording

Also while in audacity, it gives me several options for a recording device;
ALSA; HDA Itel:STAC92xxAnalog(hw:0,0)
ALSA; Pulse
ALSA; Default
OSS: /dev/dsp

don't know if thats relevant or not. 

any help would be great, thanks

---

### Post by Lord Noxarethor on 2009-06-19
Go to Preferences and check "Capture".
[http://img265.imageshack.us/img265/4155/screenshotsrw.png](http://img265.imageshack.us/img265/4155/screenshotsrw.png)
You'll get a 'Recording' tab... make sure that the slider is up, and it is not muted. 
In audacity you shall choose: ALSA; HDA Itel:STAC92xxAnalog(hw:0,0).

---

### Post by newIsle on 2009-06-19
hey thanks, i'll see if that works

---

### Post by BbUiDgZ on 2009-06-19
> **newIsle said:**
> hey thanks, i'll see if that works

have a look at [this](http://qjackctl.sourceforge.net/) it might help

---

### Post by newIsle on 2009-06-19
using jack is another story im having trouble with, first i trying to use ardour to record but i was unable to over come (so far) all the xruns and (jack and/or Ardour crashing)..i have found that audacity will not really work properly while jack is running...

again i think my problem lies in the alsa mixer options

---

### Post by newIsle on 2009-06-19
[http://i669.photobucket.com/albums/vv54/newIslander/Screenshot.png]("http://i669.photobucket.com/albums/vv54/newIslander/Screenshot.png")

[http://i669.photobucket.com/albums/vv54/newIslander/Screenshot-2.png]("http://i669.photobucket.com/albums/vv54/newIslander/Screenshot-2.png")

the options in the second image are the ones giving me trouble i think,  there are three input channels, with three options for each; 1)mic, 2)front mic, 3)line..

recording still not working in audacity :(

---

