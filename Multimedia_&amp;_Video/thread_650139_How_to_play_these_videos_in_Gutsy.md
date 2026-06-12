---
title: "How to play these videos in Gutsy"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by parallelogram on 2007-12-25
I want to play videos from WMV HD showcase
[http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx]("http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx")

I downloaded the blue nile video listed there. Uncompressed and tried using VLC, MPlayer, Kaffeine etc. None of them are able to play the video. MPlayer attempted to search for codec and came back saying "codec not found"

I have w32 codecs installed

thanks

---

### Post by ron999 on 2007-12-26
Hi
I'm using Feisty Fawn.
I can't find anything that will play those videos. And my PC is not very high spec.

I downloaded the Nile video and re-encoded it, though when I'd finished it wasn't HD anymore.:lolflag:
But I could then view it using VLC or Totem.

This is the command that I used:-
```
mencoder MysteryOfTheNile.wmv -ofps 25 -ovc xvid -oac mp3lame -srate 48000 -xvidencopts bitrate=700 -o MysteryOfTheNile.avi
```

---

### Post by cor2y on 2007-12-26
if its the vc-1 codec then you will need to compile the svn version of ffmpeg and the latest mplayer source, they worked on the vc-1 decoder integration this summer.

---

