---
title: "problems with .MKV files"
date: 2010-10-28
forum: Multimedia Software
---

### Post by sgriggly on 2010-10-28
hey all. just downloaded my first .mkv file, and i'm having some trouble getting it to play. 

in "Movie Player", the sound plays fine, but the video freezes and plays one frame for about 5 seconds, gets blocky, then freezes on another frame for a few seconds, etc....

in VLC, i get sound for a few seconds... then the player crashes, and closes/quits itself.

in Mplayer, i get the error message "Error opening/initializing the selected video_out (-vo) device." i click okay, and the player spazzes out with error messages until i close it... 

i've tried installing the latest mplayer codecs, following the instructions posted [HERE]("http://ubuntu.igameilive.com/2009/02/play-rmvb-mkv-files-with-ubuntu-810.html"). i also installed some other lib repositories that were posted on another mkv/ubuntu thread that i can't find now (i know that's not helpful, sorry...) 

help! is appreciated. thanks!

---

### Post by andrew.46 on 2010-10-28
Hi sgriggly,

> **sgriggly said:**
> in Mplayer, i get the error message "Error opening/initializing the selected video_out (-vo) device." i click okay, and the player spazzes out with error messages until i close it... 

Could you try playing the problem file from the commandline using the following syntax:

```
mplayer -v *my_problem_file.mkv*
```

and post the full terminal output here? You will of course have to give the correct filename and path where I have given 'my_problem_file.mkv'.

Andrew

---

### Post by sgriggly on 2010-11-03
sorry for the late response, at&t problems with my connection at home.... here's what i get: 


MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.86GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/dirk/.mplayer/codecs.conf'
Reading /home/dirk/.mplayer/codecs.conf: Can't open '/home/dirk/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --target=i586-linux --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-gui --enable-mencoder
CommandLine: '-v' '/home/dirk/Desktop/DarkKnight.mkv'
init_freetype
get_path('font/font.desc') -> '/home/dirk/.mplayer/font/font.desc'
font: can't open file: /home/dirk/.mplayer/font/font.desc
Bitmap font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/dirk/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/dirk/.mplayer/input.conf'
Can't open input config file /home/dirk/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('DarkKnight.mkv.conf') -> '/home/dirk/.mplayer/DarkKnight.mkv.conf'

Playing /home/dirk/Desktop/DarkKnight.mkv.
get_path('sub/') -> '/home/dirk/.mplayer/sub/'
[file] File size is 1084982253 bytes
STREAM: [file] /home/dirk/Desktop/DarkKnight.mkv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: Matroska file format
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
[mkv] Found the head...
[mkv] + a segment...
[mkv] /---- [ parsing seek head ] ---------
[mkv] /---- [ parsing seek head ] ---------
[mkv] \---- [ parsing seek head ] ---------
[mkv] /---- [ parsing cues ] -----------
[mkv] \---- [ parsing cues ] -----------
[mkv] \---- [ parsing seek head ] ---------
[mkv] |+ segment information...
[mkv] | + timecode scale: 1000000
[mkv] | + duration: 9133.312s
[mkv] |+ segment tracks...
[mkv] | + a track...
[mkv] |  + Track number: 1
[mkv] |  + Track type: Video
[mkv] |  + Default flag: 0
[mkv] |  + Codec ID: V_MPEG4/ISO/AVC
[mkv] |  + CodecPrivate, length 47
[mkv] |  + Default duration: 41.708ms ( = 23.976 fps)
[mkv] |  + Language: und
[mkv] |  + Video track
[mkv] |   + Pixel width: 1280
[mkv] |   + Pixel height: 536
[mkv] |   + Display width: 1280
[mkv] |   + Display height: 545
[mkv] | + a track...
[mkv] |  + Track number: 2
[mkv] |  + Track type: Audio
[mkv] |  + Default flag: 0
[mkv] |  + Codec ID: A_AAC
[mkv] |  + CodecPrivate, length 7
[mkv] |  + Default duration: 42.667ms ( = 23.438 fps)
[mkv] |  + Language: und
[mkv] |  + Audio track
[mkv] |   + Sampling frequency: 24000.000000
[mkv] |   + Channels: 2
[mkv] | + a track...
[mkv] |  + Track number: 3
[mkv] |  + Track type: Subtitle
[mkv] |  + Default flag: 1
[mkv] |  + Codec ID: S_TEXT/***
[mkv] |  + CodecPrivate, length 810
[mkv] |  + Language: und
[mkv] |+ found cluster, headers are parsed completely :)
==> Found video stream: 1
[mkv] Aspect: 2.348624
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
==> Found audio stream: 2
[mkv] Track ID 2: audio (A_AAC), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x536  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:31  fourcc:0x31637661  size:1280x536  fps:23.98  ftime:=0.0417
get_path('sub/') -> '/home/dirk/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1440x900 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
dec_audio: Allocating 4608 bytes for input buffer.
dec_audio: Allocating 49152 + 65536 = 114688 bytes for output buffer.
FAAD: Decoder init done (0Bytes)!
FAAD: Negotiated samplerate: 48000Hz  channels: 2
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
AO: [pulse] Failed to connect to server: Connection refused
alsa-init: requested format: 48000 Hz, 2 channels, 9
alsa-init: using ALSA 1.0.15
alsa-init: setup for 1/2 channel(s)
alsa-init: using device default
alsa-init: pcm opened in blocking mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa-init: got period size 1024
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Video: no video
Freeing 0 unused video chunks.
Starting playback...
A: 146.5 (02:26.5) of 9133.3 ( 2:32:13.3)  3.4% 
  =====  PAUSE  =====

Using this command, the audio plays back flawlessly, but there was no video at all...

---

### Post by andrew.46 on 2010-11-03
Hi sgriggly,

This seems to be the problem:

```

[VO_XV] It seems there is no Xvideo support for your video card available.
[VO_XV] Run 'xvinfo' to verify its Xv support and read
[VO_XV] DOCS/HTML/en/video.html#xv!
[VO_XV] See 'mplayer -vo help' for other (non-xv) video out drivers.
[VO_XV] Try -vo x11.
Error opening/initializing the selected video_out (-vo) device.

```

Perhaps try the suggested option:

```
mplayer -vo x11 /home/dirk/Desktop/DarkKnight.mkv
```

Andrew

---

### Post by kerry_s on 2010-11-03
gnome-mplayer & some extra options.

```
-lavdopts skiploopfilter=all -mc 100
```

---

### Post by sgriggly on 2010-11-03
Hi Andrew,

Thanks for your help so far! 

Yes, your code now gets me the video AND the sound, however, the video is garbled a bit, and "sticks" on a frame, then skips to another frame, etc... 

(I'll also mention that I've copied this same file to my friend's machines, and it has no problem playing on a Mac OR a PC, so I know it's not the file...)

Here's some of the code showing up in my terminal during this error: 


[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow8/928  5% 14%  1.9% 47 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow9/929  5% 14%  1.9% 48 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow0/930  5% 14%  1.9% 48 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow1/931  5% 14%  1.9% 49 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow4/934  5% 14%  1.9% 51 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow6/936  5% 14%  1.9% 52 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow7/937  5% 14%  1.9% 53 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]abs_diff_pic_num overflow9/939  5% 14%  1.9% 54 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]concealing 2720 DC, 2720 AC, 2720 MV errors
[h264 @ 0x89398d0]get_buffer() failed (0 0 1 0xb2760230)  1.9% 55 0 
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!
[h264 @ 0x89398d0]pic->data[0]!=NULL in avcodec_default_get_buffer0 
[h264 @ 0x89398d0]get_buffer() failed (-1 2683 2701 0xa67)
[h264 @ 0x89398d0]decode_slice_header error
[h264 @ 0x89398d0]no frame!
Error while decoding frame!

---

### Post by sgriggly on 2010-11-03
lavdopts: command not found....

---

### Post by SeijiSensei on 2010-11-04
What processor and video card does this computer have?  I haven't encountered a machine recently that couldn't use the "xv" output device, which is considerably superior to the old "x11" driver.  Perhaps you should see if you can update your video driver in Ubuntu.

---

### Post by sgriggly on 2010-11-04
Nividia 6800? it's a Dell Inspiron 9300

---

### Post by SeijiSensei on 2010-11-08
Are you using the proprietary NVIDIA driver?  I had a 6xxx card at one point, and with the proprietary driver I could use the xv video interface.  

I'd also suggest installing smplayer.  It provides an excellent GUI interface for mplayer.  You can select video drivers from a drop-down box.

---

### Post by andrew.46 on 2010-11-13
Hi sgriggly,

Can you post this file somewhere? The h264 errors look a little odd and I would be curious to have a proper look...

Andrew

---

