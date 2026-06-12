---
title: "Alsa config help needed"
date: 2010-02-22
forum: Multimedia Software
---

### Post by CannonFodderSE on 2010-02-22
I have an onboard sound card and a Logitech G35 USB headset.  I can get sound from either one by itself.  What I want is to have the sound from both simultaneously. 

HW 0 is the onbard sound card and HW 1 is the G35.  My .asoundrc is as listed below:

pcm.!default {
    type hw
    card 1
}

ctl.!default {
    type hw           
    card 1
}

I want to be able to use the mic on the headset.  any suggestion would be greatly appreciated.

Randy

---

### Post by CannonFodderSE on 2010-02-28
Hmmm, looks like I'm not the only one stumped with this one.

Randy

---

