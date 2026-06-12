---
title: "Problems with re-encoding videos in ogg and ogv formats"
date: 2009-05-10
forum: Multimedia Software
---

### Post by kung fu buntu on 2009-05-10
I used recordmydesktop to capture some desktop sessions. The file is saved as ogg with krecordmydesktop and ogv with gtk-recordmydesktop; I have used both tools.

I'm trying to encode those files (so they use less disk space) and the only tool I've found that works is [handbrake]("http://handbrake.fr/"); avidemux fails with ogg or ogv files.
The problem is that the file ends up messed up, in fact, I think it's messed up from the start.

When I open the original file in kaffeine (other players don't work well with ogg files) it tells me the file is 24 minutes long, but I can only seek at about 16 minutes, which is when the video ends (so it could be some frame issue).
When I open the original file in smplayer, I can't seek, and it tells me the it's using theora as video codec and fps is 30.
When I open the original fiel in handbrake for encoding it, it says the file is 24m long.

After encoding the file to x264 in .mp4 container, I can open it:
- avidemux tells me it's 16m long;
- smplayer and it thinks the file is 24m, but I can only seek to 16m (so I can't click on the 16-24m part of the seek bar);
- kaffeine says the file is 24m, I can seek all the way, but when I'm at the end it still says 8 minutes are still missing to the end of play, so the in practice the file is 16m as well. This is what happens too with the original file.

BTW, even the original file looks a bit weird, like it had incorrect frame rate. This could be due to the capture tool and possible frame skip.

What can I do to fix and re-encode my file to x264 or xvid?
Maybe getting the number of frames and changing that value (slowing down the video) while re-encoding it manually with ffmpeg?

Thanks for any help.



EDIT: I have checked my files with [mediainfo]("http://mediainfo.sourceforge.net/en/Download") and with ```
mediainfo --Inform="Video;%FrameCount%" $inputfile
``` I could see that the original ogg file has about 44000 frames, while the encoded mp4 file has about 29000 frames. =/
How do I fix this mess?

---

### Post by kung fu buntu on 2009-05-11
anybody?

---

### Post by rvm4000 on 2009-05-11
> **kung fu buntu said:**
> - smplayer and it thinks the file is 24m, but I can only seek to 16m (so I can't click on the 16-24m part of the seek bar);

If you still have installed the old mplayer 1.0rc2, I suggest to update:

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by kung fu buntu on 2009-05-11
I'm using Debian (and using debian multimedia packages) and I have:
mplayer 1.0.rc2svn20090508
libavcodec 0.5+svn20090508
libtheora 1.0 (although when the recordings were made I was using 0.2 or something like that)
smplayer 0.6.7

Checking mplayer log, from the smplayer menu, this seemed relevant:
> Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x7f160a69b6e0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1280 x 1024 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.2500
[swscaler @ 0x7f1609aef040]No accelerated colorspace conversion found.
[swscaler @ 0x7f1609aef040]using unscaled yuv420p -> rgb24 special converter
VO: [xv] 1280x1024 => 1280x1024 Planar YV12 
[ASPECT] Warning: No suitable new res found!
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))


---

### Post by kung fu buntu on 2009-06-04
anybody?


(I have such a great talent in starting threads that nobody can answer :p)

---

