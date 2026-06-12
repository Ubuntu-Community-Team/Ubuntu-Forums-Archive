---
title: "Can Bitrate be Changed in Gnome Sound Recorder?"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by themeone on 2007-06-08
I have successfully recorded a couple of cassette tracks as .ogg files using Sound Recorder.  However I noticed the recordings default to a bitrate of 128kbps, and wondered if this could be changed for future recordings?

---

### Post by Major_Kong on 2007-06-08
Yes, you can.

You have to use gconf-editor. Then go to /system/gstreamer/0.10/audio/profiles/cdlossy and edit the pipeline key.

The default should be : audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux

Change the quality to higher values like quality=0.6 to increase the bitrate.


PS: The bitrate is variable (vbr) not constant (cbr). So the displayed bitrate might not be very accurate...


[http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis#Recommended_Encoder_Settings](http://wiki.hydrogenaudio.org/index.php?title=Recommended_Ogg_Vorbis#Recommended_Encoder_Settings) - A little info.

---

### Post by themeone on 2007-06-08
That's great, thank you.  I had a feeling the solution was hiding somewhere in gconf-editor!

---

