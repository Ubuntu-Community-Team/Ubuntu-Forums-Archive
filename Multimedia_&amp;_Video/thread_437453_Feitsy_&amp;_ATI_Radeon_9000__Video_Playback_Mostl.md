---
title: "Feitsy &amp; ATI Radeon 9000:  Video Playback Mostly Blank"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by thepossiblehuman on 2007-05-08
I'm having a problem with my Feisty install and ATI Radeon 9000 video card where video playback is basically dead.  Whenever I start-up a video in VLC or Movie Player, you'll see the output for a split second before it goes blank.   If you try to resize the screen, the video will flicker on and off while you are resizing, but will die again once you stop.  Occasionally it will stay on, but that is rare.  Audio is fine.  

I have Beryl installed and working perfectly, but this happens regardless of whether Beryl is on or not.  This also happens on all video formats.  

When I start VLC on command line and open a video, I get:
```


** (.:20441): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed

```

When I resize which will cause the video to flicker on, I get:
```

[00000335] main decoder error: decoder is leaking pictures, resetting the heap
[00000336] main video output error: picture 0x86f7a18 refcount is -1

```

Any ideas?  Thanks.

---

### Post by thepossiblehuman on 2007-05-09
Just ran through the How-to for installing multi-media on Feisty, and I'm still getting the same problem here.  I have a second laptop of identical spec that I threw Feisty on as a test-bed, so I just tried on there as well and am getting the same exact behavior.  

Could it be that I'm aiglx instead of fglx?  The proprietary fglx drivers didn't install by default on these boxes, and I'd prefer to use the open source driver for Beryl anyway.

---

### Post by thepossiblehuman on 2007-05-09
Found a solution that works for VLC when I just ran a search regarding video playback issues and aiglx:

[http://ubuntuforums.org/showthread.php?p=2623656#post2623656](http://ubuntuforums.org/showthread.php?p=2623656#post2623656)

It is simple, but it works for 3 of the 4 files I have to test it with.

---

