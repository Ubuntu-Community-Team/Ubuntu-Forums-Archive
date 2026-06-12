---
title: "gst-launch problem"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by spych102 on 2008-03-24
I'm trying to get to grips with gstreamer and I used the guide linked below:

[http://www.cin.ufpe.br/~cinlug/wiki/index.php/Introducing_GStreamer]("http://www.cin.ufpe.br/~cinlug/wiki/index.php/Introducing_GStreamer")

Trouble is, when I get to the ogg theora/vorbis playback command:

```
gst-launch-0.10 filesrc location="A_New_Computer--small.ogg" ! oggdemux name=d d. ! queue ! theoradec ! ffmpegcolorspace ! ximagesink d. ! queue ! vorbisdec ! audioconvert ! audioresample ! osssink
```

gst-launch just hangs at the preroll stage.

I replaced ximagesink with fakesink and the sound plays normally, so the problem must be with ximagesink. Can anyone help?

---

### Post by spych102 on 2008-03-25
So, I managed to get this command working:

```
gst-launch-0.10 -v filesrc location=TP1.ogg ! oggdemux ! theoradec ! xvimagesink
```

This uses xvimagesink instead of ximagesink and there is no ffmpegcolorspace element as xvimagesink can use theoradec as a source directly.

---

### Post by spych102 on 2008-03-25
An I can also play it even easier with

```
gst-launch-0.10 -v playbin uri=file:///path_to_file
```

I think I'm gonna try and convert stuff next.

---

