---
title: "sound is very low in 10.04"
date: 2010-07-22
forum: Multimedia Software
---

### Post by Messyhair42 on 2010-07-22
I just got Lucid working and the sound is really low, i have the sound (as part of ubuntu settings) all the way up and i still have to turn up my speakers and the volume of the program i'm using to get adequate sound. is there a way to turn it up without extra hardware?

---

### Post by swong on 2010-07-22
Try running "alsamixer" in a terminal, the master volume may not be at 100%.

---

### Post by soldier1st on 2010-07-22
set the volume to either 100% or 200% but the higher it is the louder it can be but your sound may sound distored and or choppy, also if you have it too high you could blow your speakers.

---

### Post by lidex on 2010-07-23
If not installed, install these items:
```
sudo apt-get install --reinstall pavucontrol paprefs paman padevchooser
```

Start the program you wish to configure. Run Pulseaudio Device Chooser from Sound & Video menu. Click on the icon in notification area and select 'Manager'.
On the devices tab select the sink that is the parent of the device currently playing. Click the properties button. In the resulting window push the volume slider to the right in small increments, releasing the mouse button each time to allow it to update. BE CAREFUL.

---

### Post by Linuxforall on 2010-07-23
In alsamixer, check your setting for pcm and wave, turn them up.

---

