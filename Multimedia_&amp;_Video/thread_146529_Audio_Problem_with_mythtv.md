---
title: "Audio Problem with mythtv"
date: 2006-03-18
forum: Multimedia &amp; Video
---

### Post by thaldyron on 2006-03-18
I have installed a Haupauge PVR-150. I get crystal clear audio when reading directly from the device with
```

mplayer -vo xv  /dev/video0

```
So the ivtv drivers seem to be working correctly.

But when recording with
```

cat  /dev/video0 > test.mpg
mplayer test.mpg

```
and also from withing mythtv there's an annoying background interference making the audio unbearable - so there seems to be some problem with recording & playback.

Any hints what that could be?

---

### Post by crazedgremlin on 2007-01-23
I have something similar

I've got an ati tv wonder pro
watching any recordings in mythtv there's weird hissing and popping noises, but if I watch tv in tvtime, it's "crystal clear."

there's an option in mythtv:
```
**Extra audio buffering**
Enable this setting if MythTV is playing "crackly"
audio and you are using hardware encoding. This
setting will have no effect on MPEG-4 or RTJPEG
video. MythTV will keep extra audio data in its
internal buffers to workaround this bug.
```

the setting has no effect on MPEG-4 or RTJPEG, but what are the other choices?  That's all I can choose to record in.

---

