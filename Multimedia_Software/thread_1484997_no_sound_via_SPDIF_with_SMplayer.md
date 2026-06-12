---
title: "no sound via S/PDIF with SMplayer"
date: 2010-05-16
forum: Multimedia Software
---

### Post by snoozy23 on 2010-05-16
Hello, i have a Point of View ION 330 mainboard with a NVIDIA  Soundchip:


```

**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: NVidia [HDA NVidia], Gerät 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: NVidia [HDA NVidia], Gerät 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: NVidia [HDA NVidia], Gerät 3: NVIDIA HDMI [NVIDIA HDMI]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

```


I like to play DTS over S/PDIF 



i have allready done this:


```

sudo add-apt-repository ppa:nvidia-vdpau/ppa

sudo apt-get install libvdpau-dev libvdpau1 nvidia-195-kernel-source nvidia-195-modaliases nvidia-glx-195 nvidia-settings mplayer-nogui smplayer

sudo apt-get install smplayer

sudo aptitude install libavcodec-unstripped-52 libavutil-unstripped-49

```


If I select "Sound through S/PDIF" in the SMplayer it crashes.


here is the log of MPlayer:


```

/usr/bin/mplayer -noquiet -nofs -nomouseinput -vc ffh264vdpau,ffmpeg12vdpau,ffwmv3vdpau,ffvc1vdpau, -afm hwac3 -sub-fuzziness 1 -identify -msglevel demux=6 -slave -vo vdpau -ao pulse -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 71303505 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/snoozy/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -vid 0 -aid 0 -subpos 100 -cache 2000 -ss 856 -osdlevel  -vf-add screenshot -vf-clr -slices -channels 2 -softvol -softvol-max 110 /media/0AD8BBB8D8BBA07D/Filme/fluch.2.1080p.LogicBomb/fluch.der.karibik.2.2006.German.DTS.DL.1080p.BluRay.x264.mkv

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/0AD8BBB8D8BBA07D/Filme/fluch.2.1080p.LogicBomb/fluch.der.karibik.2.2006.German.DTS.DL.1080p.BluRay.x264.mkv.

Cache fill:  0.00% (0 bytes)   
Checking for YUV4MPEG2
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 9039.040s
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Track type: Video
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[mkv] |  + CodecPrivate, length 39
[mkv] |  + Default duration: 41.708ms ( = 23.976 fps)
[mkv] |  + Language: eng
[mkv] |  + Video track
[mkv] |   + Pixel width: 1920
[mkv] |   + Pixel height: 800
[mkv] |   + Display width: 12
[mkv] |   + Display height: 5
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: A_DTS
[mkv] |  + Language: ger
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 48000.000000
[mkv] |   + Channels: 6
[mkv] | + a track...
[mkv] |  + Track number: 3
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 0
[mkv] |  + Codec ID: A_AC3
[mkv] |  + Default duration: 32.000ms ( = 31.250 fps)
[mkv] |  + Language: eng
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 48000.000000
[mkv] |   + Channels: 6
[mkv] |+ found cluster, headers are parsed completely :)
ID_VIDEO_ID=0
[mkv] Aspect: 2.400000
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
ID_AUDIO_ID=0
ID_AID_0_LANG=ger
[mkv] Track ID 2: audio (A_DTS), -aid 0, -alang ger
ID_AUDIO_ID=1
ID_AID_1_LANG=eng
[mkv] Track ID 3: audio (A_AC3), -aid 1, -alang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
ID_FILENAME=/media/0AD8BBB8D8BBA07D/Filme/fluch.2.1080p.LogicBomb/fluch.der.karibik.2.2006.German.DTS.DL.1080p.BluRay.x264.mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1920
ID_VIDEO_HEIGHT=800
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=2.4000
ID_AUDIO_FORMAT=8193
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=9039.04
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
Trying to force audio codec driver family hwac3...
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 1536000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 1536.0 kbit/100.00% (ratio: 192000->192000)
ID_AUDIO_BITRATE=1536000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [hwdts] afm: hwac3 (DTS through S/PDIF)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian AC3 not yet supported 
[libaf] Reinitialization did not work, audio filter 'format' returned error code -2
Couldn't find matching filter/ao format!
ID_AUDIO_CODEC=hwdts
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
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

---

### Post by sailor420 on 2010-07-07
I just had a similar problem, and here's what I did to fix it:

1. Change the driver to ALSA in smplayer config. Pulse doesn't support spdif passthrough from what I can tell.
2. Disable all audio filters in smplayer: uncheck the boxes "Enable the audio equalizer", "global volume", "use software volume control" and "volume normalization by default".

This fixed my issues. Good luck!

---

### Post by fi2 on 2010-07-08
I had the same problem and ALSA worked to me too. But I found my V1.021 ALSA driver (Ubuntu 10.04) did not support surround sound, neither stereo on a surround system. About 1.023 upgrade I found isntructions here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Now it sounds beautiful.

---

