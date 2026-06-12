---
title: "No audio in videos taken with my mobile"
date: 2008-12-01
forum: Multimedia Software
---

### Post by iampriteshdesai on 2008-12-01
I have noticed that when I try to play videos taken with my mobile Ubuntu doesnt play sound, but shows the video. How can I listen to the audio?
I tried Banshee, VLC, Totem but no sound.
In windows too VLC didn't play sound but showed the video.
I could hear sound in Quicktime in windows.
My mobile captures video in .3GP format and I have a haunch that the audio is encoded in .AMR format.
Please help...

---

### Post by andrew.46 on 2008-12-21
Hi,

I suspect you are exactly right. I have a fairly typical 3gp file that I keep for testing:

```
    Stream #0.0(und): Video: h263, yuv420p, 176x144 [PAR 12:11 DAR 4:3], 15.00 tb(r)
    Stream #0.1(und): Audio: libamr_nb, 8000 Hz, mono, s16

```

And you can see there is an h263 video stream and amr narrowband sound. Most, if not all, Ubuntu does not come with amr support but you can compile software like ffmpeg and MPlayer against these libraries and then play the files and convert to other formats. Some examples on these forums:

**ffmpeg:**
[http://ubuntuforums.org/showpost.php?p=6320667&postcount=9](http://ubuntuforums.org/showpost.php?p=6320667&postcount=9)

**MPlayer:**
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

Hope this helps?

Andrew

---

