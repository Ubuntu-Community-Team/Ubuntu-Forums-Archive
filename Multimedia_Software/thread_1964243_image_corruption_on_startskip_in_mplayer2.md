---
title: "image corruption on start/skip in mplayer2"
date: 2012-04-23
forum: Multimedia Software
---

### Post by pickarooney on 2012-04-23
Whenever I play an .mp4 file in (s)mplayer2 the first few frames are all pixelated and the same happens when I skip forward to another part of the file. It doesn't seem to happen with .avi files in mplayer2 nor does it happen with any filetype in xine or vlc. 

From the command line I get the following messages during playback

```
[h264 @ 0x88f1940]reference picture missing during reorder
[h264 @ 0x88f1940]Missing reference picture

```

---

### Post by pickarooney on 2012-04-24
I tried playing with the various loop filter settings in smplayer but to no effect.

---

### Post by SeijiSensei on 2012-04-24
The error suggests that the initial "reference frame" is missing in the video.  Algorithms like H.264 compress video by tagging a frame periodically as a reference point, then storing only the differences between the reference frame and the current frame.  If you don't have the reference frame, then there's no baseline from which the subsequent frames can be created.

Now I have no idea why the files you have seem to be missing their initial reference frames, or why it's limited to the mp4 container.  Perhaps your AVI files have DivX- or XviD-encoded video while the mp4 files use H.264?  (AVI and mp4 are just "containers" to hold the encoded audio and video streams; what matters are the codecs used to create those streams.) 

What happens if you replace mplayer2 with standard mplayer?  If you play the file from the command line with the command "mplayer /path/to/file.mp4" you'll see a fairly detailed listing about the characteristics of the file and what mplayer is using to display it.

The fact that you also have this problem when you navigate through the video makes me think there was a problem in the creation of these files.  Where did the .mp4 files come from?

---

### Post by pickarooney on 2012-04-25
The files are fine and from a reliable source. They play perfectly in other players (xine, vlc) and other devices (phone, tablet, Windows PC).

I'm not sure how to revert to the old mplayer but with mplayer /path/to/myfile.mp4 I get 

```

MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Loading extension-related profile 'extension.mp4'

Playing myfile.mp4.
Detected file format: Quicktime/MOV
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [avc1]  720x404  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
waitpid(): No child processes
AO: [pulse] Init failed: Internal error
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
[AO_ALSA] Unable to find simple control 'Master',0.
Starting playback...
[h264 @ 0x88edc20]reference picture missing during reorder
[h264 @ 0x88edc20]Missing reference picture
[h264 @ 0x88edc20]reference picture missing during reorder
[h264 @ 0x88edc20]Missing reference picture
[h264 @ 0x88edc20]mmco: unref short failure
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x404 => 720x404 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
A:   2.8 V:   2.9 A-V:  0.000 ct: -0.000  70/ 70 10% 18%  0.6% 0 0 

```

---

### Post by SeijiSensei on 2012-04-25
I searched Google for the specific error text "[h264 @ 0x88edc20]reference picture missing during reorder", and all the references I found concern the absence of an initial "I-frame".  I saw a couple of different alternatives that can lead to this result.  One is that the file was edited and the initial I-frame dropped in the process.  Another concerned CPU speed.  I doubt the latter applies in your case since you're playing the file through vdpau.

What happens if you use xv as the video output driver instead of vdpau?  Try "mplayer -vo xv /path/to/myfile.mp4".  Any different?

Maybe the other players are more tolerant than mplayer2/ffmpeg (ffmpeg provides the library doing the decoding here). I don't really know what else to suggest.

---

### Post by pickarooney on 2012-04-26
I found a method for regressing to mplayer from mplayer2 and now playback is perfect. Odd, but I guess one of the 'improvements' in mplayer2 does not play nicely with my system. I've been usin xv as the output driver with both versions of mplayer BTW.

Thanks for the help :)

---

