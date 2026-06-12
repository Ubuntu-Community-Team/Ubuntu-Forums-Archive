---
title: "Sound in some programs but not in others EX:(totem &amp; vlc)"
date: 2009-05-25
forum: Multimedia Software
---

### Post by yumikitsune on 2009-05-25
The sound tests work, sound plays fine in firefox, rythembox and at the splash screen. Yet, VLC and totem don't make a sound. No errors or anything, I've made sure vlc uses alsa (oss doesn't work according to the sound test) but still nothing, Any clues?

---

### Post by Yellow Pasque on 2009-05-25
For VLC, perhaps install the vlc-plugin-pulse package and set VLC to use PulseAudio

Make sure you have the System -> Preferences -> Sound options set to PulseAudio.

I'm not sure why rhythmbox would work and totem wouldn't (they both use gstreamer), unless you're trying to play something in totem without the right codec.

---

### Post by yumikitsune on 2009-05-25
PulseAudio doesn't work either according to the system sound test. As for the codecs its just an mp3, I downloaded the proper codecs through totem and it says its playing but doesn't produce any sound.

---

