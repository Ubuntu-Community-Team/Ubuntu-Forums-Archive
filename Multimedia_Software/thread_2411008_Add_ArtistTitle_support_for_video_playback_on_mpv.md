---
title: "Add Artist/Title support for video playback on mpv"
date: 2019-01-23
forum: Multimedia Software
---

### Post by shantiq on 2019-01-23
This is a follow-up from an [earlier ]("https://ubuntuforums.org/showthread.php?t=2323459&p=13485599#post13485599")thread:

mpv is an astounding tool but does not natively show Artist and Title when performing video/audio playback, fortunately there is an easy way round  >>


```
--fs
--resume-playback
--save-position-on-quit
--screenshot-template=/home/yourname/Pictures/mpv/%F&#9755;%n
--screenshot-format=png
--screenshot-png-compression=9
--sub-text-back-color=0.9/1.0/0.25

# and to see Title of song and artist name when you play a video add

[COLOR=#800000]term-playing-msg='Title: ${media-title}'[/COLOR]
```

to your mpv.conf

This latest embellishment courtesy of ChrisK2 on [URL="https://github.com/mpv-player/mpv/issues/1419"]this page



[/URL][[IMG]https://i.postimg.cc/JDPJkJYF/Screenshot-from-2019-01-23-17-05-02.png[/IMG]]("https://postimg.cc/JDPJkJYF")

---

