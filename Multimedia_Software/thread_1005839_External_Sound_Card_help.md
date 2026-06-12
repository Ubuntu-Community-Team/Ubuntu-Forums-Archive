---
title: "External Sound Card help"
date: 2008-12-08
forum: Multimedia Software
---

### Post by koolcracker on 2008-12-08
Okay, so I have an external soundcard that I like to use, but Ubuntu won't recognize it as the default no matter what I do. I've tried to set it using asoundconf set-default-card Xmod, and when that didn't work, I went and edited my /etc/modprobe.d/alsa-base file to order the Xmod as 0 and the Intel card as 1, but my cat /proc/asound/modules keeps returning Intel as the 0 card.

cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio

and the lines in my alsa-base file are
options snd-usb-audio index=0
options snd-hda-intel index=1

I've had this issue before and the only thing that fixed it was reinstalling, but that can't be the only solution. Does anyone have experience with this?

---

### Post by psyke83 on 2008-12-08
If you're using Hardy or (especially) Intrepid, PulseAudio is responsible for sound mixing. What you need to know is that PulseAudio disregards ALSA module indexes and asoundconf configurations - you must change the default sound card (a.k.a. sink) in the PA Volume Control application, and not via other methods.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

