---
title: "Handling .3GPP files"
date: 2010-05-03
forum: Multimedia Software
---

### Post by amillionsheep on 2010-05-03
VLC does not play this file type and I can't seem to find some documentation on converting it. Can I use ffmpeg? Is there a player out there, or can I get a plugin for popular media players?

Thanks.

---

### Post by mc4man on 2010-05-03
Taking a guess that you may be using karmic there would be a couple of ways for .3gp or .3gpp/3gpp2 files
(gstreamer in lucid now supports, not so in karmic
Using this ppa to update karmic's gstreamer plugins will allow playback in totem (and add wmap (wma3pro support

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

Then 
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly

```

mplayer can also playback, a front end like smplayer or gnome-mplayer if a gui is desired - the repo mplayer may not support, never used, but there are many ppa's with mplayer

vlc can if it's built off of a ffmpeg version that supports decoding - you'd probably need to build vlc yourself

ex. of vlc
> doug@doug-laptop:~$ vlc '/home/doug/Downloads/sample_3GPP2.3g2'
clipped
0xb7201e80] avcodec decoder debug: libavcodec initialized (interface 0x344200)
[0xb7201e80] avcodec decoder debug: ffmpeg codec (AMR narrow band) started


Best bet - get support for totem and gstreamer, then mplayer if desired

---

