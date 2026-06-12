---
title: "Audio won't work after upgrade"
date: 2008-12-09
forum: Multimedia Software
---

### Post by Jimmey on 2008-12-09
I have recently done a fresh install of intrepid, but have kept my old /home partition.

Following the install my SB Audigy won't output sound using anything other than OSS.

I have set the card as the default and oddly selecting and testing "PulseAudio" in the sound preferences screen works fine. Just no sound outputs after that, from either Firefox, totem, VLC, rhythmbox, or even any system sounds. 

Attempting to select ALSA either results in silence or an error message:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

Does anyone know what I should do?

---

### Post by markbuntu on 2008-12-09
Try this, it will get you some important things left out of the install:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

