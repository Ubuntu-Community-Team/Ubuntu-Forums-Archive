---
title: "[SOLVED] Onboard digital sound not working with GT 430"
date: 2011-11-27
forum: Mythbuntu
---

### Post by timjunk on 2011-11-27
I wanted to post this so that the next noob has an easier time. I'm using mythbuntu 11.10. 

I'm a Linux noob and have not used mythtv for 6 years. I'm very impressed with mythbuntu. My first install worked flawlessly. Unfortunately at some point my dvi out stopped working on my graphics card. So I upgraded to a GT 430 with HDMI support.  After a clean install of mythbuntu, the sound did not work. My stereo is old and doesn't work with HDMI so I wanted the on board digital sound to work. 

Enter the first problem to solve. Turns out my bios was set to "auto" for inboard sound and the new card caused it to be disabled. Changed it to "enabled" and did a fresh install. 

Problem 2, still no sound. I was getting sound through my pc headphone jack  Finally realized I needed to go to multimedia >> mixer and select controls. I chose IEC958. Then I enabled it and now have sound. Although it looks like mythtv sound is still incorrect.  I'll continue to update this as I figure things out. It will certainly be good for my poor memory and hopefully it helps someone else as well.

---

### Post by timjunk on 2011-11-27
Went to mythtv utilities/setup >> setup >> general. A few pages in are the sound settings. I chose to scan for audio devices and then chose the iec958 device. Works great now!

---

### Post by timjunk on 2011-12-04
OK, I restarted and lost digital sound out to my stereo again.  Still worked in myth but not anywhere else.  Did some reading on the ALSA wiki and found the fix.

Created a .asoundrc file in my home directory.  
[http://alsa.opensrc.org/.asoundrc#Default_PCM_device](http://alsa.opensrc.org/.asoundrc#Default_PCM_device)

Put the following in the file and it worked like a charm.  

```
pcm.!default iec958:Intel
```

---

### Post by mtbdrew on 2012-03-26
Hello,

Not sure if you very got this working. I'm running a PNY GT 430 with Ubuntu 11.10 and HDMI audio was working at initial boot after install. Question for you if you are wanting HDMI audio then make sure you turn off on board audio device in the MB bios. 
For available devices you should only be seeing Nvidia Audio. Chances are you system is switching between the on board and GT 430 during reboots.
In regular desktop you should use the pulse sound apt to select which device to use. I got seven options, four different two channel and three different 5.1 channel. In Pulse only one of the 2ch options seemed to work.
In MythTV choose the corresponding plughw:x,y that produced sound, which gave me 5.1 audio over HDMI for movie/TV playback.

Br
Andrew

---

