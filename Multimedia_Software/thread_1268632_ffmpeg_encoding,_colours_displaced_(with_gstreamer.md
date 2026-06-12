---
title: "ffmpeg encoding, colours displaced (with gstreamer)"
date: 2009-09-17
forum: Multimedia Software
---

### Post by anlag on 2009-09-17
First off, sorry for the weird topic, hard to summarize this concisely!

I have been converting a sequence of jpg images into video using ffmpeg with commands similar to this one:

```
ffmpeg -r 2 -f image2 -i 42ff%04d.jpg -vcodec mpeg4 test3.mp4
```

When I play the output video with mplayer (or vlc, or totem-gstreamer) it runs, but all the colours are displaced with respect to the contours. A screenshot to illustrate:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=128878&stc=1&d=1253186969[/IMG]

However, when I play the same video with totem-xine, it looks like it's supposed to:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=128879&stc=1&d=1253186969[/IMG]

The individual jpg images themselves, pre-conversion, of course look fine too.

The fact that it works with totem-xine would seem to incidate it's a gstreamer problem. This seems to be supported by the fact that it plays fine also on my girlfriend's Mac with QuickTime, RealPlayer and DivX Player alike. Also on that machine, it looks weird in VLC, though in a somewhat different way.

Anyhow. I would like to know if I can either change something in the encoding so that it will run fine on gstreamer based players as well, or if I can fix gstreamer or its libraries to eliminate the problem that way.

In an attempt to perhaps reach both those ends, I downloaded the SVN trunk of ffmpeg last night and installed it. If I understand correctly, gstreamer uses the libraries of ffmpeg as well, so it was my hope that this would help it play the video correctly, but unfortunately that is not the case.

Anything else I can do or try? It would be very helpful if I could reliably play these videos on my player of choice, on this machine and others.

Thanks in advance.

---

### Post by anlag on 2009-09-17
Just as an experiment, I tried encoding with mencoder instead:

```
mencoder "mf://42ff*.jpg" -mf fps=2 -o menctest.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=800
```

The same behaviour remains with mplayer/vlc, while this also runs fine with totem-xine.

---

