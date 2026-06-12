---
title: "Mic works but not recording input"
date: 2011-12-04
forum: Multimedia Software
---

### Post by internetprofiles1 on 2011-12-04
I followed the steps in the tutorials and got my sound to work. The only  problem now is my mic does not record and there are no options in the  alsamixer to change the input, no ïnput source option. Only hint is I  have a video tuner and it was using that as the input, recordings just a  bunch of static. so I removed the tv tuner card. 
I CAN hear myself on the mic its crystal clear, I CAN hear sounds and  play videos with sounds, just for some reason the mic input cannot be  recorded. I am using onboard card. it has 1 mic input and 2 sound  outputs. The sound settings are set to 4.0 output analog input, I think  that the problem but there are no options to choose a mic input. Any  ideas? I also tried the update in the tutorials but everytime i reboot  it ubuntu  hangs for a long time.I am on ubuntu 11.10

check out my alsa screen shots 

[ATTACH]208541[/ATTACH]

[ATTACH]208542[/ATTACH]

[ATTACH]208543[/ATTACH]

---

### Post by internetprofiles1 on 2011-12-05
I figured this out.  The makers of my internal sound chipset is realtek audio. I went to 

[http://www.realtek.com/downloads/](http://www.realtek.com/downloads/)

click on the AC ´97 audio codec and realize they had a linux driver. Extracted the folder to desktop and run the install file, its self executing run from terminal and rebooted, and this time it did not hang like when i reinstall the alsa driver per ubuntu website.This reinstalled the correct alsa driver in the alsa mixer select capture mic and capture bars in order to record. The Gnome Alsa mixer also started working so no need to use terminal.

---

