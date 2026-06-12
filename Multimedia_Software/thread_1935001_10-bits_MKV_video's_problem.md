---
title: "10-bits MKV video's problem"
date: 2012-03-03
forum: Multimedia Software
---

### Post by Teawo on 2012-03-03
Hello everyone, 
I have got a little problem with some videos 10-bits MKV. 
I use mplayer2 either VLC Twoflower.

With VLC, I have that : 

```
VLC media player 2.0.1 Twoflower (revision 2.0.0+git20120301+r121)
[0x97ea1a0] main libvlc: Lancement de vlc avec l'interface par défaut. Utilisez « cvlc » pour démarrer VLC sans interface.
MKV/Ebml Parser: m_el[mi_level] == NULL
MKV/Ebml Parser: Up cannot escape itself
MKV/Ebml Parser: m_el[mi_level] == NULL
MKV/Ebml Parser: Up cannot escape itself
Erreur de segmentation
```

With mplayer2 :

```
Playing video.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "VO", -vid 0
[mkv] Track ID 2: audio (A_AC3) "Original [DVD]", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1024x576  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
A:   0.0 V:   0.0 A-V:  0.000 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 
Unsupported PixelFormat 78
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)
```

But, if i use :```
 mplayer -vo mpeg video.mkv
``` there is the sound but without picture (i'am not sure of this word, maybe it is frame) and the console displays this : 

```
Playing video.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "VO", -vid 0
[mkv] Track ID 2: audio (A_AC3) "Original [DVD]", -aid 0, -alang jpn
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [avc1]  1024x576  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in .
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
```

I do not know if you need other pieces of information. 
Thank you and forgive me if I am not very polite and comprehensible, but the english is not my mother tongue and I am not at ease with this language, nevertheless someone has advised me to ask here :).

---

### Post by andrew.46 on 2012-03-05
Can you post the difficult video somewhere? And perhaps also give your full command and terminal output with MPlayer.

---

