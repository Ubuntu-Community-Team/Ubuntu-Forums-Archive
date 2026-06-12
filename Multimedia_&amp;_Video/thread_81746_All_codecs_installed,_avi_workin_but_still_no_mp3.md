---
title: "All codecs installed, avi workin but still no mp3?"
date: 2005-10-25
forum: Multimedia &amp; Video
---

### Post by kamakazi on 2005-10-25
I'm running 5.04 :(,... sorry this might be a "5.10 only" forum, but any help will do.

I loaded all the codecs:
[LIST]
[*]gstreamer0.8-plugins
[*]gstreamer0.8-lame
[*]gstreamer0.8-ffmpeg
[*]w32codecs
[*]libdivx4linux
[*]lame
[*]sox
[*]ffmpeg
[*]mjpegtools
[*]vorbis-tools
[/LIST]

used apt for all xcept libdivx4linux (got the tar, couldn't find a repository with the .deb).

Now my OS sounds work perfectly, I even can play AVI files with sound, but I can't play MP3 files - XMMS just freezes and i have to kill the process.

Pls help!
Tnx in advance,...

---

### Post by Mustard on 2005-10-29
You missed this one;

gstreamer0.8-mad - MAD MPEG audio decoder plugin for GStreamer.

With regards to XMMS you should go into preferences and change the output.  I'm using ALSA.

---

