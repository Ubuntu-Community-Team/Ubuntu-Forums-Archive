---
title: "Volume control not working after alsa upgrade"
date: 2010-04-07
forum: Multimedia Software
---

### Post by progre55_icky on 2010-04-07
Hi all,

My internal mic on sony vaio was not working on karmic 64bit. After I followed these instructions [http://ubuntuforums.org/showthread.php?t=1292587](http://ubuntuforums.org/showthread.php?t=1292587) (updated alsa to 1.0.22) I got the microphone working, but now mplayer does not play any sound (although it plays files), as it tries to use pulse by default. However when run with -ao alsa, it works fine.

Other than that, the volume control has not effect on the sound, so every time I need to control it using alsamix.

When I remove pulseaudio, everything seems to be working, except gnome-volume-control and gnome-volume-control-applet do not start, and the keyboard volume controls dont work.

Here are the sound cards I have:

```

progre55@progre55:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


progre55@progre55:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.
Compiled on Apr  7 2010 for kernel 2.6.31-20-generic (SMP).

```Any suggestions highly appreciated!

Regards,
Ikrom

---

### Post by lidex on 2010-04-08
Do your other apps have sound?
Click the pulseaudio link in my sig and follow steps for karmic.

---

### Post by progre55_icky on 2010-04-08
Thanks a lot man, your guide worked!
I'm thinking it was probably because of the  libsdl1.2debian-pulseaudio library, as I had to remove the libsdl1.2debian-alsa, and not both my mic and sound are working.

Thanks a lot, appreciate!

---

### Post by progre55_icky on 2010-04-08
I think the problem was having 2 sound cards.

After I run alsamixer now, the second card (Intel) disappeared from the "volume control > ouput devices", and I again experienced the very same symptoms. After a restart, it appeared, but R700 was set as fallback. When I set "internal audio analog" as fallback, it got fixed again.

Well anyways, I'm not opening alsamixer anymore ))

Thanks for all the help!

---

