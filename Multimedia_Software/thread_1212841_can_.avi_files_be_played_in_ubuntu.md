---
title: "can .avi files be played in ubuntu?"
date: 2009-07-14
forum: Multimedia Software
---

### Post by j7%&lt;RmUg on 2009-07-14
Hey guys,

im running 9.04 desktop and would like to know if its even possible to play .avi files in ubuntu at all?

I have been looking for an answer to this problem for 7 months now, but have come up with nothing.

I use VLC and but i still cannot seem to be able to play .avi, ogg, ogg theora or anything along those lines.

It would be great if someone could help me out, im still convinced its possible in jaunty but i have no idea how.

thanks in advance.

---

### Post by Rhubarb on 2009-07-14
Ubuntu by default can play ogg files without any problems (ogg theora and ogg vorbis).

It can also play most other media files easily too.

vlc should be able to play most formats.

My Ubuntu 9.04 plays everything but rm files (real media), and copy protected media files.

If for some reason VLC can't play your media files, then try installing these gstreamer codecs and use the default media player in Ubuntu:-

```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

Remember that an avi file is just a container for video (a poor old container at that), what lies inside that container is what matters - like xvid + mp3.

Anyway, try installing those gstreamer plugins, and let me know if this improves things for you.

---

### Post by j7%&lt;RmUg on 2009-07-14
Thanks heaps, installing those worked for me i can now play avi's, mp4's and divx as well. Im going to find a small ogg video and try that.

Funny thing is while i can get most formats working in mplayer the sound doesnt work in mplayer, only in vlc.

Although i only use vlc so that doesnt matter. Thanks again.

PROBLEM SOLVED

---

### Post by Rhubarb on 2009-07-14
yay \\:D/

You can test out an ogg theora video from your ~/examples directory, or from here:-
/usr/share/example-content/Ubuntu_Free_Culture_Showcase/SpiritOfUbuntu.ogv

---

### Post by j7%&lt;RmUg on 2009-07-14
Ah thanks again, i found them and both .ogg and ogv work in vlc with sound.

---

