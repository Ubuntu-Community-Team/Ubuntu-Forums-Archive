---
title: "can't get video playback despite codecs"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by aijazbaig1 on 2007-06-05
Hello.
I have been having trouble any kind of video files..be it .avi or .mpeg,.mpg or anything.
I have the following gstreamer plugins installed as it shows in synaptic package manager,
[LIST]
[*]GStreamer plugin for ALSA
[*]FFmpeg plugin for GStreamer
[*]Fluendo mp3 decoder GStreamer plugin
[*]Fluendo GStreamer plugin for MPEG2 demuxing
[*]GStreamer plugin for GnomeVFS
[*]GStreamer plugins from the "bad" set
[*]GStreamer plugins from the "bad" set (Multiverse Variant)
[*]GStreamer plugins from the "base" set
[*]GStreamer plugins from the "good" set
[*]GStreamer plugins from the "ugly" set
[*]GStreamer plugins from the "ugly" set (Multiverse Variant)
[*]GStreamer plugins for X11 and Pango
[*]Core GStreamer libraries and elements
[*]GStreamer libraries from the "base" set
[*]totem-gstreamer
[/LIST]
Despite having all these plugins..i dont see any video at all.i can hear the sound pretty nicely..additionally i can play mp3 files as well the sound stream of those video formats like mpeg,mpg and avi..even wmv....ive tried movie player, gxine and even vlc..i wonder whats wrong..and i wonder if there are conflicting plugins trying to take control of the video stream simultaneously.
If thats the case I would like to remove all the plugins and even any specific plugin for any of these media players. Is there any easy way to do that?
What other suggestions do u have?

Hoping to get this problem solved,

best regards,
Aijaz

---

### Post by dodgePT on 2007-06-05
Type gstreamer-properties in a terminal, select Video tab, and choose X11/No Xv or any other option that works best for you.

---

### Post by JonDubya on 2007-06-05
> **dodgePT said:**
> Type gstreamer-properties in a terminal, select Video tab, and choose X11/No Xv or any other option that works best for you.
I know this isn't my thread, but thanks, that helped me fix my problem!

---

### Post by DarqueWing on 2007-06-05
That fixed me up, too.  Good call, DodgePT!

---

