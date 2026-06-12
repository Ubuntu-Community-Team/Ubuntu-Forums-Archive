---
title: "Problem with watching TS stream"
date: 2008-07-30
forum: Multimedia Software
---

### Post by rado2402 on 2008-07-30
Hi,

we have TV stream in .ts format. I have problem with watching the stream. In windows works everything OK but in Ubuntu it plays about 1 minute and then crashes...Some examples(outputs):

vlc [http://10.254.7.2:2000](http://10.254.7.2:2000)
VLC media player 0.8.6e Janus
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 66
[00000283] main playlist: nothing to play


mplayer [http://10.254.7.2:2000](http://10.254.7.2:2000)
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://10.254.7.2:2000](http://10.254.7.2:2000).
Resolving 10.254.7.2 for AF_INET6...
Couldn't resolve name for AF_INET6: 10.254.7.2
Connecting to server 10.254.7.2[10.254.7.2]: 2000...
Cache size set to 2000 KBytes
Cache fill: 14.80% (303104 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
TS file format detected.
VIDEO H264(pid=69) AUDIO MPA(pid=68) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 25.000000
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 544 x 436 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 544x436 => 580x436 Planar YV12  [zoom]
[swscaler @ 0x8934890]SwScaler: using unscaled yuv420p -> rgb32 special converter
Cannot sync MAD frame-V:  0.037 ct: -0.839 975/975  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame
Cannot sync MAD frame-V: -0.040 ct: -0.843 976/976  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.039 ct: -0.839 977/977  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.042 ct: -0.843 978/978  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.041 ct: -0.839 979/979  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.001 ct: -0.840 980/980  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.000 ct: -0.840 981/981  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.043 ct: -0.844 982/982  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.040 ct: -0.840 983/983  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.041 ct: -0.844 984/984  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.038 ct: -0.840 985/985  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.000 ct: -0.840 986/986  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.062 ct: -0.844 987/987  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.023 ct: -0.846 988/988  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.101 ct: -0.850 989/989  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.181 ct: -0.854 990/990  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.138 ct: -0.858 991/991  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.260 ct: -0.862 992/992  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.212 ct: -0.866 993/993  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.333 ct: -0.870 994/994  7%  8%  0.8% 0 0 0% 
A:58834.9 V:58835.3 A-V: -0.333 ct: -0.874 994/994  7%  8%  0.8% 0 0 0% 
GNOME screensaver enabled

Exiting... (End of file)


Can anyone help? I cant figure out whats the problem. Has anyone some idea?

Sorry for my english

---

### Post by rado2402 on 2008-07-31
> **rado2402 said:**
> Hi,

we have TV stream in .ts format. I have problem with watching the stream. In windows works everything OK but in Ubuntu it plays about 1 minute and then crashes...Some examples(outputs):

vlc [http://10.254.7.2:2000](http://10.254.7.2:2000)
VLC media player 0.8.6e Janus
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 0) for PID 66
[00000283] main playlist: nothing to play


mplayer [http://10.254.7.2:2000](http://10.254.7.2:2000)
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://10.254.7.2:2000](http://10.254.7.2:2000).
Resolving 10.254.7.2 for AF_INET6...
Couldn't resolve name for AF_INET6: 10.254.7.2
Connecting to server 10.254.7.2[10.254.7.2]: 2000...
Cache size set to 2000 KBytes
Cache fill: 14.80% (303104 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
TS file format detected.
VIDEO H264(pid=69) AUDIO MPA(pid=68) NO SUBS (yet)!  PROGRAM N. 1
FPS seems to be: 25.000000
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 544 x 436 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [x11] 544x436 => 580x436 Planar YV12  [zoom]
[swscaler @ 0x8934890]SwScaler: using unscaled yuv420p -> rgb32 special converter
Cannot sync MAD frame-V:  0.037 ct: -0.839 975/975  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame
Cannot sync MAD frame-V: -0.040 ct: -0.843 976/976  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.039 ct: -0.839 977/977  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.042 ct: -0.843 978/978  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.041 ct: -0.839 979/979  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.001 ct: -0.840 980/980  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.000 ct: -0.840 981/981  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.043 ct: -0.844 982/982  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.040 ct: -0.840 983/983  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.041 ct: -0.844 984/984  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.038 ct: -0.840 985/985  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V:  0.000 ct: -0.840 986/986  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.062 ct: -0.844 987/987  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.023 ct: -0.846 988/988  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.101 ct: -0.850 989/989  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.181 ct: -0.854 990/990  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.138 ct: -0.858 991/991  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.260 ct: -0.862 992/992  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.212 ct: -0.866 993/993  7%  8%  0.8% 0 0 0% 
Cannot sync MAD frame-V: -0.333 ct: -0.870 994/994  7%  8%  0.8% 0 0 0% 
A:58834.9 V:58835.3 A-V: -0.333 ct: -0.874 994/994  7%  8%  0.8% 0 0 0% 
GNOME screensaver enabled

Exiting... (End of file)


Can anyone help? I cant figure out whats the problem. Has anyone some idea?

Sorry for my english

Pliiz help

---

