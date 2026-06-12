---
title: "HDA Intel: No loopback recording?"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by eye208 on 2007-09-14
Hi!

I've got two computers with onboard sound (Realtek ALC880 and ALC885) both using ALSA's "HDA Intel" driver (snd_hda_intel). Everything works fine except I cannot record the sound output of other programs in loopback mode. The only available input devices are Mic, Front Mic, Line, CD. There is no "Mix" or similar.

Is this a bug or a missing feature in the driver? Is there any workaround except attaching an actual loopback cable to the line in/out jacks? Maybe some .asoundrc tweaks?

---

### Post by linuxwizard on 2007-09-15
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by eye208 on 2007-09-20
bump

---

### Post by John Harrington on 2008-01-12
I'm having the same problem with an HDA Intel card using a Realtek ALC882 chip in an Asus  Z96Jm laptop.  I've tried most of the model options for this chip given in /usr/share/doc/alsa-base/driver/ALSA-configuration.txt but none of them gives any input options other than mic, front mic, cd and line.  I have the current versions of alsa-utils and alsa-base from the Gutsy repositories, and I'm reluctant to upgrade ALSA manually as described in the HdaIntelSoundHowTo.  Does anyone know whether upgrading would solve this problem, or whether there's any other solution?  Thanks.

---

### Post by John Harrington on 2008-01-14
I think I've found a workaround using Jack.  Install QJackCtl from the Gutsy repositories, which will bring in jackd as a dependency.  This creates a menu item called "JACK Control" under Applications => Sound & Video.  It is a gui control for Jack.  You have to launch it, and then click "Start".  I didn't have to configure anything.  Then open Audacity and, if you've got the Device toolbar visible, there should be a recording option labelled "JACK Audio Connection Kit."  Alternately, in Audacity, you can go to Edit => Preferences => Audio I/O => Recording => Device => JACK Audio Connection Kit.  Note:  You have to start Audacity after you click start on the JACK interface.  You also have to keep JACK running while you record.  There's a button called "Patchbay" on the Jack interface which I think is supposed to create a persistent channel or pipe (not sure of the terminology) but I don't know how it works.

The foregoing works seems to work fine.  If you're looking for an alternative, I found three possible options, none of which I've tried successfully:

1.  The ALSA module snd-aloop.  I can't install this module, but there are references to it here::  

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21569.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21569.html) 
[http://www.alsa-project.org/main/index.php/Changes_v1.0.13_v1.0.14](http://www.alsa-project.org/main/index.php/Changes_v1.0.13_v1.0.14)

2.  The latest ALSA hda-codec file.

3.  Realtek's own Linux driver for HDA:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)

---

### Post by John Harrington on 2008-01-15
One other point:

I don't have a realtime kernel, and I found that recording using jack was distorted because of xruns and/or dropped data.  I increased the jack buffer size in the interface settings from 2 to 10, and that seems to have solved the problem.

---

### Post by dspcarlos on 2008-02-01
Hello,

Have you finally configured qjackctl?...

I'm trying to use it, but I don't know how...

The problem is I dont know if the 2 application I want to interconnect must be jack-compatible...

thanks

---

