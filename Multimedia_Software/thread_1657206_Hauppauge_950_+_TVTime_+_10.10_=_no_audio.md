---
title: "Hauppauge 950 + TVTime + 10.10 = no audio"
date: 2010-12-31
forum: Multimedia Software
---

### Post by imrazor on 2010-12-31
I've recently upgraded to Ubuntu 10.10 and have hit a snag. Previously I had been able to use TVTime to watch TV from an EyeTV Hybrid USB tuner (equivalent to a Hauppauge HVR-950/980 *NOT* the 950Q). I am able to watch TV, but not listen, after extracting the proper firmware to /lib/firmware. I worked around this in older versions of Ubuntu with the "sox" command. Problem is in Meerkat there are no /dev/dsp or /dev/mixer devices for sox to do its magic on. I've also tried to see if there is some way to monitor my audio input devices in Meerkat (in other words, redirect them straight to audio output instead of a recording program), but I have had zero luck in finding a working method. 

My next attempt will be to try and get MythTV working, but I expect that, like past attempts, it will be an exercise in futility. Anyone out there gotten this hardware config to work with 10.10?

---

### Post by imrazor on 2011-01-02
Found a messy fix in this thread:

[http://ubuntuforums.org/showthread.php?t=1324135](http://ubuntuforums.org/showthread.php?t=1324135)

Problem is, I've found I have to kill and restart pulseaudio then reload the loopback module every time I quit TVTime. Better than nothing though. I'm going to go ahead and try a full blown mythbuntu install and see if that works out better. Installing mythtv manually looks to be a pain...

---

### Post by imrazor on 2011-01-02
Ugh ... double post. Sorry, folks.

---

