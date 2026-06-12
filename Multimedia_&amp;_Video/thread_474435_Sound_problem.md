---
title: "Sound problem"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by mitsuo on 2007-06-15
well, i have a problem.. i play ET(the fps game), at first, the sound was not working there at all..
but after a few tries of 
```

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```and
```

echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```
 i manage to get it to work..
but there is a problem.. there is still no sound if i decide to run amarok/any other music player in the background...
thanks in advance..

---

### Post by dabl on 2007-06-15
Open the Volume Control (little speaker icon in the upper right of your desktop), make sure the PCM and Front channels are not muted.  Click "Edit>Preferences" and make sure all the boxes are checked. :)

---

### Post by mitsuo on 2007-06-15
i have checked it and it was ok..
it don't seem to solve the problem..

---

### Post by paulg on 2007-06-15
I think the problem is that you are using OSS drivers. Are there ALSA drivers available/installed for your card? You will probably have better luck running multiple sound programs from ALSA.

~pAul.

---

### Post by mitsuo on 2007-06-16
i think i do..
i have an OB sound card.. my mobo  is GIGABYTE 945GZ.. which is not too antique so i suppose it should be able to use alsa..
whether i know how to reroute the programs there is another thing..

---

### Post by mitsuo on 2007-06-16
so, does anyone have any idea how do i reroute the apps to use alsa?

---

