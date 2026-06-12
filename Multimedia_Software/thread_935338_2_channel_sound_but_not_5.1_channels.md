---
title: "2 channel sound but not 5.1 channels"
date: 2008-10-01
forum: Multimedia Software
---

### Post by JohnFH on 2008-10-01
I've had a look around the forum and tried a few things but can't get to the bottom of this.  I have sound, but only through 2 front channels. 

aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Has anyone else had the same problem with this device?  I'm running kubuntu 8.04 (64 bit) by the way.

Thanks.

---

### Post by markbuntu on 2008-10-01
SInce you are using Kbuntu and you need to do this in ALSA you can try editing your ~/.asoundrc file like here:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

---

### Post by JohnFH on 2008-10-01
Thanks for that.  I created .asoundrc as in the thread, but nothing changed.  Now though I have 5.1 sound even though I have since removed .asoundrc and restarted the sound system.  Bizarre.

---

### Post by Brebs on 2008-10-01
> **JohnFH said:**
> I have sound, but only through 2 front channels.
So? That's exactly what you'd expect with e.g. mp3 music - it's 2 channels, you get 2 channels. Be 1000 times more specific in describing what you want.

If you want 5.1 from 2.0 sound, see [thread](http://forums.gentoo.org/viewtopic-t-703981.html).

---

