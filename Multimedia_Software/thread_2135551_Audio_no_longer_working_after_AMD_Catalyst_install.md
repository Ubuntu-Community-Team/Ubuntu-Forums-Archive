---
title: "Audio no longer working after AMD Catalyst install, Xubuntu 12.04"
date: 2013-04-14
forum: Multimedia Software
---

### Post by axbycz on 2013-04-14
On a fresh Xubuntu install today I installed *fglrx-updates*, *fglrx-amdcccle-updates* and *fglrx-updates-dev* and, after restarting, everything worked fine apart from audio. The volume indicator is greyed out and there are no sound options to be found anywhere. I installed pavucontrol and xfce4-mixer but neither of them will open, and every time I try to play a song, the music player (I've tried VLC and gmusicbrowser) either freezes or sits at 0:00. Firefox hangs and eventually needs to be forced closed if I try to watch a video on Youtube or elsewhere. ([I posted this on Ask Ubuntu as well]("http://askubuntu.com/questions/281373/audio-no-longer-working-after-amd-catalyst-install-xubuntu-12-04"), but I'm searching everywhere and can't find another thread like this).

```
lspci | grep Audio
``` returns the following: 

    ```

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device aab0

```

I'm using a Radeon HD 7750 card, but my speakers are connected to the onboard Intel audio.

---

### Post by axbycz on 2013-04-15
Just fixed it! The problem must have lay with Pulseaudio, because when I followed the steps [here]("http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/") and uninstalled Pulseaudio, everything worked fine. Youtube videos play properly and no longer lock up the browser and VLC works as it should! :)

---

