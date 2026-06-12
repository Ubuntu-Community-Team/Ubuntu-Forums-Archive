---
title: "I need help with video file conversion."
date: 2009-12-09
forum: Multimedia Software
---

### Post by blackdalek on 2009-12-09
I made a video years ago on a windows machine using an analogue video capture card with hardware video codecs (Pinnacle Studio DC10 motion jpeg board).

I had not been able to play this video at all since moving to linux, but just recently I upgraded to karmic and now my old video plays again (albeit squashed vertically) in the Totem Movie Player app.

I can't remember what settings I used to create the file, but the file is MASSIVE (several gigabytes for about 20 minutes of video). I want to re-encode the video so that the file is a more sensible size and the frame size is restored to the correct 4:3 ratio.

I've been trying Avidemux, but so far I have had no luck. The best I can get is a very jerky movement video - for some reason I can find no way for avidemux to read the second set of video fields properly... one set comes out fine but the other set of fields comes out in grey or not at all.

IF someone could look at a small second of my video, perhaps you can tell me what I need to do to fix the whole video?

video is here - [ftp://ftp.alloraadvertiser.com/public_ftp/revenge2.avi](ftp://ftp.alloraadvertiser.com/public_ftp/revenge2.avi)

Thank you,

---

### Post by garryknight on 2009-12-09
The file seems to be zero bytes. And when I go to  [ftp://ftp.alloraadvertiser.com/public_ftp/]("ftp://ftp.alloraadvertiser.com/public_ftp/revenge2.avi"), there doesn't seem to be anything there.

---

### Post by jmore9 on 2009-12-09
winff should work for you.  Easy to use, and has choices.  It is in the repos

---

### Post by sandy8925 on 2009-12-15
Haven't you ever tried using mplayer to play the video ?

---

### Post by blackdalek on 2009-12-15
It seems the file didn't upload properly, so I have now re-uploaded it.

video is (hopefully) here - [http://www.alloraadvertiser.com/video/revenge2.avi](http://www.alloraadvertiser.com/video/revenge2.avi)

The problem is not that it won't play.
The problem is that a 20 minute video is taking up almost 5.5Gb of space and I want to re-encode it to a more sensible size.

In the mean time, I will see if I can find out what this winff is.

Thank you.

---

### Post by blackdalek on 2009-12-15
winff converted the audio but failed to make any kind of video. The video window is just empty black.

---

### Post by garryknight on 2009-12-15
You could try something like this:
ffmpeg -aspect 4:3 revenge2.avi revenge2.mp4
Do 'man ffmpeg' on the command line for more options.

---

### Post by FakeOutdoorsman on 2009-12-16
I looked at this video and it appears to be broken or corrupt.  FFmpeg and MPlayer were unable to decode it with my quick tests.  It will play with MPlayer for just a second or so, but then fail with numerous messages, "EOI missing, emulating".  I tried the *-ni* and *-forceidx* options with MPlayer and neither helped.  Maybe I overlooked something, and some tests with non-libavcodec decoders/players may yield better results.

Perhaps *avifix* from the **transcode-utils** package will be useful.  I'm doubful, but it is certainly worth a try.

---

### Post by blackdalek on 2009-12-19
> **FakeOutdoorsman said:**
> It will play with MPlayer for just a second or so, but then fail with numerous messages, "EOI missing,...

It only plays for a second because I used avidemux to trim a clip from the video to upload for testing. Even though the file is around 10Mb in size, it is only 1 second of video.

I can only get it to play in totem player. I tried playing the 1 second clip with mplayer from console but did not seem to get the same errors as you. The video of course did not play - just ended up with an empty player window for 1 second, and this in console -
```

Playing revenge2.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  720x540  24bpp  25.000 fps  43460.7 kbps (5305.3 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[mjpeg @ 0x4f45780]mjpeg: using external huffman table
[mjpeg @ 0x4f45780]mjpeg: error using external huffman table, switching back to internal
Unsupported PixelFormat -1
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 544 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0xa2d240]BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0xa2d240]using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0xa2d240]using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0xa2d240]using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0xa2d240]720x544 -> 720x544
VO: [xv] 720x544 => 720x544 Planar YV12 
A:   1.3 V:   1.3 A-V:  0.000 ct: -0.000  34/ 34 59%  0%  4.1% 0 0 
Broken frame at 0x6D62                                                  
A:   1.6 V:   1.8 A-V: -0.165 ct: -0.009  45/ 45 59%  0%  3.2% 0 0 

Exiting... (End of file)
```

avifix didn't seem to do anything useful.

---

### Post by vaiocomputer on 2009-12-19
What did you use to play it in Windows?  In Windows 7 RC I tried it with Windows Media Player and it was just a black screen (although I do have CCCP installed).  I tried it with Quicktime and it didn't work either.

---

### Post by blackdalek on 2009-12-25
> **vaiocomputer said:**
> What did you use to play it in Windows?  In Windows 7 RC I tried it with Windows Media Player and it was just a black screen (although I do have CCCP installed).  I tried it with Quicktime and it didn't work either.

I don't remember what I used to play it. It was probably whatever the normal media player was for Windows 98SE.

I think it needed the Pinnacle card installed in a Windows computer to be able to play it in Windows. The video was originally encoded using a hardware video codec which was built into the Pinnacle capture card. Usually I would have to re-encode the video to be able to play it in another computer. I just never got around to converting it before I deleted Windows.

For some reason Ubuntu seems to play the video with some success without the Pinnacle card being present, so I assume I must have some video codec installed which is at least partially compatible with Pinnacle's hardware codec.

---

