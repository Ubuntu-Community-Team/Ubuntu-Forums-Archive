---
title: "sound stopped working after upgrade"
date: 2010-01-19
forum: Multimedia Software
---

### Post by Ineffablewombat on 2010-01-19
Hi, I just upgraded from 8.10 to 9.10 and now my sound doesn't work (note: I don't know if sound was working on 9.4, since I only ran that long enough to upgrade again)   

Sound was working just fine under 8.10, and I just tried booting up with a livecd I had handy, which is 8.04.1  and sound worked right off the bat, no problems.   

I've checked the volumes on everything, including the master volume which WAS initially set to 0.  Sadly, turning that up did nothing.  
The Pulseaudio Volume Control app seems to think nothing's wrong- it's picking up the sound from various applications just fine, the volumes are all on, etc.  

(aplay lists my soundcard fine:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: NVidia [HDA NVidia], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
)   




I followed the instructions at 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
and the Comprehensive Sound Solutions Guide, but got a little confused when it came to figuring out ALSA drivers.  


I did try removing and re-installing the sound packages exactly as suggested by the comprehensive guide thread.   No effect.  

I ran the alsa-info.sh script referenced in the Sound Troubleshooting guide
Results for my current non-working setup:  
[http://www.alsa-project.org/db/?f=195ea8711f8886e144b7795f3130193e2354dc4d](http://www.alsa-project.org/db/?f=195ea8711f8886e144b7795f3130193e2354dc4d)
and for the working, 8.04 livecd:
[http://www.alsa-project.org/db/?f=32eea8238eab780c6164dba96912528c273a9506](http://www.alsa-project.org/db/?f=32eea8238eab780c6164dba96912528c273a9506)

Sadly, I have no idea what differences in there are important.    


I'm downloading the CD image for 9.10 at the moment so I can figure out if this is a 9.10 problem or what, but that's gonna take awhile.

---

### Post by Ineffablewombat on 2010-01-19
Okay, having tried running off the 9.10 CD, it looks like it's not a 9.10 problem so unless there's something obvious to try I'll just re-install from scratch tomorrow.

---

### Post by Ineffablewombat on 2010-01-20
...


Okay. I install 9.10 from scratch, sound works fine.  After having done nothing but installing, logging in, and playing a .ogg file succesfully with Movie Player, I let Update Manager do it's thing, and restart the system.  


And now the sound doesn't work. Again.  Once again the master volume got turned all the way down... but turing it up (via alsamixer) did nothing.  

???????????????????????

---

