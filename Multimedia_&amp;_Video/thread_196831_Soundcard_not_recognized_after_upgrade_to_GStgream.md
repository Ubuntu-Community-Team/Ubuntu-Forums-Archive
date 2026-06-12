---
title: "Soundcard not recognized after upgrade to GStgreamer0.10"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by slider on 2006-06-14
I'm running an Intel D865 Perl Motherboard with the onboard Analog Devices sound system. It was working "OK" as set up by the Ubuntu installer using the alsa driver. I was having trouble with RhythmBox crashing while importing my mp3's so I rebuilt it using the 0.9.4.1 sources. Yeah!!! .......  Rhythmbox now imports my mp3's and doesn't crash. Boo!!! ..... To build RhythmBox I had to install other packages including GStreamer0.10 . Now I don't get any sound. 

Sound preference panel shows no default soundcard and I get the red slash over the sound icon on the top panel. alsamixer complains "snd_ctl_open failed for default: no such device". I've  installed all of the GStreamer0.10 plugins (including alsa) to no avail.

Right now I am trying to find where the GStreamer docs are hidden, however, any suggestions as to how to go about debugging this would be much appreciated. I'm fairly new to desktop linux and a complete Ubuntu noob.

Thanks for your time

---

### Post by slider on 2006-06-15
You can ignore the above post. I obviously installed some bad packages in my overzealous attempt to satisfy the build dependencies of Rhythmbox 0.9.4.1 . I'm back to square one with sound working and Rhythmbox not building. If anyone knows exactly what gstreamer packages I need to install to build Rthythmbox 0.9.4.1 to build I'd appreciate a pointer. 

TIA

---

