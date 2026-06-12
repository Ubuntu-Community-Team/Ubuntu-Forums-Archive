---
title: "Thundersound sound card found but not working!!!!"
date: 2008-08-04
forum: Multimedia Software
---

### Post by asmugone on 2008-08-04
Ok I purchased a thundersound sound card, fresh install of ubuntu with the card installed registered it as a cmi 8738, however I am unable to hear ANYTHING, when I go into the sound panel and try to use the autodetect test I get this, 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

When i force it to alsa I get the test bar but no sound and when i hit okay the window hangs and must be force closed!

Putting it on oss yields this message:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

Someone PLEASE help me here!

---

