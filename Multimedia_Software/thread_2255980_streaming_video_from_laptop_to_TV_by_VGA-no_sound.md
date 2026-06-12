---
title: "streaming video from laptop to TV by VGA-no sound"
date: 2014-12-09
forum: Multimedia Software
---

### Post by cicada2 on 2014-12-09
I have Ubuntu 1404 on my laptop. I get sound on the laptop. But nothing is coming thru to the TV when I mirror the screen display. This VGA cable has a 3.5mm plug bundled, so I think it's a configuration issue in my software. I tried adjustments by using the sound controls, but there really aren't any options to change my output. I don't think pulse audio is installed - do I need it? Sorry to be such a noob. Any help is appreciated!

---

### Post by ajgreeny on 2014-12-09
Are you sure pulseaudio is not installed?  It is a default sound package in Ubuntu and should be in the list of packages you already have.

You may, however be missing pavucontrol, which lets you configure the sound setup, so check that and install it if needed.

---

### Post by cicada2 on 2014-12-09
I will go ahead and install pavucontrol. Thanks ajgreeny!  

Is there an  easy way to check for pulse audio. I was certain it would be installed,  but I cannot locate it. I am running GNOME on Ubuntu - so I searched  applications and also checked the software center... it looks like I  don't have it.

---

### Post by cicada2 on 2014-12-09
Here is what I did to restore sound. Reinstall Alsa and Pulse Audio. Try to reinstall pulse audio and Alsa, open terminal and enter the following commands:
 
Purge Alsa and Pulse audio using the command:
 ```
sudo apt-get remove --purge alsa-base pulseaudio
```

Now install again Alsa and Pulse Audio:
 ```
sudo apt-get install alsa-base pulseaudio
```

Then, reload Alsa:
 ```
sudo alsa force-reload
```

---

### Post by adlu on 2015-05-29
The steps in this document describe how to troubleshoot and fix the problem when there is no sound coming from the speakers.


[http://www.deskdecode.com/how-to-fix-no-sound-problem-laptop-desktop-computer/](http://www.deskdecode.com/how-to-fix-no-sound-problem-laptop-desktop-computer/)

---

