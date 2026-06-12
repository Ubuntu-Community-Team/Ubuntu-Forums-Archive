---
title: "USB Audio"
date: 2009-06-16
forum: Multimedia Software
---

### Post by eklypze on 2009-06-16
I just got a set of Logitech Z-5 speakers the other way which work perfectly in Windows Vista Ultimate x64. I checked System > preferences > Sound and it will autodetect the Z-5 USB Audio. I have tried both ALSA and OSS and neither seem to be providing sound.

When I use ALSA I receive the error:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

However, when I use OSS I see the dialog box displaying that the audio is being tested yet there is still no sound.

My OS is completely updated, does anyone have any suggestions?

---

### Post by kostkon on 2009-06-19
What version of Ubuntu do you have?

Could you give the command:
```
aplay -l
```
and see if you can see them listed there.

---

