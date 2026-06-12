---
title: "Sound Will not Capture with Line-In"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by jlr4u on 2007-01-21
I have a PVR-500 that works great with record/playback from cable/TV input running MythTV.   I have been trying for days to get the composite video and associated Line-In audio to work with a satellite system.  The audio stream does not capture.

Using system preferences Sound, you can perform a test.  The last section under capture using ALSA does not produce any tone.  I have loaded the gnome-alsamixer  but have not been able to get the capture mode to work with the computer line-in.

```
 cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC655 at 0xfe02d000, irq 225
```

```
cat /proc/asound/devices
  2:        : timer
  3: [ 0- 2]: digital audio playback
  4: [ 0- 1]: digital audio capture
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0]   : control

```

Can someone please help

---

