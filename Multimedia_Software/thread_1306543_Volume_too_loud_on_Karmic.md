---
title: "Volume too loud on Karmic"
date: 2009-10-30
forum: Multimedia Software
---

### Post by mockdeep on 2009-10-30
I just installed Ubuntu 9.10 yesterday and I'm trying to work out some of the kinks.  When I began playing music I tried turning the volume down and found that the volume control goes from Really Loud down to Just Plain Loud at about the 15% mark, where it just mutes.  My remedy was to put it at the minimum and then go into Rhythmbox and lower the volume in there as well.  Is there a fix so I can get the full range of volume in the main control?

---

### Post by Brachabre on 2009-10-31
YES, i have the exact same problem. 

Running Dell Inspiron 9400 soundcard below:

dev@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I'll be in class, cold-boot into ubuntu 9.10, and the sound will be maxed. Pretty embarrassing when it happens more often than not :/

---

### Post by Artsaypunk on 2009-10-31
Hi folks,

I'm no expert here, but I'll try to lend a hand.  I'm dealing with something similar.  I also have an older Dell Inspiron 9300.  The problem I've always had with earlier versions of Ubuntu was that the sound doesn't mix the channels properly, inculding the subwoofer etc.  That leads to similar problems to the ones you're describing. Up until Karmic, I could link the channels to the master volume in the volume control applet for a decent fix.  That doesn't seem possible in the new Pulseaudio setup in Karmic, or at least, I can't figure out how to do it yet.

A temporary fix for you might be to install "Gnome Alsa Mixer" in Synaptic.  This gives you access to all the channels available on your soundcard.  You can manually adjust them to listen to something at appropriate volume.  However, as soon as you adjust your master volume, it'll probably get screwed up again.

Anyway, it's not a final fix for your problem, nor mine, but like I say it might help out temporarily or help diagnose the issue.  I'll let you know if I figure out anything else.

---

### Post by nickless on 2009-10-31
same here on Dell Inspiron 9400. really annoying.

edit: It is possible to adjust the volume for each program separately under system>options>audio or something like that.

---

### Post by insertnewsn on 2009-10-31
I'm having this problem as well!

Dell Inspiron E1705 (9400).

Seems to be a problem with the bass/subwoofer maintaining the same level of output even though the overall volume is decreasing. 

I always seem to have this problem after upgrading to a new Ubuntu release, but the way audio has changed so much in the last few releases, I have no idea how to get all parts of the audio (PCM/LFE and whatever else) to behave appropriately..

---

### Post by mockdeep on 2009-10-31
Well this worked for me:

[http://ubuntuforums.org/showthread.php?t=1234894#18]("http://ubuntuforums.org/showthread.php?t=1234894#18")

I had to restart my computer and now things are working alright.  Here's a link to the launchpad bug report.  Maybe throw in your voice so that it will get fixed sooner.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948")

---

### Post by nmanoogian on 2010-08-02
I have gathered some quick links from threads - I hope this helps!

[http://alkaline9500.co.cc/sound.html](http://alkaline9500.co.cc/sound.html)

---

