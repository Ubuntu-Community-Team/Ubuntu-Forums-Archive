---
title: "messed up .mov files"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by higashi on 2008-01-14
Hi,

I'm using feisty.  I just got this new camera that saves all the video files as .mov files. When I play .mov files, the colour is all messed up!!   Even before i play them, when i just put them onto my computer, i see the little thumbnail which also has very messed up colour. I've tried converting them to something else, but it seems once it becomes a .mov file, the colour is permanently messed up. Is there a way that i can prevent this happening so that all my videos are normal?

---

### Post by benanzo on 2008-01-14
Have you tried offloading the videos to windows or Mac and see if Quicktime will play them normally?

My only suggestion would be to run them through mencoder with the **-idx** switch to rebuild the index (not sure if that will work for this).

```
mencoder BadFile.mov -idx -ovc lavc -oac mp3lame -o Test.avi
```

See if Test.avi plays normally.

---

### Post by cor2y on 2008-01-14
whats the media player you are playing them on?
I have seen this before with out of date codecs and how they are rendered by certain libraries in linux.
Strange enough it was with some early sorenson encoded quicktime files, talking about movies from 1999 when played back in linux the colors were not correct on some media players (totem-xine if i remember correctly) i ran into the problem again with some more recent quicktime encoded files (again with totem-xine) they showed perfectly well in mplayer and ffplay.
So if you have thumbnails in nautilus i am guessing it is totem with the xine library (totem-gstreamer doesn't take thumbnails of multimedia files) that could be the problem xine doesn't quite understand how to correctly decode the video hence the weird colors in the movie. I think its the version of ffmpeg xine uses they like to keep the version they use to a stable one and not one from svn.
Try looking at it with mplayer, see if the weird colors etc are gone.

---

### Post by benanzo on 2008-01-14
Totem will thumbnail videos with the gstreamer backend just fine.  I use totem-gstreamer exclusively and I get thumbnails like normal.

```
man totem-video-thumbnailer
```

Create your own thumbnails!

---

### Post by higashi on 2008-01-19
But any movie player i play them with shows them all messed up! It's like they're saved like that or something.

---

### Post by asmallerbrain on 2008-04-01
I have the same problem.  Looking for a solution --- my friend found one recently so I know it exists.

---

