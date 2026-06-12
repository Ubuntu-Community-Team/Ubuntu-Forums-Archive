---
title: "all sound is cracking/inaudible as it plays - used to work"
date: 2009-09-06
forum: Multimedia Software
---

### Post by jdstunner on 2009-09-06
I have researched this problem throughout the forums, but haven't seen anyone with a problem as specific as this. I have been using the Ubuntu forums for almost two years and have been able to teach myself linux using almost these forums alone! Thank you to everyone who contributes to these pages. They are of great assistance to everyone! I look forward to adding my own contributions as my knowledge of this great OS increases. 

I am running 9.04 on a AMD Quad, 4 GB, Asus Mobo. I am using the onboard sound: VIA VT1708B 8-Ch

I have been running Ubuntu for about 2 months on this new PC. I recently did a format and reinstall. Everything has been working perfectly. I established network, updated, installed codecs for video and sound, tested (Good), installed all necessary software for a LTSP system (good) and began to work on my visual desktop appearence using Compiz. After making a large number of changes to the appearance, I restarted.

Upon restart, the initial logon screen played its usual chime. When I logged in, the startup sound came out of the speakers as just static and crackling. I checked an MP3, same thing. The music/sound plays, but the only sound that emits from the speakers is noise. 

I tried another pair of speakers and they produced the same effect.

I booted my Live CD and played an MP3, it sounded great. 

Something has happened to my sound configuration. I am lead to believe that it is a driver issue. Although, I have been steady configuring the computer and have done a number of reboots. I don't understand why Compiz seems to be the culprit here. It was the last thing I was editing before I ran into this issue. I did reset all Compiz settings to default and am still experiencing the issue after reboot. 

I used Synaptic to reinstall the pulseaudio and alsa drivers as well as a number of plugins and codecs for audio and video. 

I have a good understanding of linux but I am still learning everyday. Please advise as to which configuration files I should look at and where I can look to troubleshoot this problem. Thank you!

---

### Post by jdstunner on 2009-09-06
SOLVED

I turned up the PCM volume control to max. Evidently, when the PCM is turned down all the way, it produces static on the device. 

Thank you Ubuntu Forums for another solved case! Just took a little more searching.

---

