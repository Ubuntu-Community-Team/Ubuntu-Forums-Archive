---
title: "cannot control mythbuntu audio"
date: 2015-09-11
forum: Mythbuntu
---

### Post by linuxhippy on 2015-09-11
Hi!  I've been using mythbuntu for years with relatively few difficulties.  I started using mythbuntu about 5 years ago and was able to control the audio with my keyboard.  I think F9 muted the audio and F10/F11 increased & decreased volume.  Now those keys display audio changes but I don't hear the changes.  Is this functionality gone?

I did notice that alsamixer doesn't seem to be installed either.

---

### Post by linuxhippy on 2015-09-13
Got alsamixer working...it needs the full path of /usr/bin/alsamixer to see the Master volume (you only need that for controlling it with ssh on a phone).  Mine was set low at 34% and in the frontend setup the volume control under audio was set under audio output settings:

ALSA:default

Next page is for audio mixer device:

ALSA:default
 
Mixer Controls:Master

Then save these settings and go to watch TV or recorded program and you should be able to use the keyboard to control the audio.  F9 will toggle mute on/off.  F10 decreases volume and F11 increases volume.  If keyboard doesn't work, you can always ssh with your phone and use:

/usr/bin/alsamixer

use up/down arrows on Master to make volume increase/decrease

---

