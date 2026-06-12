---
title: "VLC advanced settings for recording?"
date: 2010-01-31
forum: Multimedia Software
---

### Post by atomicben on 2010-01-31
I'm trying to use VLC as a PVR.  I have an old AverTV analog card.  I can confirgure VLC to show me the feed from it.  However, when I hit record, the files produced are enormous.

To give you an idea of how big.  I hooked up my video camera and just filmed the wall for 40 seconds.  The file produced was over 650megs.  That's jus not acceptable.  I'm not trying to record in HD.  I don't even care all that much about quality.  i just want to record my shows.  If I could record a half hour for about 300megs, I'd be ok with that.

Can anyone tell me how to configure the record feature to do what I need?  At this point, I don't even care what format it outputs, I could find some way to convert it.  BUt if you can tell me how to transcode to Xvid or Divx, I would appreciate it very much.

In addition, is there anyway that VLC can remember my settings so that when I 'Open Capture Device' I don't have to re enter all the info over again?  I don't like how I open it and I have to set things like, the video device name (dev/video0), change to NTSC and then under advanced options I have to set the channel frequency.  It's so annoying trying to remember the frequencies of standard cable channels (eg. channel 3 is 61250). 

Thanks for your help.  I'm pretty new to Ubuntu and I really REALLY want to stick to it.  But in Windows I could use the AverTV software to hit record and get a reasonable file out of it.

Thanks,

Ben


Oh, I almost forgot some details:
Pentium 4 3.2 ghz Prescott
1GB RAM
NVidia (driver version 96)
Karmic
VLC 1.0.4 Goldeneye
I don't know the AverTV model but it's a BT878 chipset.  Works great with TVTime... I wish they would add a recorder.  :(

---

### Post by sports.car.guy on 2010-01-31
> **atomicben said:**
> I'm trying to use VLC as a PVR.  I have an old AverTV analog card.  I can confirgure VLC to show me the feed from it.  However, when I hit record, the files produced are enormous.

To give you an idea of how big.  I hooked up my video camera and just filmed the wall for 40 seconds.  The file produced was over 650megs.  That's jus not acceptable.  I'm not trying to record in HD.  I don't even care all that much about quality.  i just want to record my shows.  If I could record a half hour for about 300megs, I'd be ok with that.

Can anyone tell me how to configure the record feature to do what I need?  At this point, I don't even care what format it outputs, I could find some way to convert it.  BUt if you can tell me how to transcode to Xvid or Divx, I would appreciate it very much.

In addition, is there anyway that VLC can remember my settings so that when I 'Open Capture Device' I don't have to re enter all the info over again?  I don't like how I open it and I have to set things like, the video device name (dev/video0), change to NTSC and then under advanced options I have to set the channel frequency.  It's so annoying trying to remember the frequencies of standard cable channels (eg. channel 3 is 61250). 

Thanks for your help.  I'm pretty new to Ubuntu and I really REALLY want to stick to it.  But in Windows I could use the AverTV software to hit record and get a reasonable file out of it.

Thanks,

Ben


Oh, I almost forgot some details:
Pentium 4 3.2 ghz Prescott
1GB RAM
NVidia (driver version 96)
Karmic
VLC 1.0.4 Goldeneye
I don't know the AverTV model but it's a BT878 chipset.  Works great with TVTime... I wish they would add a recorder.  :(


Why not load the software to do PVR instead of getting by. With what you are trying to do it is like fixing a hole in a boat with a band-aid, not very practical. I honestly think your best bet it to look at software like MythTV or XBMC and save yourself the aggravation.

---

### Post by atomicben on 2010-02-01
I don't have an extra computer sitting around to turn into a PVR.

---

### Post by sports.car.guy on 2010-02-01
> **atomicben said:**
> I don't have an extra computer sitting around to turn into a PVR.

You can use the same computer to do it. For a while I ran both my MythTV back and front ends on one machine without really any problems.

---

### Post by SoundGuy.Jon on 2010-02-25
I'm having a similar situation, but rather than recording TV, I'm wanting to recording my video games via the RCA component plug on my AverTV card.

As far as not having to set the individual settings each time, I can help a bit. All 3 video sources (coaxial, component/rca, and s-video) are all within /dev/video0. Coaxial is input 0, component is 1, and s-video is 2. In terminal if you enter
```
vlc v4l2:///dev/video0:input=X
```where X is the number of the input you want, it should automatically open to the desired input, rather than having to set it individually each and every time. I assume that there are similar commands for choosing the correct frequency, channel, etc. I just haven't found out what they are yet.
And finally, I'm having a difficult time finding what the correct audio input source is coming from my AverTV tuner card. I've tried using /dev/audio, /dev/dsp/, and the one that MythTV says should be it, /dev/adsp. But I get an error every time telling me to check the log, but I the log file is always empty.
Can anybody help me with any of my problems?

---

