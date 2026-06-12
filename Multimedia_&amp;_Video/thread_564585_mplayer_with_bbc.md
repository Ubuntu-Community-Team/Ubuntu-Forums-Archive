---
title: "mplayer with bbc"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by pakku on 2007-10-01
I followed all of ariel's instructions but have no success.  I replied to ariel's original thread but since I didn't see any response I thought maybe nobody looks at that any more and am creating a new one.
Feel free to slap my wrist if this was wrong

Anyway, when I click on the news video link on BBC
I get a series of messages of the type
[I]Playing mms:// a series of letters and numbers"
Buffering mms://a series of letters and numbers
Connecting to server series of letters and numbers
Connected[/I]

But no video.

Any thoughts?

Ditto for trying to view USopen.org's videos.  cnn works fine but I think that uses Real player by default.

The site works well enough on the same PC in XP (it is a dual boot) so I am loath to blame it on hardware

---

### Post by freeflyer57 on 2007-10-17
It sounds like you don't have the proper codecs. Find out what the fromat is and install the codecs.

---

### Post by FredB on 2007-10-17
You'll have to use the totem plugin and gstreamer dirac package.

> GStreamer Dirac video plugin
GStreamer plugin for encoding/decoding of Dirac video streams 
The Schroedinger project will implement portable libraries for the high quality Dirac video codec created by BBC Research and Development. Dirac is a free and open source codec producing very high image quality video.
This package contains a GStreamer plugin that allows encoding and decoding of Dirac video streams in any application that uses GStreamer.

You can find it in Add / Remove programs.

---

