---
title: "Sound works in Sound Preferences/Test, not in applications"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by mikkoko on 2007-11-05
I have a Native instruments RigKontrol2 audio controller/soundcard (Comes with Windows/Mac Guitar Rig software) and was happy to see Ubuntu 7.10 detecting it!

It plays the test sound just fine in System/Preferences/Sound.. And the test in gstreamer-properties works also - but the problem is that no applications have sound. 

If I try to open the gnome volume control applet from the panel, it says that "No volume control GStreamer plugins and/or devices found."

Any ideas on how to proceed from here?

Thanks!

Some more info: 

- System/Preferences/Sound shows audio device as "RigKontrol2"
- gstreamer-properties shows audio device as Custom (pipeline: halaudiosink udi=/org/freedesktop/Hal/devices/usb_device_17cc_1969_SN_03A5BB96_alsa_playback_0)

---

