---
title: "I royally messed up my audio situation in xubuntu 13.10"
date: 2014-02-13
forum: Multimedia Software
---

### Post by jawknee530 on 2014-02-13
So I was watching a video and was getting a buzzing noise so I opened up alsa-mixer to messa around with it. After that I installed gnome-alsamixer because I wanted a gui interface for it. Well while messing with that my audio cut out. After a restart the audio icon in my system tray disappeared. I've tried re installing alsa and pulse audio as well as trying to install the realtek drivers from their site.

When I try and open pulseaudio volume control the volume control says that it failed to connect to PulseAudio. When I try and force-reload alsa it says that there is no driver module to reload. I'm at a loss after two hours of scouring forums and any advice would be greatly appreciated.

Here's my alsa output [http://www.alsa-project.org/db/?f=60bf0b9a5e908f3d43feeb2f49951db4eba46a7f](http://www.alsa-project.org/db/?f=60bf0b9a5e908f3d43feeb2f49951db4eba46a7f)

---

### Post by Yellow Pasque on 2014-02-14
First, try reinstalling kernel image:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```

---

