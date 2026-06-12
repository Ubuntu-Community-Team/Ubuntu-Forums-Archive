---
title: "A question for a mencoder guru"
date: 2011-01-11
forum: Multimedia Software
---

### Post by fmmarzoa on 2011-01-11
Hello,

I've bought an MP4 player that also plays video :popcorn:, but the files should be encoded on a given manner so narrow that I've not been able to do it after a couple of hours trying. :(

Anyway the device comes with a demo video installed, and getting information from it reveals that it has been encoded using mencoder: :o

```
Playing /media/disk/Energy Sistem - The heart of your music.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  320x240  12bpp  20.000 fps  501.6 kbps (61.2 kbyte/s)
Clip info:
 Software: MEncoder 1.0rc2-4.2.1
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=MEncoder 1.0rc2-4.2.1
ID_CLIP_INFO_N=1
ID_FILENAME=/media/disk/Energy Sistem - The heart of your music.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=501640
ID_VIDEO_WIDTH=320
ID_VIDEO_HEIGHT=240
ID_VIDEO_FPS=20.000
ID_VIDEO_ASPECT=1.2500
ID_AUDIO_FORMAT=80
ID_AUDIO_BITRATE=304
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=104.25
ID_SEEKABLE=1
ID_CHAPTERS=0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mp3
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.2500
VO: [xv] 320x240 => 320x256 Planar YV12 
A:1309.9 V:   3.2 A-V:1306.727 ct:  0.315  64/ 64  5%  0%  1.1% 1 0 
```

I've tried to encode a new video file with exactly the same parameters, but I've not been able to do so. I didn't find ffodivx codec, among other things. :confused: :confused: :confused:

So, is there any **mencoder guru** that may help me? :D

Thanks a lot in advance,

---

### Post by BicyclerBoy on 2011-01-11
ffmpeg project is author of libavformat libavcodec etc..

mplayer.hu is the project were mencoder is derived.

Their websites etc could help.

---

### Post by FakeOutdoorsman on 2011-01-11
What device is this? Can you also show the FFmpeg output?
```
ffmpeg -i '/media/disk/Energy Sistem - The heart of your music.avi'
```
It can often be a challenge getting a working video for picky devices.

---

### Post by fmmarzoa on 2011-01-21
Actually I've managed to solve this installing and running the converter application that comes with the device on a Windows XP box, and watching the processes to see how it calls mencoder.

I've published it with more detail on my blog for the record:

[http://marzoa.com/2011/01/21/ubuntu-linux-encoding-videos-for-energy-sistem-mp4-devices/](http://marzoa.com/2011/01/21/ubuntu-linux-encoding-videos-for-energy-sistem-mp4-devices/)

---

### Post by andrew.46 on 2011-01-21
The sticking point with many of these devices is b-frames so you may find that the magic setting is *max_bframes=0*, as you have used it in your MEncoder string. You could try a similar command with FFmpeg utilising the equivalent *-bf 0* + the successful codecs and bitrates.

Andrew

---

