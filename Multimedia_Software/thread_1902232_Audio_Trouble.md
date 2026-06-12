---
title: "Audio Trouble"
date: 2011-12-30
forum: Multimedia Software
---

### Post by ishu161 on 2011-12-30
I've followed all the guides I could find online and have even asked in #Ubuntu, but so far, I haven't been able to get my audio to work. Here's what's happened: 

I recently reinstalled Ubuntu 11.04 because my previous install was practically unusable (another problem, but that doesn't matter). When I found that the audio wasn't working, I fixed it, using this guide here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I used the Natty command, it downloaded and installed ~200MB of stuff, and when I rebooted, the audio was working fine. 

I installed some other applications after that. (Calibre, libtorrent, emacs, truecrypt, vlc). Next day I noticed the sound was gone again, but this time, the gnome audio control was not working.(It showed me this warning: gnome volume control warning connection failed). 

I tried the troubleshooting command again, and after a reboot, the audio control was back, but since then, I haven't been able to hear any sound. I do hear a slight "pop" when I try to play any music, but that's it. 

Here is my alsa info :  [http://www.alsa-project.org/db/?f=f0d5c64821141776485ab62e5b0a5b0f4c9e76fa](http://www.alsa-project.org/db/?f=f0d5c64821141776485ab62e5b0a5b0f4c9e76fa)

I'll appreciate any help on this problem. It's been a frustrating week because of this.

EDIT: 

If I try that long troubleshoot command again, I get this output: 

> E: Unable to locate package linux-alsa-driver-modules-2.6.38-13-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-2.6.38-13-generic'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules-2.6.38-13-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-2.6.38-13-generic'

---

### Post by MoreOrLess on 2011-12-30
Play with alsamixer and make sure nothing's muted
```
alsamixer
```

---

### Post by ishu161 on 2011-12-30
I made sure that alsamixer configurations are correct, so unfortunately that's not the problem. :(

---

### Post by lidex on 2011-12-31
My guess is the alsa-driver-module update fixed your sound, then you updated your kernel and there is not yet a module update for it. You could try the alsa-upgrade link in my sig or maybe try booting into the previous kernel that worked.

---

### Post by ishu161 on 2011-12-31
Thank you! The script worked and I now have sound! You are awesome! :D

---

### Post by lidex on 2011-12-31
> **ishu161 said:**
> Thank you! The script worked and I now have sound! You are awesome! :D

Good deal. Could you mark the thread solved using 'Thread Tools' up top please?

---

