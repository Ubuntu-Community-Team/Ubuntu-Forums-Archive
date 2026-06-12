---
title: "reencoding video with low fps (ffmpeg or mencoder)"
date: 2011-05-11
forum: Multimedia Software
---

### Post by kung fu buntu on 2011-05-11
I have a couple of video captures done with recordmydesktop. These desktop captures sometimes also include the playing of videos, such that you can see the time go by in the player.

The problem which I only realized quite latter is that they were capped at 15 fps (or some other low value), using theora format, and because of that when I play then with mplayer the video looks like its being fast forwarded.

I would like to know how can I fix this problem.
My idea would be to have the reencoding tool (ffmpeg or mencoder) duplicate each frame and thus make it look like time flows normally (even though the end result could look like a very fast slideshow). How can I do this?

Any other suggestions?

Thanks

---

### Post by VanillaMozilla on 2011-05-11
> **kung fu buntu said:**
> 
I would like to know how can I fix this problem.
Play it back with a different program?  Don't you wish software would actually work?  Try the VLC player.  That's rather independent of most other media software.  If that plays back at the correct speed, than you can suspect that the other playback program is at fault.  Otherwise, the recording program stored the frame rate incorrectly.

Let's see, how to fix the file?  Check the ffmpeg manual??

---

### Post by no2498 on 2011-05-11
you can set the fps in tragtor
its a fast program

---

### Post by kung fu buntu on 2011-05-11
> **VanillaMozilla said:**
> Play it back with a different program?  Don't you wish software would actually work?  Try the VLC player.  That's rather independent of most other media software.  If that plays back at the correct speed, than you can suspect that the other playback program is at fault.  Otherwise, the recording program stored the frame rate incorrectly.

Let's see, how to fix the file?  Check the ffmpeg manual??
VLC is not any better than mplayer. The same thing happens.
I also tried playing the video with theora_player_example and the playback is still borked.



> **no2498 said:**
> you can set the fps in tragtor
its a fast program
That won't solve the problem. I already tried passing the fps option (-r) with ffmpeg using different values.






I did some more testing and investigation into this issue...

When I mentioned the 15-18 fps I was wrong. It was recorded at 30 fps, however how it was really captured that is another issue because the playback shows that frames are missing (thus the playback looking like it's in fast forward mode).


```
$ mediainfo foo.ogg 
General
ID                               : 1333266807 (0x4F780977)
Complete name                    : foo.ogg
Format                           : OGG
File size                        : 70.2 MiB
Duration                         : 2mn 28s
Overall bit rate                 : 3 966 Kbps
recordMyDesktop                  : 0.3.7.3

Video
ID                               : 1770862840 (0x698D38F8)
Format                           : Theora
Duration                         : 2mn 28s
Bit rate                         : 3 628 Kbps
Nominal bit rate                 : 45.0 Kbps
Width                            : 1 280 pixels
Height                           : 1 024 pixels
Display aspect ratio             : 5:4
Frame rate                       : 30.000 fps
Bits/(Pixel*Frame)               : 0.092
Writing library                  : libTheora 3.2.1 (UTC 2008-10-20)
```

```
$ theora_dump_video < foo.ogg  > foo.dump
Encoded by Xiph.Org libTheora I 20081020 3 2 1
theora comment header:
        recordMyDesktop=0.3.7.3
Ogg logical stream 698d38f8 is Theora 1280x1024 30.00 fps video
Encoded frame content is 1280x1024 with 0x0 offset
4459 frames
Done.
```
148 seconds * 30 frames = 4440 frames
So it confirms the 30 fps


Based on the playback of the capture (which includes a video being played with time) I could conclude that:
133 seconds of real world time were condensed into 101 seconds of desktop capture

So it's possible that these captures are foobared beyond repair.
Even if I could find a way to duplicate each frame that would produce the opposite effect. It would mean 133 seconds of real world being "slowed down" into 202 seconds of playback.
I would need to use decimal slowdown factor, which may not be even possible to get.


Any other ideas?

---

