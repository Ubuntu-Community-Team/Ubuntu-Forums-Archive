---
title: "Sound lags/crashes on 12.04 with ALC887-VD"
date: 2012-09-22
forum: Multimedia Software
---

### Post by tirade on 2012-09-22
I'm using Ubuntu 12.04 64-bit and whenever I boot, the login screen always freezes for about 30 seconds before allowing me to log in.

Volume control cannot be used. Applications that use sound either crash, or freeze for a minute or so before finally running.

I have a GIGABYTE GA-880GM-D2H motherboard. Linux detects an ALC887-VD codec although my board's manual claims it is ALC888B.

I have tried setting mode=auto or mode=generic in alsa-base.conf to no avail. I have tried installing the latest ALSA from source. Alsamixer is not my problem.

None of this was an issue on Fedora 17! Help!

In the attached archive I have my dmesg output as well as the output of alsa-info.sh.

---

### Post by tirade on 2012-09-22
All right, finally setting mode=generic does get me rudimentary control. Volume control works but, as others in similar situations have noted, sound plays out of **both** the front headphone jack and the speaker system.

---

### Post by tirade on 2012-09-24
Compiling my own ALSA drivers and/or running the first giant terminal command [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") only succeeded in making my soundcard totally invisible to Ubuntu.

Here's how I fixed it:

First, run the command to reset to Ubuntu stock defaults:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-backports-modules-`uname -r` libasound2
```


I added the following line to /etc/modprobe.d/blacklist.conf:
```
blacklist snd_hda_codec_hdmi
```

This is because one of the pieces of sound hardware being detected was the HDMI out on my ATI Radeon HD 5770. It wasn't listed as the first sound device, but something about this was making sound so buggy that nothing even showed up in the device list when I typed ```
aplay -l
```

With that, I was able to get rudimentary sound functionality as long as I had the following at the end of my /etc/modprobe.d/alsa-base.conf file:
```
options snd-hda-intel model=generic
```

But I like to be able to switch between headphones and main speakers just by plugging or unplugging my headphones. That feature isn't supported by the model "generic" so I changed that line to the following:
```
options snd-hda-intel model=auto
```

I had thought I had tried these steps before, but I think I had a hard time getting it to work because I would try more than one change at once. If you're troubleshooting your sound, **totally shut down your system and start it back up after every modification you make.**

---

### Post by tirade on 2012-09-25
After having working sound for a while, suddenly I booted up and even though the welcome noise played at the login screen, my desktop was totally silent. Not even a volume control appeared in the Unity bar at the top of the screen.

While searching threads at LinuxQuestions.org I discovered that the problem could have something to do with pulseaudio becoming corrupted. Deleting or moving .pulse and .pulse-cookie allows the system to re-create those files the next time you log in.

I did that and it corrected my problem.

---

