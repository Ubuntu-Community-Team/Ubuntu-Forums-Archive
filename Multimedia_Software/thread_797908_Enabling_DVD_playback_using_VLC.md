---
title: "Enabling DVD playback using VLC?"
date: 2008-05-17
forum: Multimedia Software
---

### Post by kimvall on 2008-05-17
GOAL: Play DVDs using VLC.
PROBLEM: Image lags, like the PC is low on CPU.
INFO: Used to work fine on this PC (I just lost the installation scripts that installed all the codecs, etc - Great!)

1. sudo apt-get install vlc
2. sudo apt-get install libdvdcss2

These two steps are mentioned in most HOWTOs on enabling DVD playback. And it does work, almost. It's just that the image is out of sync, and you can really see that the VLC struggles so very very much, even when it's not in full-screen mode. And it used to work, using the exact same PC (I haven't changed anything, I just reinstalled it).

Check out the attached and you'll see what I mean.

Any clues? Recommendations?

---

### Post by ubuntu-freak on 2008-05-17
> **kimvall said:**
> GOAL: Play DVDs using VLC.
PROBLEM: Image lags, like the PC is low on CPU.
INFO: Used to work fine on this PC (I just lost the installation scripts that installed all the codecs, etc - Great!)

1. sudo apt-get install vlc
2. sudo apt-get install libdvdcss2

These two steps are mentioned in most HOWTOs on enabling DVD playback. And it does work, almost. It's just that the image is out of sync, and you can really see that the VLC struggles so very very much, even when it's not in full-screen mode. And it used to work, using the exact same PC (I haven't changed anything, I just reinstalled it).

Check out the attached and you'll see what I mean.

Any clues? Recommendations?

 
Could it be PulseAudio related? Try switching to ALSA in VLC's preferences, seems to have helped some with similar issues in MPlayer.
 
Nathan
 
P.S Did enabling deinterlacing make any difference?

---

### Post by kimvall on 2008-05-17
> **reassuringlyoffensive said:**
> Could it be PulseAudio related? Try switching to ALSA in VLC's preferences, seems to have helped some with similar issues in MPlayer.
 
Nathan
 
P.S Did enabling deinterlacing make any difference?

Hello Nathan, thank you for a speedy reply.

1. I found two instances of deinterlacing, and enabled them both.
2. I installed the pulseaudio package.
3. I installed vlc-plugin-alsa, and the ALSA option appeared in the VLC settings.

After completing step 1, 2 and 3 (I tried all ALSA options) there's still no improvement.

---

### Post by ubuntu-freak on 2008-05-17
> **kimvall said:**
> Hello Nathan, thank you for a speedy reply.

1. I found two instances of deinterlacing, and enabled them both.
2. I installed the pulseaudio package.
3. I installed vlc-plugin-alsa, and the ALSA option appeared in the VLC settings.

After completing step 1, 2 and 3 (I tried all ALSA options) there's still no improvement.

 
Well, as a last resort, try installing esound, remove pulseaudio packages, switch to ALSA in System > Preferences > Sound and in VLC's preferences. Rebooting afterwards may help.
 
Nathan

---

### Post by kimvall on 2008-05-18
I managed to fix it.

1. I installed Ubuntu 8.04.
2. Added Medibuntu to sources.list.
3. Installed VLC and libdvdcss2 packages.

I.e. exactly what I did before, only on Ubuntu 8.04. So newer DOES equal better!

Anyway, thank you all for your concern. :)

---

