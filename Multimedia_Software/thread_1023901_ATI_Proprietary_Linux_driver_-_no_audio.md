---
title: "ATI Proprietary Linux driver - no audio"
date: 2008-12-28
forum: Multimedia Software
---

### Post by goodrench on 2008-12-28
I have a homebrew home theatre pc with amd processor, ati 2400 hd video card and I am having trouble with the audio.
When I enable the ATI Proprietary linux driver I lose the audio.
I have the video card hooked up to my tv using a dvi to hdmi cable(no adapter). The audio is hooked up through the 1/8" speaker jack on the rear of the PC, using a cable that splits to R/L RCA jacks and plugged directly into the LCD tv.  The video card has a vga,dvi and s-video output. I would like to get it to work with the dvi to hdmi cable but I believe the ati driver is trying to use sound across hdmi( which is not possible). It doesn't matter what device is selected in System>Preferences>Sound. If I disable the ATI driver, all audio works fine. 
Is there a way to change this through a configuration file or something.
I don't know if pulseaudio is getting in the way or not. I have tried removing pulseaudio from the system and using esound, but nothing changes.
I have tried reinstalling the os, doing all updates first, downloaded the binary package right from the ATI/AMD site, but nothing seems to make a difference.
Any help would be appreciated.

---

### Post by markbuntu on 2008-12-28
There is a way to make a pulseaudio device for the hdmi output and then you can redirect any streams trying to use it to another device. The answer is in here, look for the Digital Output and PulseAudio section

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by goodrench on 2008-12-29
> **markbuntu said:**
> There is a way to make a pulseaudio device for the hdmi output and then you can redirect any streams trying to use it to another device. The answer is in here, look for the Digital Output and PulseAudio section

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I am not sure I understand what you mean.

---

### Post by goodrench on 2008-12-29
Maybe I should be shopping for a video card that supports hdmi?
Is this the simplest solution?

---

