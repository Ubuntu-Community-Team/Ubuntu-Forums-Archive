---
title: "Can't get vdpau working with Nvidia ION"
date: 2010-08-20
forum: Multimedia Software
---

### Post by llamafier on 2010-08-20
This is on a basically fresh installation of Lucid. I've installed the nvidia drivers and added the vdpau PPA.

I used the vdpau setting in smplayer and it wouldn't work at all. Then I installed libvdpau1 and that sorta fixed it, but 1080p videos crash after a couple seconds and I can see frames messing up in lower res stuff, so I don't think it's working.

I get this trying to play a 1080p clip, kinda glitches out for a couple seconds and then crashes.
```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 65012055 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/llama/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -nocache -ss 22 -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/llama/Downloads/killa.sampla.x264.mkv

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/llama/Downloads/killa.sampla.x264.mkv.
Checking for YUV4MPEG2
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] /---- [ parsing seek head ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 23.046s
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Default duration: 41.708ms ( = 23.976 fps)
[mkv] |  + Language: und
[mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[mkv] |  + Track type: Video
[mkv] |  + Video track
[mkv] |   + Pixel width: 1920
[mkv] |   + Pixel height: 1080
[mkv] |   + Display width: 16
[mkv] |   + Display height: 9
[mkv] |  + CodecPrivate, length 42
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Language: und
[mkv] |  + Codec ID: A_AC3
[mkv] |  + Track type: Audio
[mkv] |  + Audio track
[mkv] |   + Channels: 6
[mkv] |   + Sampling frequency: 48000.000000
[mkv] |   + Bit depth: 16
[mkv] |+ found cluster, headers are parsed completely :)
ID_VIDEO_ID=0
[mkv] Aspect: 1.777778
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=und
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/home/llama/Downloads/killa.sampla.x264.mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=1080
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7778
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=23.05
ID_SEEKABLE=1
ID_CHAPTERS=0
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
ID_VIDEO_CODEC=ffh264vdpau
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
ID_AUDIO_BITRATE=448000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=a52
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1920 x 1080 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7778
VO: [vdpau] 1920x1080 => 1920x1080 H.264 VDPAU acceleration 
[ASPECT] Warning: No suitable new res found!
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[Mixer] No hardware mixing, inserting volume filter.
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture
[h264_vdpau @ 0x36bf6c0]Missing reference picture



MPlayer interrupted by signal 11 in module: unknown
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

```


This is something lower res and it doesn't crash:
```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -sub-fuzziness 1 -identify -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 65012055 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/llama/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 1 -subpos 100 -nocache -ss 219 -osdlevel 0 -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/llama/Downloads/Royal.Pains.S02E10.Whole.Lotto.Love.HDTV.XviD-FQM.avi

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/llama/Downloads/Royal.Pains.S02E10.Whole.Lotto.Love.HDTV.XviD-FQM.avi.
AVI file format detected.
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1003.0 kbps (122.4 kbyte/s)
Clip info:
 Software: transcode-1.0.4
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=transcode-1.0.4
ID_CLIP_INFO_N=1
ID_FILENAME=/home/llama/Downloads/Royal.Pains.S02E10.Whole.Lotto.Love.HDTV.XviD-FQM.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=XVID
ID_VIDEO_BITRATE=1003016
ID_VIDEO_WIDTH=624
ID_VIDEO_HEIGHT=352
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=160224
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=2495.12
ID_SEEKABLE=1
ID_CHAPTERS=0
Couldn't open video filter '***'.
***: cannot add video filter
[***] Init
[***] Updating font cache.
==========================================================================
Forced video codec: ffh264vdpau
Forced video codec: ffmpeg12vdpau
Forced video codec: ffwmv3vdpau
Forced video codec: ffvc1vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
ID_VIDEO_CODEC=ffodivx
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=mp3
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.7727
VO: [vdpau] 624x352 => 624x352 Planar YV12 
[Mixer] No hardware mixing, inserting volume filter.

```

---

