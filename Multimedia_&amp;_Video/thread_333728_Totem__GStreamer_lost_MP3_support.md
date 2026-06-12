---
title: "Totem / GStreamer lost MP3 support?"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by brian.baggett on 2007-01-07
Greetings!

Today, I tried to play my MP3's with Totem and I'm getting "There is no plugin to handle this type of movie" despite the fact it's been working for months. Anything that doesn't require gstreamer seems to work (e.g. Beep, XMMS, VLC, Audacity, MPlayer, etc.) I'm running Edgy on AMD64. I have the following installed:

gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-fluendo-mpegdemux
gstreamer0.10-gl
gstreamer0.10-gnomevfs
gstreamer0.10-gnonlin
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-sdl
gstreamer0.10-tools
gstreamer0.10-x
gstreamer0.8-a52dec
gstreamer0.8-mpeg2dec
libgstreamer0.10-0
libgstreamer0.8-0
libgstreamer-plugins-base0.10-0
amarok-xine
libxine1
libxine-extracodecs
libxine-main1
totem-xine

Any ideas on why this would suddenly stop working?

Thanks,

Brian

---

### Post by pay on 2007-01-07
You could try the xine backend for totem.```
sudo aptitude install totem-xine
```

---

### Post by brian.baggett on 2007-01-07
As you can see from my initial post, I already have that installed.

---

### Post by pay on 2007-01-07
Opps sorry. Maybe totem gsteamer then ```
sudo aptitude install totem-gstreamer
```

---

### Post by brian.baggett on 2007-01-07
Okay, that worked. I am confused as to what has broken libxine ...

---

### Post by jamespi on 2007-01-10
i have the same problem. i tried installing totem gstreamer, which meant mp3s started playing again, but whenever i touched the volume control on totem, the mp3 just crackled and cut out, so i used automatix to put totem-xine back on and now i'm back to "no plugin to handle this movie"

---

### Post by brian.baggett on 2007-01-10
Glad to know I'm not the only one. In my testing, amarok (which I use in Gnome because I like it better than banshee) is also broken saying it has no MP3 support. I too use Automatix2 but no updates have been applied that are xine related to my knowledge ...

---

### Post by brian.baggett on 2007-01-12
I'm not sure why, but removing my .xine directory from my home directory and then reinstalling totem-xine seems to have cleared it up.

--
Brian

---

### Post by jamespi on 2007-01-14
i found that just deleting the .xine folder worked. that might be because i had already reinstalled xine about 3 times beforehand though.

---

### Post by scawa on 2007-10-13
I did all these things.... still not working

---

### Post by magaltavor on 2008-02-04
[https://help.ubuntu.com/community/RestrictedFormats/MP3#head-70c871ec4e080cee979d182af025821416454c5b](https://help.ubuntu.com/community/RestrictedFormats/MP3#head-70c871ec4e080cee979d182af025821416454c5b)

---

### Post by TryMe on 2008-05-08
> **jamespi said:**
> i found that just deleting the .xine folder worked. that might be because i had already reinstalled xine about 3 times beforehand though.

After installing rezound I got the no plugin error. Deleting the ~/.xine worked. No totem reinstall needed. Thanks guys.

ubuntu 8.04

---

### Post by mike.grabowski on 2008-05-18
No idea what the cause is, but if you use gstreamer instead of xine... deleting the .gstreamer folder in your home dir seems to fix gstreamer if you are having a similar issue.

---

