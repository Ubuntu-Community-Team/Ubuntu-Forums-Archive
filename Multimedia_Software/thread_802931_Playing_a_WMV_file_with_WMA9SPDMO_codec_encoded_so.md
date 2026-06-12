---
title: "Playing a WMV file with WMA9SPDMO codec encoded sound in totem, not mplayer"
date: 2008-05-21
forum: Multimedia Software
---

### Post by ThomasDM on 2008-05-21
Hello: 

I have a need to watch lectures stored in wmv video files with audio encoded for the WMA9SPDMO codec for school. I can play them fine with mplayer and the win32codecs package, but when I try to play the same files in totem, I get no sound. 

It would be a big help to be able to watch these files in totem, because the totem browser plug-in is compatible with my school's video delivery website, which syncs a slide show to the streaming video, and the mozilla mplayer plug-in is not because it doesn't handle the auto-generated play lists that the website creates. 

Has anyone had success playing wmv files with WMA9SPDMO encoded audio in totem? 

Any instruction on how to set up the ability to do so, or a pointer to where I can find such information would be greatly appreciated.

Many thanks, 

Thomas

---

### Post by cor2y on 2008-05-21
which version of totem? 
Totem-gstreamer or totem-xine?
To find out open totem and select Help->About that will tell you which backend totem is using.
If its totem-gstreamer add the gstreamer0.10-pitfdll plugin this allows totem-gstreamer to use the w32codecs.
Note there is only a 32bit version available non for ubuntu64.
On the totem-xine side be sure to add the libxine1-misc-plugins libxine1-plugins they also can use the w32codecs not to sure if like pitfdll that its only on 32bit ubuntu.

---

### Post by ThomasDM on 2008-05-23
Update: xine-totem seems to support the sound fine, but the gstreamer variant does not. So long as the totem mozilla plugin will work with the xine version, I am happy. I will find this out tomorrow when I am back on my school's local network using their intranet site. 

Out of curiosity, is there a configuration step I am missing to get gstreamer to pick up the right codec?

Thanks for your help.

===================================================================

Thanks for your reply. Lets see what ive got here... Ok, the version of totem is GStreamer 0.10.18. I have the gstreamer0.10-pitfdll package installed (version 0.9.1.1+cvs20080215-1). I am running the 32 bit verison of ubuntu. libxine1-misc-plugins is installed. But still this particular codec (I believe it is the windows media 9 streaming voice codec) seems to give me trouble. 

Would I have better luck with totem-xine? 

Am I correct in assuming that mplayer and gstreamer would be using the same directory from which to load codecs?


> **cor2y said:**
> which version of totem? 
Totem-gstreamer or totem-xine?
To find out open totem and select Help->About that will tell you which backend totem is using.
If its totem-gstreamer add the gstreamer0.10-pitfdll plugin this allows totem-gstreamer to use the w32codecs.
Note there is only a 32bit version available non for ubuntu64.
On the totem-xine side be sure to add the libxine1-misc-plugins libxine1-plugins they also can use the w32codecs not to sure if like pitfdll that its only on 32bit ubuntu.

---

### Post by cor2y on 2008-05-23
yes they look for the w32codecs in the same folder.
Gstreamer plugins i have installed.
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

---

