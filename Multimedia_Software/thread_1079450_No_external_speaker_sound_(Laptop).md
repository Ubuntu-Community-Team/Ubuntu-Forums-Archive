---
title: "No external speaker sound (Laptop)"
date: 2009-02-24
forum: Multimedia Software
---

### Post by Qrackaduck on 2009-02-24
Hey peops... The internal laptop speakers is working fine, but when I plug in my speakers/headphones there's no sound.

I've been searching the net for 2 days now and I can't find any solution to my problem. I found a lot of threads with people having the same problem, and they had this easy solution:

Double click on the speaker icon then changing different options (Headphones, amps etc.). But I don't have those options. Is there anyway to get them?

I only have: HDA Intel (Alsa mixer)
Playback: Master and PCM
Recording: Capture and Digital
Switches: Caller ID and Off-hook
(I don't have the options tab)

I also found solutions by going into the BIOS and changing stuff. But I only have two things to enable/disable, is that right or am I looking the wrong place? Its the place with Boot options as well... 

Using 8.04 and the "lspci | grep -i audio" output is:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Hope you can help me and sorry for the long post!
thx

---

### Post by markbuntu on 2009-02-24
You can look in here, there are a lot of issues with the intel HDA. Look in the drivers section.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

