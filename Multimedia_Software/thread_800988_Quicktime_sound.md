---
title: "Quicktime sound"
date: 2008-05-20
forum: Multimedia Software
---

### Post by waldrepdebater on 2008-05-20
I've had a difficult journey searching for a good video player and I've finally settled on vlc for everything except quicktime videos.  When I try to play quicktime in VLC it freezes, forcing me to use totem.  Totem plays the video part fine, it just has no sound.  I have ubuntu-restricted-extras installed as well as all the other multimedia codecs I could find.  Here is what I need help with:

1. Get sound to work with quicktime on totem.

2. (my final goal or if 1. is not possible) Get audio and visual to work on VLC for quicktime videos.



Some info about my system and background in case it helps:

I am dual-booting ubuntu gutsy with windows vista.  Intel dual-core processor with 512 MB of RAM.  I've been using ubuntu for about 6-8 months and I love it, but I still have a lot to learn.  I am comfortable pasting commands into the terminal and can do basic commands as root but that is where my experience beyond GUI ends.

Thanks in advance.

---

### Post by cor2y on 2008-05-20
which version of totem is it?
If its totem-gstreamer make sure all the gstreamer plugins are installed and w32codecs as well
Ok here are the needed gstreamer plugins
gstreamer0.10-ffmpeg (ffmpeg support)
gstreamer0.10-fluendo-mp3 (mp3 support/playback)
gstreamer0.10-pitfdll (to use the w32codec pack if installed)
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

Optional Plugins
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-fluendo-mpegmux

If you don't see some of these in synaptic you will need to enable the mulitverse, universe, and perhaps restricted repos, then reload

Some quicktime movies use an older or unsupported audio codec that you may need the w32codecs to decode.

---

