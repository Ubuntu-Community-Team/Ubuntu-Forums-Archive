---
title: "YASNWT (Yet Another SPDIF Not Working Thread)"
date: 2010-01-05
forum: Multimedia Software
---

### Post by yonkiman on 2010-01-05
I've spent about 12 hours over the last few days struggling with this, but I think I can summarize it succinctly.  After upgrading Mythbuntu 9.10 to use nvidia 190 driver, I lost my SPDIF audio.

[LIST]
[*]When booting, my SPDIF cable tip lights up halfway through, then goes out a second or so after it gets to the log-in screen.  I can never get it back on.
[*]To try to simplify the problem, I've removed PulseAudio.  (I've also tried the opposite - to get PulseAudio working - no dice.)
[*]I upgraded to alsa 1.0.22.1 (first manually thanks to [MoosesooM]("http://moosesoom.blogspot.com/2009/12/asus-k50ij-x5dij-audio-english.html") and then with a script thanks to [soundcheck]("http://ubuntuforums.org/showthread.php?t=1046137")).
[*]aplay -l output: ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[*]alsamixer has "S/PDIF" and "S/PDIF Default PCM" un-muted (set to "00") 
[*]"speaker-test -Dplughw:0,0 -c2" - I hear the pink noise
[*]"speaker-test -Dplughw:0,1 -c2" - No light on spdif cable (so obviously no sound)
[/LIST]

I think the last two bullets are the most interesting.  

I have literally spent about 12 hours on this.  Any help appreciated!

---

### Post by yonkiman on 2010-01-05
One thing I forgot to mention: Ubuntu seems to consistently think I have an ALC889A, but the manual for my motherboard (DFI BloodIron P35) says I have an ALC885.  They're probably interchangeable, but just in case...

---

### Post by yonkiman on 2010-01-06
A few more things:
[LIST]
[*]When the system boots, the analog output sounds like it's playing 2 (no more than 3) copies of the Ubuntu boot sound at the same time, but staggered by a second or so.  ???  Is this a clue to what's hosed?
[*]Is there a log file I could look at to see why "speaker-test -Dhw:0,1 -c2" doesn't give me an output?
[/LIST]

---

### Post by yonkiman on 2010-01-09
It wasn't the PC at all - it was the A/V receiver.

I ignored the most basic, simplest rule of debugging: verify your basic assumptions. I assumed my A/V receiver couldn't be the problem because it was brand new, it was working fine before I upgraded the video driver (and it has nothing to do with the video driver), and I hadn't messed with any of its settings. So in all the hours I spent troubleshooting, I never verified that the receiver was still working with an optical input. Tonight I plugged the s/pdif from my Ubuntu system into the optical input for the CD, and it worked. My receiver had somehow scrambled the connection for the original optical input. I played with the receiver preferences (switching the input source to HDMI and then back to optical) and now it works again.

Live and learn (again)...

---

