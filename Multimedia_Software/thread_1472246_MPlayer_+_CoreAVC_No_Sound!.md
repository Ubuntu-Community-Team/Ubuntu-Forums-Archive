---
title: "MPlayer + CoreAVC No Sound!"
date: 2010-05-04
forum: Multimedia Software
---

### Post by amacus on 2010-05-04
Hi everyone,

After loads of trying I have finally got MPlayer compiled to work with CoreAVC, following the instructions here and here

[http://www.zimbio.com/Ubuntu+Linux/articles/524/1080p+HDTV+H+264+Playback+Linux](http://www.zimbio.com/Ubuntu+Linux/articles/524/1080p+HDTV+H+264+Playback+Linux)
[http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation](http://code.google.com/p/coreavc-for-linux/wiki/MplayerInstallation)

However, when I play any video, H264 or not, I get no sound! Sound works fine in Banshee, vlc etc

I have included the output from Mplayer below. Have obviously tried turning the volume up and down with keystrokes. Any ideas?

H264
Cache fill:  0.00% (0 bytes)   
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3) "English (AC3)", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/***), -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Forced video codec: coreserve
Opening video decoder: [dshowserver] DirectShowServer video codecs
[PP] Using codec's postprocessing, max q = 4.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [gl_nosw] 1920x1080 => 1920x1080 Planar YV12 
dshowserver --codec CoreAVCDecoder.ax --size 1920x1080 --guid 09571a4b-f1fe-4c60-9760de6d310c7c31 --fourc 0x31637661 --bits 12 --outfmt 0x32315659 --pid 14967 --id ed192730 --numpages 10 --port 31435 &
Starting wine dshowserver.exe
Opening device (port is 31435)
len: 992
ProductVersion: 2.0.0
fixme:thread:SetThreadIdealProcessor (0x78): stub
fixme:thread:SetThreadIdealProcessor (0x7c): stub
fixme:thread:SetThreadIdealProcessor (0x80): stub
fixme:thread:SetThreadIdealProcessor (0x84): stub
Decoder supports the following YUV formats: YUY2 UYVY YV12 I420 
EINPROGRESS in connect() - selecting
Found DirectShow filterSelected video codec: [coreserve] vfm: dshowserver (CoreAVC DShow H264 decoder 1.3 for x86 - [http://corecodec.org/](http://corecodec.org/))
==========================================================================
==========================================================================
Requested audio codec family [a52] (afm=liba52) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
pts value < previousV: -0.191 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 98%                                          
Seek now V:   2.4 A-V:  0.000 ct: -0.042   0/  0 10% 12%  0.5% 1 0 97%                                          
Seek now V:  21.0 A-V: -0.209 ct: -0.041   0/  0 ??% ??% ??,?% 0 0 73%                                          
Seek now V:  33.2 A-V: -0.135 ct: -0.025   0/  0 ??% ??% ??,?% 0 0 47%                                          
Seek now V:  48.7 A-V:  0.083 ct: -0.007   0/  0 ??% ??% ??,?% 0 0 95%                                          
Seek now V:  65.8 A-V: -0.121 ct: -0.025   0/  0 ??% ??% ??,?% 0 0 47%                                          
Seek now V:  86.4 A-V:  0.000 ct: -0.005   0/  0 ??% ??% ??,?% 0 0 95%                                          
Seek now V:  99.6 A-V:  0.008 ct: -0.020   0/  0 ??% ??% ??,?% 0 0 83%                                          
Seek now V: 110.0 A-V:  0.014 ct: -0.019   0/  0 ??% ??% ??,?% 2 0 86%                                          
Seek now V: 121.8 A-V: -0.044 ct: -0.013   0/  0 ??% ??% ??,?% 0 0 49%                                          
Seek now V: 147.7 A-V:  0.000 ct: -0.065   0/  0 12%  8%  0.5% 0 0 49%                                          
Seek now V: 213.7 A-V: -0.044 ct: -0.079   0/  0 36%  9%  0.7% 0 0 92%                                          
No bind found for key '='.                         %  9%  0.6% 0 0 78%                                          
No bind found for key '='.                         %  9%  0.5% 0 0 76%                                          
No bind found for key '='.                         %  9%  0.5% 0 0 75%                                          
No bind found for key '='.                         % 10%  0.5% 4 0 68%                                          
No bind found for key '='.                         % 10%  0.5% 4 0 66%                                          
No bind found for key '='.                         % 10%  0.5% 4 0 64%                                          
No bind found for key '='.                         %  9%  0.5% 6 0 58%                                          
No bind found for key 'b'.                         %  9%  0.5% 7 0 49%                                          
[Mixer] No hardware mixing, inserting volume filter.  9%  0.5% 7 0 49%                                          
No bind found for key ','.                         %  8%  0.5% 7 0 49%                                          
A: 293.0 V: 293.0 A-V: -0.000 ct: -0.189   0/  0 10%  8%  0.5% 7 0 49%                                          
A: 293.0 V: 293.0 A-V:  0.000 ct: -0.189   0/  0 10%  8%  0.5% 7 0 49%                                          
A: 293.1 V: 293.1 A-V:  0.000 ct: -0.189   0/  0 10%  8%  0.5% 7 0 49%                                          
No bind found for key 'l'.                         %  8%  0.5% 7 0 49%                                          
Decoder is capable of YUV output (flags 0x2b)  0  7%  8%  0.5% 7 0 49%                                          
Setting fmt
Starting
Initialization is complete
Using socket based mutex
Dshowserver Connected to host
************
in-frames: 1307 out-frames: 1197
************
Destroying filter
Exiting... (Quit)


AVI
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1024.4 kbps (125.1 kbyte/s)
Clip info:
 Software: transcode-1.0.2
[gl] using extended formats. Use -vo gl:nomanyfmts if playback fails.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [gl_nosw] 624x352 => 624x352 Planar YV12 
A:  21.3 V:  21.3 A-V:  0.005 ct: -0.040 511/511  3%  0%  0.5% 0 0                                              
Exiting... (Quit)

---

