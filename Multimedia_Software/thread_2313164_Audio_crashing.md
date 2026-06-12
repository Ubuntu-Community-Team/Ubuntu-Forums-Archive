---
title: "Audio crashing"
date: 2016-02-10
forum: Multimedia Software
---

### Post by leodp on 2016-02-10
Hi all,

since I upgraded to Ubuntu 15.10 I experience crashes and lockups on certain videos (typically on mplayer and VLC).
In the following lines I'll explain the situation, then I'll post debug info

1) Prerequisite for the audio to work is: pavucontrol must be launched and open.

2) When I select the Output: Digital surround 5.1 IEC958/AC3 - optical SPDIF connection
- Most of the videos work, stereo is correctly upscaled when source has only 2 channels, 5.1 cchannels sources work ok.
- Some other videos crash.

3) When I select the Output: Digital stereo IEC958/AC3 - optical SPDIF connection
- Videos which were working on 5.1 output continue working
- Videos which were crashing on 5.1 output are now almost working. After ~30 sec of play they freeze for a few seconds, then resume play

4) If a video which crashes on 5.1 is playing on stereo, then as soon as I change the output to digital 5.1 the video freezes.

5) Analog outputs work without problem, so I guess the issue is with the IEC958 encoding/re-encoding or whatever the card does


I have followed the sound troubleshooting guide 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
including the command:
```

sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*;  sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`

```
(removed ubuntu-support-status which does not work)
and also installed the daily build: oem-audio-hda-daily-lts-wily-dkms_0.201602091746~ubuntu14.04.1_all.deb
but still no solution.

Can anybody suggest me how to proceed?
Thanks,
leodp



This is the output of mplayer from start to crash:
```

 mplayer -v   When.Youre.Strange.LIMITED.BDRip.XviD-SUBMERGE.avi 
Reading config file /etc/mplayer/mplayer.conf
: No such file or directory
get_path('') -> '/home/casa/.mplayer/'
get_path('config') -> '/home/casa/.mplayer/config'
Reading config file /home/casa/.mplayer/config
MPlayer2 2.0-728-g2c378c7-4build1 (C) 2000-2012 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz (Family: 6, Model: 60, Stepping: 3)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
Compiled against libavutil version 54.27.100
Compiled against libavcodec version 56.41.100
Compiled against libavformat version 56.36.100
Compiled against libswscale version 3.1.101
get_path('codecs.conf') -> '/home/casa/.mplayer/codecs.conf'
No optional codecs config file: /home/casa/.mplayer/codecs.conf
No optional codecs config file: /etc/mplayer/codecs.conf
163 audio & 363 video codecs
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-translation --enable-debug=3 --extra-ldflags=-Wl,--as-needed --enable-runtime-cpudetection
CommandLine: '-v' 'When.Youre.Strange.LIMITED.BDRip.XviD-SUBMERGE.avi'
get_path('fonts') -> '/home/casa/.mplayer/fonts'
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/casa/.mplayer/fonts'
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 1.0.1 (COMPLEX)
[ass] Initialized
get_path('fonts') -> '/home/casa/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/casa/.mplayer/subfont.ttf'
[ass] Adding memory font 'OSD'
[ass] Updating font cache
Using nanosleep() timing
get_path('input.conf') -> '/home/casa/.mplayer/input.conf'
Cannot open file '/home/casa/.mplayer/input.conf': No such file or directory
Failed to open /home/casa/.mplayer/input.conf.
Can't open input config file /home/casa/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.
Can't open input config file /etc/mplayer/input.conf.
Falling back on default (hardcoded) input config
Setting up LIRC support...
Failed to open LIRC support. You will not be able to use your remote control.
get_path('When.Youre.Strange.LIMITED.BDRip.XviD-SUBMERGE.avi.conf') -> '/home/casa/.mplayer/When.Youre.Strange.LIMITED.BDRip.XviD-SUBMERGE.avi.conf'

Playing When.Youre.Strange.LIMITED.BDRip.XviD-SUBMERGE.avi.
get_path('sub/') -> '/home/casa/.mplayer/sub/'
[file] File size is 733908992 bytes
STREAM: [file] When.Youre.Strange.LIMITED.BDRip.XviD-SUBMERGE.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: AVI (Audio Video Interleaved)
Detected file format: AVI (Audio Video Interleaved) (libavformat)
==> Found video stream: 0
======= VIDEO Format ======
  biSize 82
  biWidth 624
  biHeight 352
  biPlanes 0
  biBitCount 12
  biCompression 1446269005='MP4V'
  biSizeImage 329472
Unknown extra header dump: [0] [0] [1] [b0] [f5] [0] [0] [1] [b5] [9] [0] [0] [1] [0] [0] [0] [1] [20] [8] [86] [87] [ff] [fb] [a] [ad] [89] [c2] [16] [a] [31] [0] [0] [1] [b2] [58] [76] [69] [44] [30] [30] [35] [30] 
===========================
[lavf] stream 0: video (mpeg4), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 85 (0x55)
Channels: 2
Samplerate: 48000
avg byte/sec: 15841
Block align: 1152
bits/sample: 0
cbSize: 12
mp3.wID=1
mp3.fdwFlags=0x0
mp3.nBlockSize=381
mp3.nFramesPerBlock=1
mp3.nCodecDelay=0
==========================================================================
[lavf] stream 1: audio (mp3), -aid 0
LAVF: 1 audio and 1 video streams found
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 1.0.1 (COMPLEX)
[ass] Initialized
get_path('fonts') -> '/home/casa/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/casa/.mplayer/subfont.ttf'
[ass] Updating font cache
[V] filefmt:41  fourcc:0x5634504D  size:624x352  fps:23.976  ftime:=0.0417
Clip info:
 encoder: VirtualDubMod 1.5.10.2 (build 2540/release)
Load subtitles in .
get_path('sub/') -> '/home/casa/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 running at 1440x900 with depth 24 (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
vo: uninit ...
X11 opening display: :0.0
vo: X11 running at 1440x900 with depth 24 (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 16384x16384
[vo] query(Planar YV12) -> 437
[ass] auto-open
Opening video decoder: [ffmpeg] libavcodec video codecs
Asking decoder to use 8 threads if supported.
Selected video codec: MPEG-4 part 2 [libavcodec]
Video codecs.conf entry: ffodivx (FFmpeg MPEG-4)  vfm: ffmpeg
Opening audio decoder: [mpg123] MPEG 1.0/2.0/2.5 layers I, II, III
dec_audio: Allocating 8192 + 65536 = 73728 bytes for output buffer.
MPEG 1.0 layer III, 128 kbit/s ABR, 48000 Hz joint-stereo
Selected audio codec: MPEG 1.0/2.0/2.5 layers I, II, III [mpg123]
Audio codecs.conf entry: mpg123 (MPEG 1.0/2.0/2.5 layers I, II, III)  afm: mpg123
AUDIO: 48000 Hz, 2 ch, s16le, 32.0 kbit/2.08% (ratio: 4000->192000)
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Audio filter chain:
  [in] 48000Hz/2ch/s16le
  [dummy] 48000Hz/2ch/s16le
  [out] 0Hz/0ch/??
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Audio filter chain:
  [in] 48000Hz/2ch/s16le
  [dummy] 48000Hz/2ch/s16le
  [out] 0Hz/0ch/??
Trying every known audio driver...
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Audio filter chain:
  [in] 48000Hz/2ch/s16le
  [dummy] 48000Hz/2ch/s16le
  [out] 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
Audio filter chain:
  [in] 48000Hz/2ch/s16le
  [dummy] 48000Hz/2ch/s16le
  [out] 48000Hz/2ch/s16le
Starting playback...
[ffmpeg] aspect_ratio: 1.772727
VIDEO:  624x352  23.976 fps  1006.4 kbps (125.8 kB/s)
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
Trying filter chain: ass vo
VDec: using Planar YV12 as output csp (no 0)
VO Config (624x352->624x352,flags=0,0x32315659)
REQ: flags=0x437  req=0x0  
VO: [xv] 624x352 => 624x352 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 74 for hw scaling
xv_set_eq called! (bt_709, -100)
*** [ass] Exporting mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
*** [vo] Allocating mp_image_t, 624x352x12bpp YUV planar, 329472 bytes
Increasing filtered audio buffer size from 0 to 2048
Increasing filtered audio buffer size from 2048 to 11076
Increasing filtered audio buffer size from 11076 to 80196
Increasing filtered audio buffer size from 80196 to 149316
Increasing filtered audio buffer size from 149316 to 193988
A:   9.8 V:   9.8 A-V:  0.001 ct:  0.000   0/  0  0%  0%  0.2% 0 0 
AO: [pulse] pa_stream_update_timing_info() failed: Connection terminated
A:  11.1 V:   9.8 A-V:  1.278 ct:  0.000   0/  0  0%  0%  0.2% 0 0 
Increasing filtered audio buffer size from 193988 to -2147481608


MPlayer interrupted by signal 6 in module: decode_audio
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

And this is mplayer on a working video:
```

mplayer  -v  Scrivania/Continuavano\ Chiamarlo\ Trinita\ 1971\ iTALiAN\ DVDRip\ Xvi.flv 
Reading config file /etc/mplayer/mplayer.conf
: No such file or directory
get_path('') -> '/home/casa/.mplayer/'
get_path('config') -> '/home/casa/.mplayer/config'
Reading config file /home/casa/.mplayer/config
MPlayer2 2.0-728-g2c378c7-4build1 (C) 2000-2012 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM) i7-4790 CPU @ 3.60GHz (Family: 6, Model: 60, Stepping: 3)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSSE3: 1
Compiled with runtime CPU detection.
Compiled against libavutil version 54.27.100
Compiled against libavcodec version 56.41.100
Compiled against libavformat version 56.36.100
Compiled against libswscale version 3.1.101
get_path('codecs.conf') -> '/home/casa/.mplayer/codecs.conf'
No optional codecs config file: /home/casa/.mplayer/codecs.conf
No optional codecs config file: /etc/mplayer/codecs.conf
163 audio & 363 video codecs
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-translation --enable-debug=3 --extra-ldflags=-Wl,--as-needed --enable-runtime-cpudetection
CommandLine: '-v' 'Scrivania/Continuavano Chiamarlo Trinita 1971 iTALiAN DVDRip Xvi.flv'
get_path('fonts') -> '/home/casa/.mplayer/fonts'
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/casa/.mplayer/fonts'
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 1.0.1 (COMPLEX)
[ass] Initialized
get_path('fonts') -> '/home/casa/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/casa/.mplayer/subfont.ttf'
[ass] Adding memory font 'OSD'
[ass] Updating font cache
Using nanosleep() timing
get_path('input.conf') -> '/home/casa/.mplayer/input.conf'
Cannot open file '/home/casa/.mplayer/input.conf': No such file or directory
Failed to open /home/casa/.mplayer/input.conf.
Can't open input config file /home/casa/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.
Can't open input config file /etc/mplayer/input.conf.
Falling back on default (hardcoded) input config
Setting up LIRC support...
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Continuavano Chiamarlo Trinita 1971 iTALiAN DVDRip Xvi.flv.conf') -> '/home/casa/.mplayer/Continuavano Chiamarlo Trinita 1971 iTALiAN DVDRip Xvi.flv.conf'

Playing Scrivania/Continuavano Chiamarlo Trinita 1971 iTALiAN DVDRip Xvi.flv.
get_path('sub/') -> '/home/casa/.mplayer/sub/'
[file] File size is 34832384 bytes
STREAM: [file] Scrivania/Continuavano Chiamarlo Trinita 1971 iTALiAN DVDRip Xvi.flv
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: FLV (Flash Video)
Detected file format: FLV (Flash Video) (libavformat)
==> Found video stream: 0
======= VIDEO Format ======
  biSize 81
  biWidth 640
  biHeight 272
  biPlanes 0
  biBitCount 0
  biCompression 875967048='H264'
  biSizeImage 0
Unknown extra header dump: [1] [64] [0] [15] [ff] [e1] [0] [19] [67] [64] [0] [15] [ac] [d9] [40] [a0] [23] [b0] [11] [0] [0] [3] [0] [1] [0] [0] [3] [0] [32] [f] [16] [2d] [96] [1] [0] [5] [68] [ea] [e1] [3c] [b0] 
===========================
[lavf] stream 0: video (h264), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 20557 (0x504D)
Channels: 2
Samplerate: 44100
avg byte/sec: 16086
Block align: 1
bits/sample: 16
cbSize: 2
Unknown extra header dump: [12] [10] 
==========================================================================
[lavf] stream 1: audio (aac), -aid 0
LAVF: 1 audio and 1 video streams found
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE) HarfBuzz-ng 1.0.1 (COMPLEX)
[ass] Initialized
get_path('fonts') -> '/home/casa/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/casa/.mplayer/subfont.ttf'
[ass] Updating font cache
[V] filefmt:41  fourcc:0x34363248  size:640x272  fps:25.000  ftime:=0.0400
Clip info:
 creator: XVideoSharing
 metadatacreator: Yet Another Metadata Injector for FLV - Version 1.8
 hasKeyframes: true
 hasVideo: true
 hasAudio: true
 hasMetadata: true
 canSeekToEnd: true
 datasize: 726181886
 videosize: 617606806
 audiosize: 106818700
 lasttimestamp: 6452
 lastkeyframetimestamp: 6452
 lastkeyframelocation: 726203582
Load subtitles in Scrivania/
get_path('sub/') -> '/home/casa/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 running at 1440x900 with depth 24 (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Failed to open VDPAU backend libvdpau_va_gl.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
vo: uninit ...
X11 opening display: :0.0
vo: X11 running at 1440x900 with depth 24 (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Detected wm supports FULLSCREEN state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (Intel(R) Textured Video)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 16384x16384
[vo] query(Planar YV12) -> 437
[ass] auto-open
Opening video decoder: [ffmpeg] libavcodec video codecs
Asking decoder to use 8 threads if supported.
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Video codecs.conf entry: ffh264 (FFmpeg H.264)  vfm: ffmpeg
Opening audio decoder: [ffmpeg] libavcodec audio decoders
dec_audio: Allocating 8192 + 65536 = 73728 bytes for output buffer.
INFO: libavcodec "aac" init OK!
(Re)initializing libavresample format conversion...
Selected audio codec: AAC (Advanced Audio Coding) [libavcodec]
Audio codecs.conf entry: ffaac (FFmpeg AAC (MPEG-2/MPEG-4 Audio))  afm: ffmpeg
AUDIO: 44100 Hz, 2 ch, floatle, 128.7 kbit/4.56% (ratio: 16086->352800)
Building audio filter chain for 44100Hz/2ch/floatle -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Audio filter chain:
  [in] 44100Hz/2ch/floatle
  [dummy] 44100Hz/2ch/floatle
  [out] 0Hz/0ch/??
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Audio filter chain:
  [in] 44100Hz/2ch/floatle
  [dummy] 44100Hz/2ch/floatle
  [out] 0Hz/0ch/??
Trying every known audio driver...
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 44100Hz/2ch/floatle -> 44100Hz/2ch/floatle...
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Audio filter chain:
  [in] 44100Hz/2ch/floatle
  [dummy] 44100Hz/2ch/floatle
  [out] 44100Hz/2ch/floatle
[dummy] Was reinitialized: 44100Hz/2ch/floatle
Audio filter chain:
  [in] 44100Hz/2ch/floatle
  [dummy] 44100Hz/2ch/floatle
  [out] 44100Hz/2ch/floatle
Starting playback...
[ffmpeg] aspect_ratio: 2.352941
VIDEO:  640x272  25.000 fps  763.6 kbps (95.5 kB/s)
VDec: vo config request - 640 x 272 (preferred colorspace: Planar YV12)
Trying filter chain: ass vo
VDec: using Planar YV12 as output csp (no 0)
VO Config (640x272->640x272,flags=0,0x32315659)
REQ: flags=0x437  req=0x0  
VO: [xv] 640x272 => 640x272 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x434d5658 (XVMC) planar
using Xvideo port 74 for hw scaling
xv_set_eq called! (bt_709, -100)
*** [ass] Exporting mp_image_t, 640x272x12bpp YUV planar, 261120 bytes
*** [vo] Allocating mp_image_t, 640x272x12bpp YUV planar, 261120 bytes
Increasing filtered audio buffer size from 0 to 4096
Increasing filtered audio buffer size from 4096 to 30848
Increasing filtered audio buffer size from 30848 to 69576
Increasing filtered audio buffer size from 69576 to 135112
Increasing filtered audio buffer size from 135112 to 200648
Increasing filtered audio buffer size from 200648 to 266184
Increasing filtered audio buffer size from 266184 to 331720
Increasing filtered audio buffer size from 331720 to 356808
A:   2.8 V:   2.8 A-V:  0.000 ct: -0.000   0/  0  0%  0%  0.3% 0 0 
Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: ffmpeg
Uninit video: ffmpeg
vo: uninit ...

Exiting... (Quit)

```

Info on the system has been gathered with the command:
wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh
and the output is:
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Wed Feb 10 09:13:36 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 15.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      To Be Filled By O.E.M.
Product Name:      To Be Filled By O.E.M.
Product Version:   To Be Filled By O.E.M.
Firmware Version:  P1.90


!!Kernel Information
!!------------------

Kernel release:    4.2.0-28-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.2.0-28-generic
Library version:    1.0.29
Utilities version:  1.0.29


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xefd34000 irq 30
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xefd30000 irq 29


!!PCI Soundcards installed in the system
!!--------------------------------------

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:03.0 0403: 8086:0c0c (rev 06)
	Subsystem: 1849:0c0c
--
00:1b.0 0403: 8086:8ca0
	Subsystem: 1849:c892


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1

!!Module: snd_hda_intel
	align_buffer_size : -1
	bdl_pos_adj : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N,N
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	jackpoll_ms : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N
	snoop : -1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Intel Haswell HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862807
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled GenLevel KAE
  Digital category: 0x2
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D3, actual=D3
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560020: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560030: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
Codec: Realtek ALC892
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0892
Subsystem Id: 0x1849c892
Revision Id: 0x100302
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D1 D2 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Control: name="Headphone Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x611: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC892 Digital", type="SPDIF", device=1
  Converter: stream=5, channel=0
  Digital: Enabled Non-Audio GenLevel
  Digital category: 0x2
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x08 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC892 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0xae 0xae]
  Converter: stream=1, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10051b: Stereo Amp-In
  Control: name="Capture Volume", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Capture Switch", index=1, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="ALC892 Alt Analog", type="Audio", device=2
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100711: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Rear Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Rear Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x611: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x11 [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x40000000: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0x0, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400401: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0001003e: IN OUT HP EAPD Detect Trigger
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=05, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0c
Node 0x15 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=06, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0d
Node 0x16 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=07, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x17 [Pin Complex] wcaps 0x40058d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00000036: IN OUT Detect Trigger
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0f
Node 0x18 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Rear Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19040: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x4, Sequence = 0x0
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x19 [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x02 0x02]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373e: IN OUT HP Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19050: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1a [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Line Boost Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x00003736: IN OUT Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181304f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x4, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=04, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1b [Pin Complex] wcaps 0x40058f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0001373e: IN OUT HP EAPD Detect Trigger
    Vref caps: HIZ 50 GRD 80 100
  EAPD 0x2: EAPD
  Pin Default 0x02214020: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x1c [Pin Complex] wcaps 0x400481: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1d [Pin Complex] wcaps 0x400400: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4035e601: [N/A] CD at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x1e [Pin Complex] wcaps 0x400781: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x01451130: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Black
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=24
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 12
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x80 0x80] [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x25 [Audio Output] wcaps 0x41d: Stereo Amp-Out
  Amp-Out caps: ofs=0x40, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Power states:  D0 D1 D2 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x26 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80]
  Connection: 2
     0x25 0x0b
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  8 Feb 10 09:42 /dev/snd/controlC0
crw-rw----+ 1 root audio 116,  2 Feb 10 09:42 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 12 Feb 10 09:42 /dev/snd/hwC0D0
crw-rw----+ 1 root audio 116,  7 Feb 10 09:42 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116,  9 Feb 10 09:43 /dev/snd/pcmC0D3p
crw-rw----+ 1 root audio 116, 10 Feb 10 09:43 /dev/snd/pcmC0D7p
crw-rw----+ 1 root audio 116, 11 Feb 10 09:43 /dev/snd/pcmC0D8p
crw-rw----+ 1 root audio 116,  4 Feb 10 09:43 /dev/snd/pcmC1D0c
crw-rw----+ 1 root audio 116,  3 Feb 10 09:43 /dev/snd/pcmC1D0p
crw-rw----+ 1 root audio 116,  5 Feb 10 09:58 /dev/snd/pcmC1D1p
crw-rw----+ 1 root audio 116,  6 Feb 10 09:42 /dev/snd/pcmC1D2c
crw-rw----+ 1 root audio 116,  1 Feb 10 09:42 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Feb 10 09:42 /dev/snd/timer

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root  80 Feb 10 09:42 .
drwxr-xr-x 3 root root 320 Feb 10 09:42 ..
lrwxrwxrwx 1 root root  12 Feb 10 09:42 pci-0000:00:03.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Feb 10 09:42 pci-0000:00:1b.0 -> ../controlC1


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)

# alsa plugin a52
# speaker-test -c 6 -l 1 -D pcm.a52:[CARD]
pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 640 # 448 is max for most
      channels 6
      card $CARD
    }
  rate 48000
  }
}


!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 2: ALC892 Alt Analog [ALC892 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [HDMI]

Card hw:0 'HDMI'/'HDA Intel HDMI at 0xefd34000 irq 30'
  Mixer name	: 'Intel Haswell HDMI'
  Components	: 'HDA:80862807,80860101,00100000'
  Controls      : 21
  Simple ctrls  : 3
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 1 [PCH]

Card hw:1 'PCH'/'HDA Intel PCH at 0xefd30000 irq 29'
  Mixer name	: 'Realtek ALC892'
  Components	: 'HDA:10ec0892,1849c892,00100302'
  Controls      : 47
  Simple ctrls  : 21
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [-64.00dB] [off]
  Front Right: Playback 0 [0%] [-64.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 2 [67%] [20.00dB]
  Front Right: 2 [67%] [20.00dB]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Line Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 46 [100%] [30.00dB] [off]
  Front Right: Capture 46 [100%] [30.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Front Mic' 'Rear Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Loopback Mixing',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]


!!Alsactl output
!!--------------

--startcollapse--
state.HDMI {
	control.1 {
		iface CARD
		name 'HDMI/DP,pcm=3 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.2 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.3 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.4 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write locked'
			type IEC958
			count 1
		}
	}
	control.5 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.6 {
		iface PCM
		device 3
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.7 {
		iface CARD
		name 'HDMI/DP,pcm=7 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 1
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 1
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.10 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 1
		value '0400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.11 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 1
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.12 {
		iface PCM
		device 7
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.13 {
		iface CARD
		name 'HDMI/DP,pcm=8 Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.14 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		index 2
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.15 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		index 2
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.16 {
		iface MIXER
		name 'IEC958 Playback Default'
		index 2
		value '0482000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write'
			type IEC958
			count 1
		}
	}
	control.17 {
		iface MIXER
		name 'IEC958 Playback Switch'
		index 2
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.18 {
		iface PCM
		device 8
		name ELD
		value ''
		comment {
			access 'read volatile'
			type BYTES
			count 0
		}
	}
	control.19 {
		iface PCM
		device 3
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.20 {
		iface PCM
		device 7
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
	control.21 {
		iface PCM
		device 8
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		value.6 0
		value.7 0
		comment {
			access 'read write'
			type INTEGER
			count 8
			range '0 - 36'
		}
	}
}
state.PCH {
	control.1 {
		iface MIXER
		name 'Front Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.2 {
		iface MIXER
		name 'Front Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.3 {
		iface MIXER
		name 'Surround Playback Volume'
		value.0 64
		value.1 64
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.4 {
		iface MIXER
		name 'Surround Playback Switch'
		value.0 true
		value.1 true
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.5 {
		iface MIXER
		name 'Center Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.6 {
		iface MIXER
		name 'LFE Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.7 {
		iface MIXER
		name 'Center Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.8 {
		iface MIXER
		name 'LFE Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.9 {
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 -6400
			dbvalue.1 -6400
		}
	}
	control.10 {
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.11 {
		iface MIXER
		name 'Loopback Mixing'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.12 {
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.13 {
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.14 {
		iface MIXER
		name 'Rear Mic Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.15 {
		iface MIXER
		name 'Rear Mic Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.16 {
		iface MIXER
		name 'Line Playback Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 31'
			dbmin -3450
			dbmax 1200
			dbvalue.0 -3450
			dbvalue.1 -3450
		}
	}
	control.17 {
		iface MIXER
		name 'Line Playback Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.18 {
		iface MIXER
		name 'Auto-Mute Mode'
		value Enabled
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 Disabled
			item.1 Enabled
		}
	}
	control.19 {
		iface MIXER
		name 'Input Source'
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.20 {
		iface MIXER
		name 'Input Source'
		index 1
		value 'Front Mic'
		comment {
			access 'read write'
			type ENUMERATED
			count 1
			item.0 'Front Mic'
			item.1 'Rear Mic'
			item.2 Line
		}
	}
	control.21 {
		iface MIXER
		name 'Capture Volume'
		value.0 46
		value.1 46
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 46'
			dbmin -1600
			dbmax 3000
			dbvalue.0 3000
			dbvalue.1 3000
		}
	}
	control.22 {
		iface MIXER
		name 'Capture Switch'
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.23 {
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 46'
			dbmin -1600
			dbmax 3000
			dbvalue.0 -1600
			dbvalue.1 -1600
		}
	}
	control.24 {
		iface MIXER
		name 'Capture Switch'
		index 1
		value.0 false
		value.1 false
		comment {
			access 'read write'
			type BOOLEAN
			count 2
		}
	}
	control.25 {
		iface MIXER
		name 'Front Mic Boost Volume'
		value.0 2
		value.1 2
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 2000
			dbvalue.1 2000
		}
	}
	control.26 {
		iface MIXER
		name 'Rear Mic Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.27 {
		iface MIXER
		name 'Line Boost Volume'
		value.0 0
		value.1 0
		comment {
			access 'read write'
			type INTEGER
			count 2
			range '0 - 3'
			dbmin 0
			dbmax 3000
			dbvalue.0 0
			dbvalue.1 0
		}
	}
	control.28 {
		iface MIXER
		name 'IEC958 Playback Con Mask'
		value '0fff000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.29 {
		iface MIXER
		name 'IEC958 Playback Pro Mask'
		value '0f00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access read
			type IEC958
			count 1
		}
	}
	control.30 {
		iface MIXER
		name 'IEC958 Playback Default'
		value '0682000200000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'
		comment {
			access 'read write locked'
			type IEC958
			count 1
		}
	}
	control.31 {
		iface MIXER
		name 'IEC958 Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.32 {
		iface MIXER
		name 'IEC958 Default PCM Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.33 {
		iface MIXER
		name 'Master Playback Volume'
		value 64
		comment {
			access 'read write'
			type INTEGER
			count 1
			range '0 - 64'
			dbmin -6400
			dbmax 0
			dbvalue.0 0
		}
	}
	control.34 {
		iface MIXER
		name 'Master Playback Switch'
		value true
		comment {
			access 'read write'
			type BOOLEAN
			count 1
		}
	}
	control.35 {
		iface CARD
		name 'Front Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.36 {
		iface CARD
		name 'Rear Mic Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.37 {
		iface CARD
		name 'Line Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.38 {
		iface CARD
		name 'Line Out Front Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.39 {
		iface CARD
		name 'Line Out Surround Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.40 {
		iface CARD
		name 'Line Out CLFE Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.41 {
		iface CARD
		name 'Front Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.42 {
		iface CARD
		name 'SPDIF Phantom Jack'
		value true
		comment {
			access read
			type BOOLEAN
			count 1
		}
	}
	control.43 {
		iface PCM
		name 'Playback Channel Map'
		value.0 0
		value.1 0
		value.2 0
		value.3 0
		value.4 0
		value.5 0
		comment {
			access read
			type INTEGER
			count 6
			range '0 - 36'
		}
	}
	control.44 {
		iface PCM
		name 'Capture Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.45 {
		iface PCM
		device 1
		name 'Playback Channel Map'
		value.0 3
		value.1 4
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.46 {
		iface PCM
		device 2
		name 'Capture Channel Map'
		value.0 0
		value.1 0
		comment {
			access read
			type INTEGER
			count 2
			range '0 - 36'
		}
	}
	control.47 {
		iface MIXER
		name 'PCM Playback Volume'
		value.0 255
		value.1 255
		comment {
			access 'read write user'
			type INTEGER
			count 2
			range '0 - 255'
			tlv '0000000100000008ffffec1400000014'
			dbmin -5100
			dbmax 0
			dbvalue.0 0
			dbvalue.1 0
		}
	}
}
--endcollapse--


!!All Loaded Modules
!!------------------

Module
dm_crypt
drbg
ansi_cprng
algif_skcipher
af_alg
input_leds
joydev
hid_sunplus
usbhid
uas
usb_storage
binfmt_misc
arc4
intel_rapl
x86_pkg_temp_thermal
intel_powerclamp
rtl8192ce
kvm_intel
rtl_pci
rtl8192c_common
kvm
rtlwifi
snd_hda_codec_hdmi
mac80211
crct10dif_pclmul
snd_hda_codec_realtek
snd_hda_codec_generic
crc32_pclmul
aesni_intel
aes_x86_64
lrw
gf128mul
glue_helper
ablk_helper
cryptd
cfg80211
snd_soc_rt5640
snd_hda_intel
snd_soc_rl6231
snd_soc_core
snd_hda_codec
snd_compress
snd_hda_core
ac97_bus
snd_hwdep
snd_pcm_dmaengine
snd_pcm
shpchp
lpc_ich
mei_me
serio_raw
mei
nct6775
hwmon_vid
coretemp
snd_seq_midi
snd_seq_midi_event
snd_rawmidi
snd_seq
snd_seq_device
snd_timer
snd
nuvoton_cir
8250_fintek
rc_core
soundcore
i2c_designware_platform
dw_dmac
snd_soc_sst_acpi
dw_dmac_core
i2c_designware_core
intel_smartconnect
spi_pxa2xx_platform
8250_dw
acpi_pad
mac_hid
parport_pc
ppdev
lp
parport
autofs4
mxm_wmi
i915
i2c_algo_bit
drm_kms_helper
e1000e
drm
psmouse
ahci
ptp
libahci
pps_core
sdhci_acpi
wmi
video
sdhci
i2c_hid
hid


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D0/init_pin_configs:
0x05 0x18560010
0x06 0x18560020
0x07 0x18560030

/sys/class/sound/hwC0D0/driver_pin_configs:

/sys/class/sound/hwC0D0/user_pin_configs:

/sys/class/sound/hwC0D0/init_verbs:

/sys/class/sound/hwC0D0/hints:

/sys/class/sound/hwC1D0/init_pin_configs:
0x11 0x40000000
0x12 0x411111f0
0x14 0x01014010
0x15 0x01011012
0x16 0x01016011
0x17 0x411111f0
0x18 0x01a19040
0x19 0x02a19050
0x1a 0x0181304f
0x1b 0x02214020
0x1c 0x411111f0
0x1d 0x4035e601
0x1e 0x01451130
0x1f 0x411111f0

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC1D0/hints:


!!ALSA/HDA dmesg
!!--------------

[    1.690076] audit: type=1400 audit(1455093726.592:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=521 comm="apparmor_parser"
[    1.693403] snd_hda_core: module verification failed: signature and/or required key missing - tainting kernel
[    1.701444] snd_hda_intel 0000:00:03.0: Probing card using HDA DKMS, version 0.201602091746~ubuntu14.04.1
[    1.701562] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    1.701563] audit: type=1400 audit(1455093726.604:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=521 comm="apparmor_parser"
--
[    1.701573] audit: type=1400 audit(1455093726.604:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=521 comm="apparmor_parser"
[    1.702089] snd_hda_intel 0000:00:1b.0: Probing card using HDA DKMS, version 0.201602091746~ubuntu14.04.1
[    1.712210] AVX2 version of gcm_enc/dec engaged.
[    1.712212] AES CTR mode by8 optimization enabled
[    1.717280] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC892: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
[    1.717283] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    1.717285] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    1.717286] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    1.717288] snd_hda_codec_realtek hdaudioC1D0:    dig-out=0x1e/0x0
[    1.717289] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    1.717291] snd_hda_codec_realtek hdaudioC1D0:      Front Mic=0x19
[    1.717292] snd_hda_codec_realtek hdaudioC1D0:      Rear Mic=0x18
[    1.717294] snd_hda_codec_realtek hdaudioC1D0:      Line=0x1a
[    1.729442] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7
[    1.729501] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input8
[    1.729557] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input9
[    1.729607] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card1/input10
[    1.729658] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card1/input11
[    1.729711] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card1/input12
[    1.729760] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[    1.730057] snd_hda_intel 0000:00:03.0: failed to add i915 component master (-19)
[    1.733307] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[    1.733365] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[    1.733460] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input16
[    1.738259] intel_rapl: Found RAPL domain package
--
[    3.489327] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    8.063264] snd_hda_intel 0000:00:1b.0: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   24.689854] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by leodp on 2016-02-10
It seems I get crashes when the played audio has a sample rate of 48kHz
/etc/asound.conf is set to 48kHz
I have reduced the bitrate but still no solution

```

# alsa plugin a52
# speaker-test -c 6 -l 1 -D pcm.a52:[CARD]
pcm.a52 {
  @args [CARD]
  @args.CARD {
    type string
  }
  type rate
  slave {
    pcm {
      type a52
      bitrate 640 # 448 is max for most
      channels 6
      card $CARD
    }
  rate 48000
  }
}

```


When mplayer crashes there is a sort of overflow error:
AO: [pulse] pa_stream_update_timing_info() failed: Connection terminated
Increasing filtered audio buffer size from 193988 to -2147481608

VLC error message reads :
[000000000177ada8] pulse audio output error: unknown latency: Stato errato (wrong status?)
[000000000177ada8] pulse audio output error: cannot write: Stato errato

---

### Post by leodp on 2016-02-10
adding the verbose pulseaudio crash log (changed square brackets with round ones, 'cause reply was not accepted by forum reply form):
```

(   0.000|   0.000) I: (pulseaudio) main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: (pulseaudio) main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: (pulseaudio) core-rtclock.c: Timer slack is set to 50 us.
(   0.002|   0.002) D: (pulseaudio) core-util.c: RealtimeKit worked.
(   0.002|   0.000) I: (pulseaudio) core-util.c: Successfully gained nice level -11.
(   0.002|   0.000) I: (pulseaudio) main.c: This is PulseAudio 6.0
(   0.002|   0.000) D: (pulseaudio) main.c: Compilation host: x86_64-pc-linux-gnu
(   0.002|   0.000) D: (pulseaudio) main.c: Compilation CFLAGS: -g -O2 -fstack-protector-strong -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -fno-common -fdiagnostics-show-option -fdiagnostics-color=auto
(   0.002|   0.000) D: (pulseaudio) main.c: Running on host: Linux x86_64 4.2.0-28-generic #33-Ubuntu SMP Mon Feb 1 23:09:27 UTC 2016
(   0.002|   0.000) D: (pulseaudio) main.c: Found 8 CPUs.
(   0.002|   0.000) I: (pulseaudio) main.c: Page size is 4096 bytes
(   0.002|   0.000) D: (pulseaudio) main.c: Compiled with Valgrind support: no
(   0.002|   0.000) D: (pulseaudio) main.c: Running in valgrind mode: no
(   0.002|   0.000) D: (pulseaudio) main.c: Running in VM: no
(   0.002|   0.000) D: (pulseaudio) main.c: Optimized build: yes
(   0.002|   0.000) D: (pulseaudio) main.c: FASTPATH defined, only fast path asserts disabled.
(   0.002|   0.000) I: (pulseaudio) main.c: Machine ID is adbef842f549a8c77a0abd52563e6f2e.
(   0.002|   0.000) I: (pulseaudio) main.c: Session ID is c2.
(   0.002|   0.000) I: (pulseaudio) main.c: Using runtime directory /run/user/1000/pulse.
(   0.002|   0.000) I: (pulseaudio) main.c: Using state directory /home/casa/.config/pulse.
(   0.002|   0.000) I: (pulseaudio) main.c: Using modules directory /usr/lib/pulse-6.0/modules.
(   0.002|   0.000) I: (pulseaudio) main.c: Running in system mode: no
(   0.002|   0.000) I: (pulseaudio) main.c: Fresh high-resolution timers available! Bon appetit!
(   0.002|   0.000) D: (pulseaudio) memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65472
(   0.002|   0.000) D: (pulseaudio) memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65472
(   0.002|   0.000) I: (pulseaudio) cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
(   0.002|   0.000) I: (pulseaudio) svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.002|   0.000) I: (pulseaudio) remap_mmx.c: Initialising MMX optimized remappers.
(   0.002|   0.000) I: (pulseaudio) svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.002|   0.000) I: (pulseaudio) remap_sse.c: Initialising SSE2 optimized remappers.
(   0.002|   0.000) I: (pulseaudio) sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.002|   0.000) I: (pulseaudio) svolume_orc.c: Initialising ORC optimized volume functions.
(   0.002|   0.000) D: (pulseaudio) database-tdb.c: Opened TDB database '/home/casa/.config/pulse/adbef842f549a8c77a0abd52563e6f2e-device-volumes.tdb'
(   0.002|   0.000) I: (pulseaudio) module-device-restore.c: Successfully opened database file '/home/casa/.config/pulse/adbef842f549a8c77a0abd52563e6f2e-device-volumes'.
(   0.002|   0.000) I: (pulseaudio) module.c: Loaded "module-device-restore" (index: #0; argument: "").
(   0.003|   0.000) D: (pulseaudio) database-tdb.c: Opened TDB database '/home/casa/.config/pulse/adbef842f549a8c77a0abd52563e6f2e-stream-volumes.tdb'
(   0.003|   0.000) I: (pulseaudio) module-stream-restore.c: Successfully opened database file '/home/casa/.config/pulse/adbef842f549a8c77a0abd52563e6f2e-stream-volumes'.
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry2
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry3
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry4
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry5
(   0.003|   0.000) D: (pulseaudio) protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry6
(   0.003|   0.000) I: (pulseaudio) module.c: Loaded "module-stream-restore" (index: #1; argument: "").
(   0.003|   0.000) D: (pulseaudio) database-tdb.c: Opened TDB database '/home/casa/.config/pulse/adbef842f549a8c77a0abd52563e6f2e-card-database.tdb'
(   0.003|   0.000) I: (pulseaudio) module-card-restore.c: Successfully opened database file '/home/casa/.config/pulse/adbef842f549a8c77a0abd52563e6f2e-card-database'.
(   0.003|   0.000) I: (pulseaudio) module.c: Loaded "module-card-restore" (index: #2; argument: "").
(   0.003|   0.000) I: (pulseaudio) module.c: Loaded "module-augment-properties" (index: #3; argument: "").
(   0.003|   0.000) I: (pulseaudio) module.c: Loaded "module-switch-on-port-available" (index: #4; argument: "").
(   0.003|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-udev-detect.so': success
(   0.004|   0.000) D: (pulseaudio) module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.004|   0.000) D: (pulseaudio) module-udev-detect.c: /devices/pci0000:00/0000:00:03.0/sound/card0 is busy: no
(   0.004|   0.000) D: (pulseaudio) module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="0" name="pci-0000_00_03.0" card_name="alsa_card.pci-0000_00_03.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"'
(   0.005|   0.001) D: (pulseaudio) dbus-util.c: Successfully connected to D-Bus session bus 14e4e1a6318fb87760d9baa156baf7e4 as :1.195
(   0.005|   0.000) D: (pulseaudio) reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
(   0.005|   0.000) I: (pulseaudio) (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/HDA Intel HDMI/HDA Intel HDMI.conf
(   0.005|   0.000) I: (pulseaudio) (alsa-lib)parser.c: error: could not parse configuration for card HDA Intel HDMI
(   0.005|   0.000) I: (pulseaudio) (alsa-lib)main.c: error: failed to import HDA Intel HDMI use case configuration -2
(   0.005|   0.000) I: (pulseaudio) alsa-ucm.c: UCM not available for card HDA Intel HDMI
(   0.005|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf'
(   0.006|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:analog-mono
(   0.006|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.006|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.007|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.007|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.007|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open input:analog-mono
(   0.007|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:analog-stereo
(   0.007|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.007|   0.000) D: (pulseaudio) alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open input:analog-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:iec958-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open input:iec958-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-mono
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-mono
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:analog-mono - will not be able to open output:analog-mono
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:analog-stereo - will not be able to open output:analog-mono
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:iec958-stereo - will not be able to open output:analog-mono
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device front:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-mono - will not be able to open output:analog-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-stereo - will not be able to open output:analog-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-stereo+input:iec958-stereo - will not be able to open output:analog-stereo
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-21
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 2.1 (analog-surround-21)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying surround21:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device surround21:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-21
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-21+input:analog-mono - will not be able to open output:analog-surround-21
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-21+input:analog-stereo - will not be able to open output:analog-surround-21
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-21+input:iec958-stereo - will not be able to open output:analog-surround-21
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-40
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device surround40:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-40
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-mono - will not be able to open output:analog-surround-40
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-stereo - will not be able to open output:analog-surround-40
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-40+input:iec958-stereo - will not be able to open output:analog-surround-40
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-41
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device surround41:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-41
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-mono - will not be able to open output:analog-surround-41
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-stereo - will not be able to open output:analog-surround-41
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-41+input:iec958-stereo - will not be able to open output:analog-surround-41
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-50
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.008|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.008|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device surround50:0: No such file or directory
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-50
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-mono - will not be able to open output:analog-surround-50
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-stereo - will not be able to open output:analog-surround-50
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-50+input:iec958-stereo - will not be able to open output:analog-surround-50
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-51
(   0.008|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.008|   0.000) D: (pulseaudio) alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.009|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.009|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device surround51:0: No such file or directory
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-51
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-mono - will not be able to open output:analog-surround-51
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-stereo - will not be able to open output:analog-surround-51
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-51+input:iec958-stereo - will not be able to open output:analog-surround-51
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-71
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.009|   0.000) D: (pulseaudio) alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.009|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0p' failed (-2)
(   0.009|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device surround71:0: No such file or directory
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-71
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-mono - will not be able to open output:analog-surround-71
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-stereo - will not be able to open output:analog-surround-71
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:iec958-stereo - will not be able to open output:analog-surround-71
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-stereo
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.009|   0.000) D: (pulseaudio) alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.009|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.009|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device iec958:0: No such file or directory
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:iec958-stereo
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-mono - will not be able to open output:iec958-stereo
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-stereo - will not be able to open output:iec958-stereo
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-stereo+input:iec958-stereo - will not be able to open output:iec958-stereo
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
(   0.009|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.009|   0.000) D: (pulseaudio) alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.014|   0.004) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.014|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-40
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-mono - will not be able to open output:iec958-ac3-surround-40
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-stereo - will not be able to open output:iec958-ac3-surround-40
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-40
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.014|   0.000) D: (pulseaudio) alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.014|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1p' failed (-2)
(   0.014|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device a52:0: No such file or directory
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-mono - will not be able to open output:iec958-ac3-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-stereo - will not be able to open output:iec958-ac3-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-dts-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
(   0.014|   0.000) D: (pulseaudio) alsa-util.c: Trying dca:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.014|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dca:0
(   0.014|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dca:0: No such file or directory
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:iec958-dts-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-mono - will not be able to open output:iec958-dts-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-stereo - will not be able to open output:iec958-dts-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:iec958-stereo - will not be able to open output:iec958-dts-surround-51
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo
(   0.014|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.014|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.014|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0
(   0.014|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.021|   0.007) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-stereo supported.
(   0.022|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-0.conf'
(   0.022|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0
(   0.022|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
(   0.022|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'hdmi-output-0'
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=3 Jack' succeeded (found!)
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2284920, direction=1
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-mono - will not be able to open input:analog-mono
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-stereo - will not be able to open input:analog-stereo
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround
(   0.022|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
(   0.022|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.022|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0
(   0.022|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.029|   0.006) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround supported.
(   0.030|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0
(   0.030|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
(   0.030|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2299da0, direction=1
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-mono - will not be able to open input:analog-mono
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-stereo - will not be able to open input:analog-stereo
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71
(   0.030|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI) (hdmi-surround71)
(   0.030|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.030|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0
(   0.030|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 92 ms
(   0.037|   0.007) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround71 supported.
(   0.038|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0
(   0.038|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
(   0.038|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2289e50, direction=1
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:analog-mono - will not be able to open input:analog-mono
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:analog-stereo - will not be able to open input:analog-stereo
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI/DTS) (hdmi-dts-surround)
(   0.038|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.038|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0
(   0.038|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0: No such file or directory
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:analog-mono - will not be able to open output:hdmi-dts-surround
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:analog-stereo - will not be able to open output:hdmi-dts-surround
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:iec958-stereo - will not be able to open output:hdmi-dts-surround
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1
(   0.038|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 2) (hdmi-stereo-extra1)
(   0.038|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.038|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0,1
(   0.038|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.045|   0.006) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-stereo-extra1 supported.
(   0.046|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-1.conf'
(   0.046|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0,1
(   0.046|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0,1: No such file or directory
(   0.046|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'hdmi-output-1'
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=7 Jack' succeeded (found!)
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x22ea240, direction=1
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-1 (HDMI / DisplayPort 2), direction=1, priority=58, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=7, alsa_name='HDMI/DP,pcm=7 Jack', detection possible
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-mono - will not be able to open input:analog-mono
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-stereo - will not be able to open input:analog-stereo
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra1
(   0.046|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 2) (hdmi-surround-extra1)
(   0.046|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.046|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0,1
(   0.046|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.053|   0.006) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround-extra1 supported.
(   0.054|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0,1
(   0.054|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0,1: No such file or directory
(   0.054|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x22e7b00, direction=1
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-1 (HDMI / DisplayPort 2), direction=1, priority=58, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=7, alsa_name='HDMI/DP,pcm=7 Jack', detection possible
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-mono - will not be able to open input:analog-mono
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-stereo - will not be able to open input:analog-stereo
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra1
(   0.054|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 2) (hdmi-surround71-extra1)
(   0.054|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.054|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0,1
(   0.054|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 92 ms
(   0.061|   0.006) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround71-extra1 supported.
(   0.062|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0,1
(   0.062|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0,1: No such file or directory
(   0.062|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x228ae20, direction=1
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-1 (HDMI / DisplayPort 2), direction=1, priority=58, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=7, alsa_name='HDMI/DP,pcm=7 Jack', detection possible
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:analog-mono - will not be able to open input:analog-mono
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:analog-stereo - will not be able to open input:analog-stereo
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra1
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 2/DTS) (hdmi-dts-surround-extra1)
(   0.062|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.062|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,1
(   0.062|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,1: No such file or directory
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra1
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra1
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra1
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra1
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2
(   0.062|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 3) (hdmi-stereo-extra2)
(   0.062|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.062|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0,2
(   0.062|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.069|   0.006) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-stereo-extra2 supported.
(   0.070|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/hdmi-output-2.conf'
(   0.070|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0,2
(   0.070|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0,2: No such file or directory
(   0.070|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'hdmi-output-2'
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'HDMI/DP,pcm=8 Jack' succeeded (found!)
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x22eb6d0, direction=1
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-2 (HDMI / DisplayPort 3), direction=1, priority=57, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=8, alsa_name='HDMI/DP,pcm=8 Jack', detection possible
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-mono - will not be able to open input:analog-mono
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-stereo - will not be able to open input:analog-stereo
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra2
(   0.070|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 3) (hdmi-surround-extra2)
(   0.070|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.070|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0,2
(   0.070|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.077|   0.006) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround-extra2 supported.
(   0.078|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0,2
(   0.078|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0,2: No such file or directory
(   0.078|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x22ebbb0, direction=1
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-2 (HDMI / DisplayPort 3), direction=1, priority=57, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=8, alsa_name='HDMI/DP,pcm=8 Jack', detection possible
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-mono - will not be able to open input:analog-mono
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-stereo - will not be able to open input:analog-stereo
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra2
(   0.078|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 3) (hdmi-surround71-extra2)
(   0.078|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.078|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0,2
(   0.078|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 92 ms
(   0.085|   0.007) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround71-extra2 supported.
(   0.086|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0,2
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0,2: No such file or directory
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x22ecd70, direction=1
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-2 (HDMI / DisplayPort 3), direction=1, priority=57, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=8, alsa_name='HDMI/DP,pcm=8 Jack', detection possible
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:analog-mono - will not be able to open input:analog-mono
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:analog-stereo - will not be able to open input:analog-stereo
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra2
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 3/DTS) (hdmi-dts-surround-extra2)
(   0.086|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.086|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,2
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,2: No such file or directory
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra2
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra2
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra2
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra2
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 4) (hdmi-stereo-extra3)
(   0.086|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.086|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-mono - will not be able to open output:hdmi-stereo-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-stereo - will not be able to open output:hdmi-stereo-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 4) (hdmi-surround-extra3)
(   0.086|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.086|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-mono - will not be able to open output:hdmi-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 4) (hdmi-surround71-extra3)
(   0.086|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.086|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D9p' failed (-2)
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,3: No such file or directory
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:analog-mono - will not be able to open output:hdmi-surround71-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:analog-stereo - will not be able to open output:hdmi-surround71-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 4/DTS) (hdmi-dts-surround-extra3)
(   0.086|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.086|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,3
(   0.086|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,3: No such file or directory
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra3
(   0.086|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra3
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 5) (hdmi-stereo-extra4)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D10p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,4: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:analog-mono - will not be able to open output:hdmi-stereo-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:analog-stereo - will not be able to open output:hdmi-stereo-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 5) (hdmi-surround-extra4)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D10p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,4: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:analog-mono - will not be able to open output:hdmi-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:analog-stereo - will not be able to open output:hdmi-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:iec958-stereo - will not be able to open output:hdmi-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 5) (hdmi-surround71-extra4)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D10p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,4: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:analog-mono - will not be able to open output:hdmi-surround71-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:analog-stereo - will not be able to open output:hdmi-surround71-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 5/DTS) (hdmi-dts-surround-extra4)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,4
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,4: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra4
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 6) (hdmi-stereo-extra5)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D11p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,5: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:analog-mono - will not be able to open output:hdmi-stereo-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:analog-stereo - will not be able to open output:hdmi-stereo-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 6) (hdmi-surround-extra5)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D11p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,5: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:analog-mono - will not be able to open output:hdmi-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:analog-stereo - will not be able to open output:hdmi-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:iec958-stereo - will not be able to open output:hdmi-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 6) (hdmi-surround71-extra5)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D11p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,5: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:analog-mono - will not be able to open output:hdmi-surround71-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:analog-stereo - will not be able to open output:hdmi-surround71-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 6/DTS) (hdmi-dts-surround-extra5)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,5
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,5: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra5
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra6
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 7) (hdmi-stereo-extra6)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.087|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D12p' failed (-2)
(   0.087|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,6: No such file or directory
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra6
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:analog-mono - will not be able to open output:hdmi-stereo-extra6
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:analog-stereo - will not be able to open output:hdmi-stereo-extra6
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra6
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra6
(   0.087|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 7) (hdmi-surround-extra6)
(   0.087|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D12p' failed (-2)
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,6: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:analog-mono - will not be able to open output:hdmi-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:analog-stereo - will not be able to open output:hdmi-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:iec958-stereo - will not be able to open output:hdmi-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 7) (hdmi-surround71-extra6)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D12p' failed (-2)
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,6: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:analog-mono - will not be able to open output:hdmi-surround71-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:analog-stereo - will not be able to open output:hdmi-surround71-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 7/DTS) (hdmi-dts-surround-extra6)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,6
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,6: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 8) (hdmi-stereo-extra7)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D13p' failed (-2)
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,7: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:analog-mono - will not be able to open output:hdmi-stereo-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:analog-stereo - will not be able to open output:hdmi-stereo-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 8) (hdmi-surround-extra7)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D13p' failed (-2)
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,7: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:analog-mono - will not be able to open output:hdmi-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:analog-stereo - will not be able to open output:hdmi-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:iec958-stereo - will not be able to open output:hdmi-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 8) (hdmi-surround71-extra7)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D13p' failed (-2)
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:0,7: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:analog-mono - will not be able to open output:hdmi-surround71-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:analog-stereo - will not be able to open output:hdmi-surround71-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 8/DTS) (hdmi-dts-surround-extra7)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:0,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:0,7
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:0,7: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Multichannel (multichannel)
(   0.088|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.088|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D0c' failed (-2)
(   0.088|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hw:0: No such file or directory
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:multichannel - will not be able to open output:analog-mono
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-stereo+input:multichannel - will not be able to open output:analog-stereo
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-21+input:multichannel - will not be able to open output:analog-surround-21
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-40+input:multichannel - will not be able to open output:analog-surround-40
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-41+input:multichannel - will not be able to open output:analog-surround-41
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-50+input:multichannel - will not be able to open output:analog-surround-50
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-51+input:multichannel - will not be able to open output:analog-surround-51
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:multichannel - will not be able to open output:analog-surround-71
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-stereo+input:multichannel - will not be able to open output:iec958-stereo
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:multichannel - will not be able to open output:iec958-ac3-surround-40
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:multichannel - will not be able to open output:iec958-ac3-surround-51
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:multichannel - will not be able to open output:iec958-dts-surround-51
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:multichannel - will not be able to open output:hdmi-dts-surround
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:multichannel - will not be able to open output:hdmi-dts-surround-extra1
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:multichannel - will not be able to open input:multichannel
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:multichannel - will not be able to open output:hdmi-dts-surround-extra2
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:multichannel - will not be able to open output:hdmi-stereo-extra3
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:multichannel - will not be able to open output:hdmi-surround-extra3
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:multichannel - will not be able to open output:hdmi-surround71-extra3
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:multichannel - will not be able to open output:hdmi-dts-surround-extra3
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:multichannel - will not be able to open output:hdmi-stereo-extra4
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:multichannel - will not be able to open output:hdmi-surround-extra4
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:multichannel - will not be able to open output:hdmi-surround71-extra4
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:multichannel - will not be able to open output:hdmi-dts-surround-extra4
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:multichannel - will not be able to open output:hdmi-stereo-extra5
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:multichannel - will not be able to open output:hdmi-surround-extra5
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:multichannel - will not be able to open output:hdmi-surround71-extra5
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:multichannel - will not be able to open output:hdmi-dts-surround-extra5
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:multichannel - will not be able to open output:hdmi-stereo-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:multichannel - will not be able to open output:hdmi-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:multichannel - will not be able to open output:hdmi-surround71-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:multichannel - will not be able to open output:hdmi-dts-surround-extra6
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:multichannel - will not be able to open output:hdmi-stereo-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:multichannel - will not be able to open output:hdmi-surround-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:multichannel - will not be able to open output:hdmi-surround71-extra7
(   0.088|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:multichannel - will not be able to open output:hdmi-dts-surround-extra7
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) flist.c: pulsecore/idxset.c: entries flist is full (don't worry)
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile set 0x21a05f0, auto_profiles=yes, probed=yes, n_mappings=9, n_profiles=9, n_decibel_fixes=0
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-stereo (Digital Stereo (HDMI)), priority=54, channel_map=front-left,front-right, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-surround (Digital Surround 5.1 (HDMI)), priority=3, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-surround71 (Digital Surround 7.1 (HDMI)), priority=3, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-stereo-extra1 (Digital Stereo (HDMI 2)), priority=52, channel_map=front-left,front-right, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-surround-extra1 (Digital Surround 5.1 (HDMI 2)), priority=1, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-surround71-extra1 (Digital Surround 7.1 (HDMI 2)), priority=1, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-stereo-extra2 (Digital Stereo (HDMI 3)), priority=52, channel_map=front-left,front-right, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-surround-extra2 (Digital Surround 5.1 (HDMI 3)), priority=1, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping hdmi-surround71-extra2 (Digital Surround 7.1 (HDMI 3)), priority=1, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right, supported=yes, direction=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-stereo (Digital Stereo (HDMI) Output), priority=5400, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-stereo
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround (Digital Surround 5.1 (HDMI) Output), priority=300, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-surround
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround71 (Digital Surround 7.1 (HDMI) Output), priority=300, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-surround71
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-stereo-extra1 (Digital Stereo (HDMI 2) Output), priority=5200, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-stereo-extra1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround-extra1 (Digital Surround 5.1 (HDMI 2) Output), priority=100, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-surround-extra1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround71-extra1 (Digital Surround 7.1 (HDMI 2) Output), priority=100, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-surround71-extra1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-stereo-extra2 (Digital Stereo (HDMI 3) Output), priority=5200, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-stereo-extra2
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround-extra2 (Digital Surround 5.1 (HDMI 3) Output), priority=100, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-surround-extra2
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:hdmi-surround71-extra2 (Digital Surround 7.1 (HDMI 3) Output), priority=100, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.089|   0.000) D: (pulseaudio) alsa-mixer.c: Output hdmi-surround71-extra2
(   0.089|   0.000) I: (pulseaudio) module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_00_03.0.
(   0.089|   0.000) I: (pulseaudio) card.c: Created 0 "alsa_card.pci-0000_00_03.0"
(   0.089|   0.000) D: (pulseaudio) module-alsa-card.c: Found 3 jacks.
(   0.089|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.089|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'HDMI/DP,pcm=3 Jack' is now unplugged
(   0.089|   0.000) D: (pulseaudio) device-port.c: Setting port hdmi-output-0 to status no
(   0.089|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.089|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'HDMI/DP,pcm=7 Jack' is now unplugged
(   0.089|   0.000) D: (pulseaudio) device-port.c: Setting port hdmi-output-1 to status no
(   0.089|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.089|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'HDMI/DP,pcm=8 Jack' is now unplugged
(   0.089|   0.000) D: (pulseaudio) device-port.c: Setting port hdmi-output-2 to status no
(   0.089|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.089|   0.000) D: (pulseaudio) reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
(   0.089|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
(   0.090|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hdmi:0
(   0.090|   0.000) I: (pulseaudio) alsa-util.c: Trying to disable ALSA period wakeups, using timers only
(   0.090|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.097|   0.007) D: (pulseaudio) alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.098|   0.000) I: (pulseaudio) alsa-util.c: ALSA period wakeups disabled
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Successfully opened device hdmi:0.
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Selected mapping 'Digital Stereo (HDMI)' (hdmi-stereo).
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Successfully enabled mmap() mode.
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Successfully enabled timer-based scheduling mode.
(   0.098|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL hdmi:0
(   0.098|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer hdmi:0: No such file or directory
(   0.098|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:0'
(   0.098|   0.000) D: (pulseaudio) alsa-mixer.c: Added 1 ports
(   0.098|   0.000) I: (pulseaudio) module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_03.0.hdmi-stereo.
(   0.098|   0.000) D: (pulseaudio) module-switch-on-port-available.c: Switching initial port for sink 'alsa_output.pci-0000_00_03.0.hdmi-stereo' to 'hdmi-output-0'
(   0.098|   0.000) I: (pulseaudio) sink.c: Created sink 0 "alsa_output.pci-0000_00_03.0.hdmi-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.resolution_bits = "16"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.api = "alsa"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.class = "sound"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.class = "generic"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.subclass = "generic-mix"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.name = "HDMI 0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.id = "HDMI 0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.subdevice = "0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.subdevice_name = "subdevice #0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.device = "3"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.card = "0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.card_name = "HDA Intel HDMI"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.long_card_name = "HDA Intel HDMI at 0xefd34000 irq 30"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.driver_name = "snd_hda_intel"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.bus_path = "pci-0000:00:03.0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.bus = "pci"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.vendor.id = "8086"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.vendor.name = "Intel Corporation"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.product.id = "0c0c"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.product.name = "Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.form_factor = "internal"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.string = "hdmi:0"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.buffering.buffer_size = "65536"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.buffering.fragment_size = "32768"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.access_mode = "mmap+timer"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.profile.name = "hdmi-stereo"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.profile.description = "Digital Stereo (HDMI)"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.description = "Built-in Audio Digital Stereo (HDMI)"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.mixer_name = "Intel Haswell HDMI"
(   0.098|   0.000) I: (pulseaudio) sink.c:     alsa.components = "HDA:80862807,80860101,00100000"
(   0.098|   0.000) I: (pulseaudio) sink.c:     module-udev-detect.discovered = "1"
(   0.098|   0.000) I: (pulseaudio) sink.c:     device.icon_name = "audio-card-pci"
(   0.098|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.098|   0.000) I: (pulseaudio) source.c: Created source 0 "alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.098|   0.000) I: (pulseaudio) source.c:     device.description = "Monitor of Built-in Audio Digital Stereo (HDMI)"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.class = "monitor"
(   0.098|   0.000) I: (pulseaudio) source.c:     alsa.card = "0"
(   0.098|   0.000) I: (pulseaudio) source.c:     alsa.card_name = "HDA Intel HDMI"
(   0.098|   0.000) I: (pulseaudio) source.c:     alsa.long_card_name = "HDA Intel HDMI at 0xefd34000 irq 30"
(   0.098|   0.000) I: (pulseaudio) source.c:     alsa.driver_name = "snd_hda_intel"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.bus_path = "pci-0000:00:03.0"
(   0.098|   0.000) I: (pulseaudio) source.c:     sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.bus = "pci"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.vendor.id = "8086"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.vendor.name = "Intel Corporation"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.product.id = "0c0c"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.product.name = "Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.form_factor = "internal"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.string = "0"
(   0.098|   0.000) I: (pulseaudio) source.c:     module-udev-detect.discovered = "1"
(   0.098|   0.000) I: (pulseaudio) source.c:     device.icon_name = "audio-card-pci"
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Using 2,0 fragments of size 32768 bytes (185,76ms), buffer size is 65536 bytes (371,52ms)
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Time scheduling watermark is 20,00ms
(   0.098|   0.000) D: (pulseaudio) alsa-sink.c: hwbuf_unused=0
(   0.098|   0.000) D: (pulseaudio) alsa-sink.c: setting avail_min=15502
(   0.098|   0.000) D: (pulseaudio) alsa-mixer.c: Activating path hdmi-output-0
(   0.098|   0.000) D: (pulseaudio) alsa-mixer.c: Path hdmi-output-0 (HDMI / DisplayPort), direction=1, priority=59, probed=yes, supported=yes, has_mute=no, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.098|   0.000) D: (pulseaudio) alsa-mixer.c: Jack HDMI/DP,pcm=3, alsa_name='HDMI/DP,pcm=3 Jack', detection possible
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Driver does not support hardware volume control, falling back to software volume control.
(   0.098|   0.000) I: (pulseaudio) alsa-sink.c: Driver does not support hardware mute control, falling back to software mute control.
(   0.098|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_dump():
(   0.098|   0.000) D: (pulseaudio) alsa-util.c: Hooks PCM
(   0.098|   0.000) D: (pulseaudio) alsa-util.c: Its setup is:
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   stream       : PLAYBACK
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   format       : S16_LE
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   subformat    : STD
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   channels     : 2
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   rate         : 44100
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   msbits       : 16
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   buffer_size  : 16384
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_size  : 8192
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_time  : 185759
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_mode  : ENABLE
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_type  : MONOTONIC
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_step  : 1
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   avail_min    : 15502
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_event : 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   start_threshold  : -1
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   silence_threshold: 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   silence_size : 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   boundary     : 4611686018427387904
(   0.098|   0.000) D: (pulseaudio) alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel HDMI' device 3 subdevice 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c: Its setup is:
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   stream       : PLAYBACK
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   format       : S16_LE
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   subformat    : STD
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   channels     : 2
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   rate         : 44100
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   msbits       : 16
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   buffer_size  : 16384
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_size  : 8192
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_time  : 185759
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_mode  : ENABLE
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_type  : MONOTONIC
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_step  : 1
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   avail_min    : 15502
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   period_event : 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   start_threshold  : -1
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   silence_threshold: 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   silence_size : 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   boundary     : 4611686018427387904
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   appl_ptr     : 0
(   0.098|   0.000) D: (pulseaudio) alsa-util.c:   hw_ptr       : 0
(   0.099|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Thread starting up
(   0.100|   0.001) D: (alsa-sink-HDMI 0) core-util.c: RealtimeKit worked.
(   0.100|   0.000) I: (alsa-sink-HDMI 0) core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.101|   0.000) I: (alsa-sink-HDMI 0) alsa-sink.c: Starting playback.
(   0.101|   0.000) D: (pulseaudio) alsa-util.c: ELD info empty (for device=3)
(   0.101|   0.000) D: (pulseaudio) alsa-util.c: ELD info empty (for device=7)
(   0.101|   0.000) D: (pulseaudio) alsa-util.c: ELD info empty (for device=8)
(   0.101|   0.000) I: (pulseaudio) module.c: Loaded "module-alsa-card" (index: #6; argument: "device_id="0" name="pci-0000_00_03.0" card_name="alsa_card.pci-0000_00_03.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
(   0.101|   0.000) I: (pulseaudio) module-udev-detect.c: Card /devices/pci0000:00/0000:00:03.0/sound/card0 (alsa_card.pci-0000_00_03.0) module loaded.
(   0.101|   0.000) D: (pulseaudio) module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
(   0.101|   0.000) D: (pulseaudio) module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card1 is busy: no
(   0.101|   0.000) D: (pulseaudio) module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"'
(   0.101|   0.000) D: (pulseaudio) reserve-wrap.c: Successfully acquired reservation lock on device 'Audio1'
(   0.101|   0.000) I: (pulseaudio) (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/HDA Intel PCH/HDA Intel PCH.conf
(   0.101|   0.000) I: (pulseaudio) (alsa-lib)parser.c: error: could not parse configuration for card HDA Intel PCH
(   0.101|   0.000) I: (pulseaudio) (alsa-lib)main.c: error: failed to import HDA Intel PCH use case configuration -2
(   0.101|   0.000) I: (pulseaudio) alsa-ucm.c: UCM not available for card HDA Intel PCH
(   0.101|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/profile-sets/default.conf'
(   0.102|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:analog-mono
(   0.102|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Mono (analog-mono)
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hw:1
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hw:1
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:hw:1
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:hw:1
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.102|   0.000) I: (pulseaudio) alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.102|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open input:analog-mono
(   0.102|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:analog-stereo
(   0.102|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.102|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.103|   0.000) D: (pulseaudio) alsa-mixer.c: Profile input:analog-stereo supported.
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-front-mic.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-rear-mic.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-internal-mic.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-dock-mic.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-linein.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-aux.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-video.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-tvtuner.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-fm.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic-line.conf'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input.conf.common'
(   0.103|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.104|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headphone-mic.conf'
(   0.104|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.104|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-headset-mic.conf'
(   0.104|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-input-mic.conf.common'
(   0.104|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL front:1
(   0.104|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.104|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-front-mic'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (found!)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Front Mic Phantom Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=1, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-rear-mic'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (found!)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Rear Mic Phantom Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=1, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-internal-mic'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Front Mic Jack' succeeded (found!)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Rear Mic Jack' succeeded (found!)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Internal Mic Phantom Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Int Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Int Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping path 'analog-input-internal-mic', none of required-any elements preset.
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-dock-mic'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Dock Mic Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Dock Mic Phantom Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping path 'analog-input-dock-mic', none of required-any elements preset.
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' failed.
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-mic'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Mic Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Mic Phantom Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Select' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost (+20dB)' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping path 'analog-input-mic', none of required-any elements preset.
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-linein'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Jack' succeeded (found!)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Phantom Jack' succeeded (not found)
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=1, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-aux'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' failed.
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-video'
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.104|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' failed.
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-tvtuner'
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' failed.
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-fm'
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' failed.
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-mic-line'
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' failed.
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-headphone-mic'
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Auto-Mute Mode' succeeded (volume=0, switch=0, enumeration=1).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping path 'analog-input-headphone-mic', none of required-any elements preset.
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-input-headset-mic'
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headset Mic Jack' succeeded (not found)
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headset Mic Phantom Jack' succeeded (not found)
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture' succeeded (volume=1, switch=1, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headset Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headset Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headset' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Input Source' succeeded (volume=0, switch=0, enumeration=1).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Capture Source' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Dock Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Internal Mic Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear Mic Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line Boost' succeeded (volume=2, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Aux' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Video' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic/Line' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'TV Tuner' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'FM' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Inverted Internal Mic' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Mic Jack Mode' succeeded (volume=0, switch=0, enumeration=0).
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping path 'analog-input-headset-mic', none of required-any elements preset.
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x21eb8b0, direction=2
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-input-front-mic (Front Microphone), direction=2, priority=85, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=46, min_dB=-16, max_dB=60
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Option Front Mic (analog-input-microphone-front/analog-input-microphone-front) index=0, priority=0
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Rear Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Line Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Front Mic, alsa_name='Front Mic Jack', detection possible
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Front Mic Phantom, alsa_name='Front Mic Phantom Jack', detection unavailable
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Setting analog-input-microphone-front (analog-input-microphone-front) priority=0
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-input-rear-mic (Rear Microphone), direction=2, priority=82, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=46, min_dB=-16, max_dB=60
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Rear Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Option Rear Mic (analog-input-microphone-rear/analog-input-microphone-rear) index=1, priority=0
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Line Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Rear Mic, alsa_name='Rear Mic Jack', detection possible
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Rear Mic Phantom, alsa_name='Rear Mic Phantom Jack', detection unavailable
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Setting analog-input-microphone-rear (analog-input-microphone-rear) priority=0
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-input-linein (Line In), direction=2, priority=81, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=46, min_dB=-16, max_dB=60
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Line Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Option Line (analog-input-linein/analog-input-linein) index=2, priority=0
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Element Rear Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line, alsa_name='Line Jack', detection possible
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Phantom, alsa_name='Line Phantom Jack', detection unavailable
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Setting analog-input-linein (analog-input-linein) priority=0
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile input:iec958-stereo
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D1c' failed (-2)
(   0.105|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device iec958:1: No such file or directory
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open input:iec958-stereo
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-mono
(   0.105|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Mono (analog-mono)
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hw:1
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Trying hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Managed to open hw:1
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:hw:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:hw:1
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:hw:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.105|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:hw:1
(   0.106|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
(   0.106|   0.000) I: (pulseaudio) alsa-util.c: Failed to set hardware parameters on plug:hw:1: Invalid argument
(   0.106|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-mono
(   0.106|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:analog-mono - will not be able to open output:analog-mono
(   0.106|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:analog-stereo - will not be able to open output:analog-mono
(   0.106|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-mono+input:iec958-stereo - will not be able to open output:analog-mono
(   0.106|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-stereo
(   0.106|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Stereo (analog-stereo)
(   0.106|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.106|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.106|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.137|   0.031) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.137|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-stereo supported.
(   0.137|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf'
(   0.137|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common'
(   0.137|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output-lineout.conf'
(   0.137|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common'
(   0.138|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output-speaker.conf'
(   0.138|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common'
(   0.138|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf'
(   0.138|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common'
(   0.138|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones-2.conf'
(   0.138|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common'
(   0.138|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL front:1
(   0.138|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.138|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-output'
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Surround' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Center' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'LFE' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-output-lineout'
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Front Jack' succeeded (found!)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Front Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out CLFE Jack' succeeded (found!)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out CLFE Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Surround Jack' succeeded (found!)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Surround Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Side Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Side Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=2, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Surround' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Center' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'LFE' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-output-speaker'
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Dock Headphone Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (found!)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Line Out Front Jack' succeeded (found!)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Speaker Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Speaker Front Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=2, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Surround' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Surround Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Center' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Center Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'LFE' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'LFE Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping path 'analog-output-speaker', none of required-any elements preset.
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-output-headphones'
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Dock Headphone Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Dock Headphone Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Front Headphone Jack' succeeded (found!)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Front Headphone Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Phantom Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of jack 'Headphone Mic Jack' succeeded (not found)
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headset' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Line HP Swap' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone2' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Desktop Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Front' succeeded (volume=3, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Rear' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Surround' succeeded (volume=2, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Center' succeeded (volume=2, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'LFE' succeeded (volume=2, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Speaker' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Front' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Surround' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker Side' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker CLFE' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'PCM' succeeded (volume=1, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'External Amplifier' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Bass Boost' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=2, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958 Optical Raw' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Analog Output' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'analog-output-headphones-2'
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Hardware Master' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master' succeeded (volume=1, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Master Mono' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone' succeeded (volume=3, switch=1, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Speaker+LO' succeeded (volume=0, switch=0, enumeration=0).
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'Headphone2' failed.
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-lineout'.
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x23137d0, direction=1
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-lineout (Line Out), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.138|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out, alsa_name='Line Out Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Phantom, alsa_name='Line Out Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front, alsa_name='Line Out Front Jack', detection possible
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front Phantom, alsa_name='Line Out Front Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE, alsa_name='Line Out CLFE Jack', detection possible
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE Phantom, alsa_name='Line Out CLFE Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround, alsa_name='Line Out Surround Jack', detection possible
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround Phantom, alsa_name='Line Out Surround Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side, alsa_name='Line Out Side Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side Phantom, alsa_name='Line Out Side Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-headphones (Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=3, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Dock Headphone, alsa_name='Dock Headphone Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Dock Headphone Phantom, alsa_name='Dock Headphone Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Front Headphone, alsa_name='Front Headphone Jack', detection possible
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Front Headphone Phantom, alsa_name='Front Headphone Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone Phantom, alsa_name='Headphone Phantom Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone Mic, alsa_name='Headphone Mic Jack', detection unavailable
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-stereo+input:analog-mono - will not be able to open input:analog-mono
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-stereo+input:analog-stereo
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo supported.
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-21
(   0.139|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 2.1 (analog-surround-21)
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Trying surround21:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround21:1
(   0.139|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.169|   0.030) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.169|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-21 supported.
(   0.169|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL surround21:1
(   0.169|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer surround21:1: No such file or directory
(   0.169|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.169|   0.000) D: (pulseaudio) alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-lineout'.
(   0.169|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.169|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2310990, direction=1
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-lineout (Line Out), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out, alsa_name='Line Out Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Phantom, alsa_name='Line Out Phantom Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front, alsa_name='Line Out Front Jack', detection possible
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front Phantom, alsa_name='Line Out Front Phantom Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE, alsa_name='Line Out CLFE Jack', detection possible
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE Phantom, alsa_name='Line Out CLFE Phantom Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround, alsa_name='Line Out Surround Jack', detection possible
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround Phantom, alsa_name='Line Out Surround Phantom Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side, alsa_name='Line Out Side Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side Phantom, alsa_name='Line Out Side Phantom Jack', detection unavailable
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-21+input:analog-mono - will not be able to open input:analog-mono
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-21+input:analog-stereo
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-21+input:analog-stereo supported.
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-21+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-40
(   0.170|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 4.0 (analog-surround-40)
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Trying surround40:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround40:1
(   0.170|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 185 ms
(   0.201|   0.031) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.201|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-40 supported.
(   0.201|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL surround40:1
(   0.201|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer surround40:1: No such file or directory
(   0.201|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.201|   0.000) D: (pulseaudio) alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-lineout'.
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2366470, direction=1
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-lineout (Line Out), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out, alsa_name='Line Out Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Phantom, alsa_name='Line Out Phantom Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front, alsa_name='Line Out Front Jack', detection possible
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front Phantom, alsa_name='Line Out Front Phantom Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE, alsa_name='Line Out CLFE Jack', detection possible
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE Phantom, alsa_name='Line Out CLFE Phantom Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround, alsa_name='Line Out Surround Jack', detection possible
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround Phantom, alsa_name='Line Out Surround Phantom Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side, alsa_name='Line Out Side Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side Phantom, alsa_name='Line Out Side Phantom Jack', detection unavailable
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-40+input:analog-mono - will not be able to open input:analog-mono
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-40+input:analog-stereo
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-40+input:analog-stereo supported.
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-40+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-41
(   0.202|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 4.1 (analog-surround-41)
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Trying surround41:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround41:1
(   0.202|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.233|   0.031) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-41 supported.
(   0.233|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL surround41:1
(   0.233|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer surround41:1: No such file or directory
(   0.233|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-lineout'.
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2335240, direction=1
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-lineout (Line Out), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
(   0.233|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out, alsa_name='Line Out Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Phantom, alsa_name='Line Out Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front, alsa_name='Line Out Front Jack', detection possible
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front Phantom, alsa_name='Line Out Front Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE, alsa_name='Line Out CLFE Jack', detection possible
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE Phantom, alsa_name='Line Out CLFE Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround, alsa_name='Line Out Surround Jack', detection possible
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround Phantom, alsa_name='Line Out Surround Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side, alsa_name='Line Out Side Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side Phantom, alsa_name='Line Out Side Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-41+input:analog-mono - will not be able to open input:analog-mono
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-41+input:analog-stereo
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-41+input:analog-stereo supported.
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-41+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-50
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 5.0 (analog-surround-50)
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Trying surround50:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround50:1
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-50 supported.
(   0.234|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL surround50:1
(   0.234|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer surround50:1: No such file or directory
(   0.234|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-lineout'.
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2310d90, direction=1
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-lineout (Line Out), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out, alsa_name='Line Out Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Phantom, alsa_name='Line Out Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front, alsa_name='Line Out Front Jack', detection possible
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front Phantom, alsa_name='Line Out Front Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE, alsa_name='Line Out CLFE Jack', detection possible
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE Phantom, alsa_name='Line Out CLFE Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround, alsa_name='Line Out Surround Jack', detection possible
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround Phantom, alsa_name='Line Out Surround Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side, alsa_name='Line Out Side Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side Phantom, alsa_name='Line Out Side Phantom Jack', detection unavailable
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-50+input:analog-mono - will not be able to open input:analog-mono
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-50+input:analog-stereo
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.234|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-50+input:analog-stereo supported.
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-50+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-51
(   0.234|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 5.1 (analog-surround-51)
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Trying surround51:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround51:1
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 123 ms
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-51 supported.
(   0.235|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL surround51:1
(   0.235|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer surround51:1: No such file or directory
(   0.235|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Removing path 'analog-output' as it is a subset of 'analog-output-lineout'.
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2319980, direction=1
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-output-lineout (Line Out), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-179, max_dB=0
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element Headphone, direction=1, switch=2, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=yes
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element Surround, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x60, n_channels=2, override_map=yes
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element Center, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x4900000000018, n_channels=1, override_map=yes
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element LFE, direction=1, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x80, n_channels=1, override_map=yes
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=2, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out, alsa_name='Line Out Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Phantom, alsa_name='Line Out Phantom Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Headphone, alsa_name='Headphone Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front, alsa_name='Line Out Front Jack', detection possible
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Front Phantom, alsa_name='Line Out Front Phantom Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE, alsa_name='Line Out CLFE Jack', detection possible
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out CLFE Phantom, alsa_name='Line Out CLFE Phantom Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround, alsa_name='Line Out Surround Jack', detection possible
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Surround Phantom, alsa_name='Line Out Surround Phantom Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side, alsa_name='Line Out Side Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Line Out Side Phantom, alsa_name='Line Out Side Phantom Jack', detection unavailable
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-51+input:analog-mono - will not be able to open input:analog-mono
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-51+input:analog-stereo
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-51+input:analog-stereo supported.
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-51+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:analog-surround-71
(   0.235|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Analog Surround 7.1 (analog-surround-71)
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Trying surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround71:1
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Trying surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Managed to open surround71:1
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.235|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:surround71:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:surround71:1
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:surround71:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:surround71:1
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(8) failed: Invalid argument
(   0.236|   0.000) I: (pulseaudio) alsa-util.c: Failed to set hardware parameters on plug:surround71:1: Invalid argument
(   0.236|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:analog-surround-71
(   0.236|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-mono - will not be able to open output:analog-surround-71
(   0.236|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:analog-stereo - will not be able to open output:analog-surround-71
(   0.236|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:analog-surround-71+input:iec958-stereo - will not be able to open output:analog-surround-71
(   0.236|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-stereo
(   0.236|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (IEC958) (iec958-stereo)
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: Trying iec958:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: Managed to open iec958:1
(   0.236|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.241|   0.005) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-stereo supported.
(   0.242|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/pulseaudio/alsa-mixer/paths/iec958-stereo-output.conf'
(   0.242|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL iec958:1
(   0.242|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer iec958:1: No such file or directory
(   0.242|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Probing path 'iec958-stereo-output'
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Probe of element 'IEC958' succeeded (volume=0, switch=1, enumeration=0).
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Available mixer paths (after tidying):
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Path Set 0x2368d90, direction=1
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Path iec958-stereo-output (Digital Output (S/PDIF)), direction=1, priority=0, probed=yes, supported=yes, has_mute=yes, has_volume=no, has_dB=no, min_volume=0, max_volume=0, min_dB=inf, max_dB=-inf
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Element IEC958, direction=1, switch=1, volume=0, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-stereo+input:analog-mono - will not be able to open input:analog-mono
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-stereo+input:analog-stereo
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo supported.
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-stereo+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-ac3-surround-40
(   0.242|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 4.0 (IEC958/AC3) (iec958-ac3-surround-40)
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Managed to open a52:1
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Trying a52:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.242|   0.000) D: (pulseaudio) alsa-util.c: Managed to open a52:1
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:a52:1
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Trying plug:a52:1 without SND_PCM_NO_AUTO_FORMAT ...
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Managed to open plug:a52:1
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_channels(4) failed: Invalid argument
(   0.243|   0.000) I: (pulseaudio) alsa-util.c: Failed to set hardware parameters on plug:a52:1: Invalid argument
(   0.243|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:iec958-ac3-surround-40
(   0.243|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-mono - will not be able to open output:iec958-ac3-surround-40
(   0.243|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:analog-stereo - will not be able to open output:iec958-ac3-surround-40
(   0.243|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-40+input:iec958-stereo - will not be able to open output:iec958-ac3-surround-40
(   0.243|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51
(   0.243|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/AC3) (iec958-ac3-surround-51)
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Managed to open a52:1
(   0.243|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 320 ms
(   0.243|   0.000) I: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_buffer_size_near() failed: Invalid argument
(   0.243|   0.000) I: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_buffer_size_near() failed: Invalid argument
(   0.243|   0.000) I: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_buffer_size_near() failed: Invalid argument
(   0.250|   0.006) D: (pulseaudio) alsa-util.c: Set only period size (to 1102 samples).
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-ac3-surround-51 supported.
(   0.250|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL a52:1
(   0.250|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer a52:1: No such file or directory
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:analog-mono - will not be able to open input:analog-mono
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-ac3-surround-51+input:analog-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 4408 samples), period size second (to 1102 samples).
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-ac3-surround-51+input:analog-stereo supported.
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-ac3-surround-51+input:iec958-stereo - will not be able to open input:iec958-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:iec958-dts-surround-51
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (IEC958/DTS) (iec958-dts-surround-51)
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Trying dca:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.250|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dca:1
(   0.250|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dca:1: No such file or directory
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:iec958-dts-surround-51
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-mono - will not be able to open output:iec958-dts-surround-51
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:analog-stereo - will not be able to open output:iec958-dts-surround-51
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:iec958-dts-surround-51+input:iec958-stereo - will not be able to open output:iec958-dts-surround-51
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI) (hdmi-stereo)
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.250|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.250|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-mono - will not be able to open output:hdmi-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:analog-stereo - will not be able to open output:hdmi-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo+input:iec958-stereo - will not be able to open output:hdmi-stereo
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI) (hdmi-surround)
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.250|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.250|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-mono - will not be able to open output:hdmi-surround
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:analog-stereo - will not be able to open output:hdmi-surround
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround+input:iec958-stereo - will not be able to open output:hdmi-surround
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI) (hdmi-surround71)
(   0.250|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.250|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D3p' failed (-2)
(   0.250|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1: No such file or directory
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:analog-mono - will not be able to open output:hdmi-surround71
(   0.250|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:analog-stereo - will not be able to open output:hdmi-surround71
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71+input:iec958-stereo - will not be able to open output:hdmi-surround71
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI/DTS) (hdmi-dts-surround)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:analog-mono - will not be able to open output:hdmi-dts-surround
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:analog-stereo - will not be able to open output:hdmi-dts-surround
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround+input:iec958-stereo - will not be able to open output:hdmi-dts-surround
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 2) (hdmi-stereo-extra1)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D7p' failed (-2)
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,1: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-mono - will not be able to open output:hdmi-stereo-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:analog-stereo - will not be able to open output:hdmi-stereo-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra1+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 2) (hdmi-surround-extra1)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D7p' failed (-2)
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,1: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-mono - will not be able to open output:hdmi-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:analog-stereo - will not be able to open output:hdmi-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra1+input:iec958-stereo - will not be able to open output:hdmi-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 2) (hdmi-surround71-extra1)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D7p' failed (-2)
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,1: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:analog-mono - will not be able to open output:hdmi-surround71-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:analog-stereo - will not be able to open output:hdmi-surround71-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra1+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 2/DTS) (hdmi-dts-surround-extra1)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,1
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,1: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra1+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra1
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 3) (hdmi-stereo-extra2)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D8p' failed (-2)
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,2: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-mono - will not be able to open output:hdmi-stereo-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:analog-stereo - will not be able to open output:hdmi-stereo-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra2+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 3) (hdmi-surround-extra2)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D8p' failed (-2)
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,2: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-mono - will not be able to open output:hdmi-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:analog-stereo - will not be able to open output:hdmi-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra2+input:iec958-stereo - will not be able to open output:hdmi-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 3) (hdmi-surround71-extra2)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D8p' failed (-2)
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,2: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:analog-mono - will not be able to open output:hdmi-surround71-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:analog-stereo - will not be able to open output:hdmi-surround71-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra2+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 3/DTS) (hdmi-dts-surround-extra2)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,2 with SND_PCM_NO_AUTO_FORMAT ...
(   0.251|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,2
(   0.251|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,2: No such file or directory
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra2+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra2
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra3
(   0.251|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 4) (hdmi-stereo-extra3)
(   0.251|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D9p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,3: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-mono - will not be able to open output:hdmi-stereo-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:analog-stereo - will not be able to open output:hdmi-stereo-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra3+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 4) (hdmi-surround-extra3)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D9p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,3: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-mono - will not be able to open output:hdmi-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 4) (hdmi-surround71-extra3)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D9p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,3: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:analog-mono - will not be able to open output:hdmi-surround71-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:analog-stereo - will not be able to open output:hdmi-surround71-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra3+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 4/DTS) (hdmi-dts-surround-extra3)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,3 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,3
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,3: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra3+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra3
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 5) (hdmi-stereo-extra4)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D10p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,4: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:analog-mono - will not be able to open output:hdmi-stereo-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:analog-stereo - will not be able to open output:hdmi-stereo-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra4+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 5) (hdmi-surround-extra4)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D10p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,4: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:analog-mono - will not be able to open output:hdmi-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:analog-stereo - will not be able to open output:hdmi-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra4+input:iec958-stereo - will not be able to open output:hdmi-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 5) (hdmi-surround71-extra4)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D10p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,4: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:analog-mono - will not be able to open output:hdmi-surround71-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:analog-stereo - will not be able to open output:hdmi-surround71-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra4+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 5/DTS) (hdmi-dts-surround-extra4)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,4 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,4
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,4: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra4+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra4
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra5
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 6) (hdmi-stereo-extra5)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.252|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D11p' failed (-2)
(   0.252|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,5: No such file or directory
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra5
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:analog-mono - will not be able to open output:hdmi-stereo-extra5
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:analog-stereo - will not be able to open output:hdmi-stereo-extra5
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra5+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra5
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra5
(   0.252|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 6) (hdmi-surround-extra5)
(   0.252|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D11p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,5: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:analog-mono - will not be able to open output:hdmi-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:analog-stereo - will not be able to open output:hdmi-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra5+input:iec958-stereo - will not be able to open output:hdmi-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 6) (hdmi-surround71-extra5)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D11p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,5: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:analog-mono - will not be able to open output:hdmi-surround71-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:analog-stereo - will not be able to open output:hdmi-surround71-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra5+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 6/DTS) (hdmi-dts-surround-extra5)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,5 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,5
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,5: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra5+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra5
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 7) (hdmi-stereo-extra6)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D12p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,6: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:analog-mono - will not be able to open output:hdmi-stereo-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:analog-stereo - will not be able to open output:hdmi-stereo-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra6+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 7) (hdmi-surround-extra6)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D12p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,6: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:analog-mono - will not be able to open output:hdmi-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:analog-stereo - will not be able to open output:hdmi-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra6+input:iec958-stereo - will not be able to open output:hdmi-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 7) (hdmi-surround71-extra6)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D12p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,6: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:analog-mono - will not be able to open output:hdmi-surround71-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:analog-stereo - will not be able to open output:hdmi-surround71-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra6+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 7/DTS) (hdmi-dts-surround-extra6)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,6 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,6
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,6: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra6+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra6
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-stereo-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Stereo (HDMI 8) (hdmi-stereo-extra7)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D13p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,7: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-stereo-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:analog-mono - will not be able to open output:hdmi-stereo-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:analog-stereo - will not be able to open output:hdmi-stereo-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-stereo-extra7+input:iec958-stereo - will not be able to open output:hdmi-stereo-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 8) (hdmi-surround-extra7)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.253|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D13p' failed (-2)
(   0.253|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,7: No such file or directory
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:analog-mono - will not be able to open output:hdmi-surround-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:analog-stereo - will not be able to open output:hdmi-surround-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround-extra7+input:iec958-stereo - will not be able to open output:hdmi-surround-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-surround71-extra7
(   0.253|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 7.1 (HDMI 8) (hdmi-surround71-extra7)
(   0.253|   0.000) D: (pulseaudio) alsa-util.c: Trying hdmi:1,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.254|   0.000) I: (pulseaudio) (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC1D13p' failed (-2)
(   0.254|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device hdmi:1,7: No such file or directory
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-surround71-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:analog-mono - will not be able to open output:hdmi-surround71-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:analog-stereo - will not be able to open output:hdmi-surround71-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-surround71-extra7+input:iec958-stereo - will not be able to open output:hdmi-surround71-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Looking at profile output:hdmi-dts-surround-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Checking for playback on Digital Surround 5.1 (HDMI 8/DTS) (hdmi-dts-surround-extra7)
(   0.254|   0.000) D: (pulseaudio) alsa-util.c: Trying dcahdmi:1,7 with SND_PCM_NO_AUTO_FORMAT ...
(   0.254|   0.000) I: (pulseaudio) (alsa-lib)pcm.c: Unknown PCM dcahdmi:1,7
(   0.254|   0.000) I: (pulseaudio) alsa-util.c: Error opening PCM device dcahdmi:1,7: No such file or directory
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Caching failure to open output:hdmi-dts-surround-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:analog-mono - will not be able to open output:hdmi-dts-surround-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:analog-stereo - will not be able to open output:hdmi-dts-surround-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Skipping profile output:hdmi-dts-surround-extra7+input:iec958-stereo - will not be able to open output:hdmi-dts-surround-extra7
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile set 0x21a3700, auto_profiles=yes, probed=yes, n_mappings=8, n_profiles=17, n_decibel_fixes=0
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping analog-stereo (Analog Stereo), priority=60, channel_map=front-left,front-right, supported=yes, direction=0
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping analog-surround-21 (Analog Surround 2.1), priority=8, channel_map=front-left,front-right,lfe, supported=yes, direction=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping analog-surround-40 (Analog Surround 4.0), priority=7, channel_map=front-left,front-right,rear-left,rear-right, supported=yes, direction=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping analog-surround-41 (Analog Surround 4.1), priority=8, channel_map=front-left,front-right,rear-left,rear-right,lfe, supported=yes, direction=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping analog-surround-50 (Analog Surround 5.0), priority=7, channel_map=front-left,front-right,rear-left,rear-right,front-center, supported=yes, direction=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping analog-surround-51 (Analog Surround 5.1), priority=8, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping iec958-stereo (Digital Stereo (IEC958)), priority=55, channel_map=front-left,front-right, supported=yes, direction=0
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Mapping iec958-ac3-surround-51 (Digital Surround 5.1 (IEC958/AC3)), priority=3, channel_map=front-left,front-right,rear-left,rear-right,front-center,lfe, supported=yes, direction=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile input:analog-stereo (Analog Stereo Input), priority=60, supported=yes n_input_mappings=1, n_output_mappings=0
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-stereo (Analog Stereo Output), priority=6000, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-stereo+input:analog-stereo (Analog Stereo Duplex), priority=6060, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-21 (Analog Surround 2.1 Output), priority=800, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-21
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-21+input:analog-stereo (Analog Surround 2.1 Output + Analog Stereo Input), priority=860, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-21
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-40 (Analog Surround 4.0 Output), priority=700, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-40
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-40+input:analog-stereo (Analog Surround 4.0 Output + Analog Stereo Input), priority=760, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-40
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-41 (Analog Surround 4.1 Output), priority=800, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-41
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-41+input:analog-stereo (Analog Surround 4.1 Output + Analog Stereo Input), priority=860, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-41
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-50 (Analog Surround 5.0 Output), priority=700, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-50
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-50+input:analog-stereo (Analog Surround 5.0 Output + Analog Stereo Input), priority=760, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-50
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-51 (Analog Surround 5.1 Output), priority=800, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-51
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:analog-surround-51+input:analog-stereo (Analog Surround 5.1 Output + Analog Stereo Input), priority=860, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output analog-surround-51
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-stereo (Digital Stereo (IEC958) Output), priority=5500, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output iec958-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-stereo+input:analog-stereo (Digital Stereo (IEC958) Output + Analog Stereo Input), priority=5560, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output iec958-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-ac3-surround-51 (Digital Surround 5.1 (IEC958/AC3) Output), priority=300, supported=yes n_input_mappings=0, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output iec958-ac3-surround-51
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Profile output:iec958-ac3-surround-51+input:analog-stereo (Digital Surround 5.1 (IEC958/AC3) Output + Analog Stereo Input), priority=360, supported=yes n_input_mappings=1, n_output_mappings=1
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Input analog-stereo
(   0.254|   0.000) D: (pulseaudio) alsa-mixer.c: Output iec958-ac3-surround-51
(   0.254|   0.000) I: (pulseaudio) module-card-restore.c: Restored profile 'output:iec958-ac3-surround-51+input:analog-stereo' for card alsa_card.pci-0000_00_1b.0.
(   0.254|   0.000) I: (pulseaudio) module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_00_1b.0.
(   0.254|   0.000) I: (pulseaudio) card.c: Created 1 "alsa_card.pci-0000_00_1b.0"
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Found 7 jacks.
(   0.254|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Line Out Front Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) device-port.c: Setting port analog-output-lineout to status no
(   0.254|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Line Out CLFE Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Line Out Surround Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Front Headphone Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) device-port.c: Setting port analog-output-headphones to status no
(   0.254|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Front Mic Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) device-port.c: Setting port analog-input-front-mic to status no
(   0.254|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Rear Mic Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) device-port.c: Setting port analog-input-rear-mic to status no
(   0.254|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.254|   0.000) D: (pulseaudio) module-alsa-card.c: Jack 'Line Jack' is now unplugged
(   0.254|   0.000) D: (pulseaudio) device-port.c: Setting port analog-input-linein to status no
(   0.254|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.255|   0.000) D: (pulseaudio) reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio1'
(   0.255|   0.000) D: (pulseaudio) alsa-util.c: Trying a52:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.255|   0.000) D: (pulseaudio) alsa-util.c: Managed to open a52:1
(   0.255|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 320 ms
(   0.255|   0.000) I: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_buffer_size_near() failed: Invalid argument
(   0.255|   0.000) I: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_buffer_size_near() failed: Invalid argument
(   0.255|   0.000) I: (pulseaudio) alsa-util.c: snd_pcm_hw_params_set_buffer_size_near() failed: Invalid argument
(   0.255|   0.000) D: (pulseaudio) alsa-util.c: Set only period size (to 1102 samples).
(   0.255|   0.000) I: (pulseaudio) alsa-sink.c: Successfully opened device a52:1.
(   0.255|   0.000) I: (pulseaudio) alsa-sink.c: Selected mapping 'Digital Surround 5.1 (IEC958/AC3)' (iec958-ac3-surround-51).
(   0.255|   0.000) I: (pulseaudio) alsa-sink.c: Cannot enable timer-based scheduling, falling back to sound IRQ scheduling.
(   0.255|   0.000) I: (pulseaudio) alsa-sink.c: Successfully enabled mmap() mode.
(   0.256|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL a52:1
(   0.256|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer a52:1: No such file or directory
(   0.256|   0.000) I: (pulseaudio) alsa-sink.c: Failed to find a working mixer device.
(   0.256|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.256|   0.000) I: (pulseaudio) module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51: front-left: 42981 /  66%,   front-right: 42981 /  66%,   rear-left: 42981 /  66%,   rear-right: 42981 /  66%,   front-center: 42981 /  66%,   lfe: 42981 /  66%
(   0.256|   0.000) I: (pulseaudio) sink.c: Created sink 1 "alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51" with sample spec s16le 6ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.resolution_bits = "16"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.api = "alsa"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.class = "sound"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.class = "generic"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.subclass = "generic-mix"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.name = ""
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.id = ""
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.subdevice = "0"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.subdevice_name = ""
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.device = "0"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.string = "a52:1"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.buffering.buffer_size = "169344"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.buffering.fragment_size = "16932"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.access_mode = "mmap"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.profile.name = "iec958-ac3-surround-51"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.profile.description = "Digital Surround 5.1 (IEC958/AC3)"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.description = "Built-in Audio Digital Surround 5.1 (IEC958/AC3)"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.card = "1"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.card_name = "HDA Intel PCH"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.long_card_name = "HDA Intel PCH at 0xefd30000 irq 29"
(   0.256|   0.000) I: (pulseaudio) sink.c:     alsa.driver_name = "snd_hda_intel"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.bus_path = "pci-0000:00:1b.0"
(   0.256|   0.000) I: (pulseaudio) sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.bus = "pci"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.vendor.id = "8086"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.vendor.name = "Intel Corporation"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.product.id = "8ca0"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.product.name = "9 Series Chipset Family HD Audio Controller"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.form_factor = "internal"
(   0.256|   0.000) I: (pulseaudio) sink.c:     module-udev-detect.discovered = "1"
(   0.256|   0.000) I: (pulseaudio) sink.c:     device.icon_name = "audio-card-pci"
(   0.256|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.256|   0.000) I: (pulseaudio) source.c: Created source 1 "alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51.monitor" with sample spec s16le 6ch 44100Hz and channel map front-left,front-right,rear-left,rear-right,front-center,lfe
(   0.256|   0.000) I: (pulseaudio) source.c:     device.description = "Monitor of Built-in Audio Digital Surround 5.1 (IEC958/AC3)"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.class = "monitor"
(   0.256|   0.000) I: (pulseaudio) source.c:     alsa.card = "1"
(   0.256|   0.000) I: (pulseaudio) source.c:     alsa.card_name = "HDA Intel PCH"
(   0.256|   0.000) I: (pulseaudio) source.c:     alsa.long_card_name = "HDA Intel PCH at 0xefd30000 irq 29"
(   0.256|   0.000) I: (pulseaudio) source.c:     alsa.driver_name = "snd_hda_intel"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.bus_path = "pci-0000:00:1b.0"
(   0.256|   0.000) I: (pulseaudio) source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.bus = "pci"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.vendor.id = "8086"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.vendor.name = "Intel Corporation"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.product.id = "8ca0"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.product.name = "9 Series Chipset Family HD Audio Controller"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.form_factor = "internal"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.string = "1"
(   0.256|   0.000) I: (pulseaudio) source.c:     module-udev-detect.discovered = "1"
(   0.256|   0.000) I: (pulseaudio) source.c:     device.icon_name = "audio-card-pci"
(   0.256|   0.000) I: (pulseaudio) alsa-sink.c: Using 10,0 fragments of size 16932 bytes (32,00ms), buffer size is 169344 bytes (320,00ms)
(   0.256|   0.000) I: (pulseaudio) alsa-sink.c: Disabling rewind for device a52:1
(   0.256|   0.000) D: (pulseaudio) alsa-sink.c: hwbuf_unused=0
(   0.256|   0.000) D: (pulseaudio) alsa-sink.c: setting avail_min=1
(   0.256|   0.000) I: (pulseaudio) alsa-sink.c: Disabling rewind_within_thread for device a52:1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_dump():
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: Rate conversion PCM (48000)
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: Converter: libspeex (builtin)
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: Protocol version: 10002
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: Its setup is:
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   stream       : PLAYBACK
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   format       : S16_LE
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   subformat    : STD
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   channels     : 6
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   rate         : 44100
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   msbits       : 16
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   buffer_size  : 14112
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_size  : 1411
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_time  : 32000
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_mode  : ENABLE
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_type  : GETTIMEOFDAY
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_step  : 1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   avail_min    : 1411
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_event : 1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   start_threshold  : -1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   stop_threshold   : 7944349742681554944
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   silence_threshold: 0
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   silence_size : 0
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   boundary     : 7944349742681554944
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: Slave: A52 Output Plugin
(   0.256|   0.000) D: (pulseaudio) alsa-util.c: Its setup is:
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   stream       : PLAYBACK
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   access       : MMAP_NONINTERLEAVED
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   format       : S16_LE
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   subformat    : STD
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   channels     : 6
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   rate         : 48000
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   exact rate   : 48000 (48000/1)
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   msbits       : 16
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   buffer_size  : 15360
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_size  : 1536
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_time  : 32000
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_mode  : ENABLE
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_type  : GETTIMEOFDAY
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_step  : 1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   avail_min    : 1536
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   period_event : 1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   start_threshold  : -1
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   stop_threshold   : 8646911284551352320
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   silence_threshold: 0
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   silence_size : 0
(   0.256|   0.000) D: (pulseaudio) alsa-util.c:   boundary     : 8646911284551352320
(   0.256|   0.000) D: (alsa-sink-) alsa-sink.c: Thread starting up
(   0.258|   0.002) D: (alsa-sink-) core-util.c: RealtimeKit worked.
(   0.258|   0.000) I: (alsa-sink-) core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.265|   0.006) I: (alsa-sink-) alsa-sink.c: Starting playback.
(   0.265|   0.000) I: (alsa-sink-) (alsa-lib)pcm_hw.c: SNDRV_PCM_IOCTL_START failed (-77)
(   0.265|   0.000) D: (pulseaudio) module-device-restore.c: Could not set format on sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51
(   0.265|   0.000) D: (pulseaudio) alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
(   0.266|   0.000) D: (pulseaudio) alsa-util.c: Managed to open front:1
(   0.266|   0.000) I: (pulseaudio) alsa-util.c: Trying to disable ALSA period wakeups, using timers only
(   0.266|   0.000) D: (pulseaudio) alsa-util.c: Maximum hw buffer size is 371 ms
(   0.266|   0.000) D: (pulseaudio) alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
(   0.266|   0.000) I: (pulseaudio) alsa-util.c: ALSA period wakeups disabled
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Successfully opened device front:1.
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Successfully enabled mmap() mode.
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Successfully enabled timer-based scheduling mode.
(   0.266|   0.000) I: (pulseaudio) (alsa-lib)control.c: Invalid CTL front:1
(   0.266|   0.000) I: (pulseaudio) alsa-util.c: Unable to attach to mixer front:1: No such file or directory
(   0.266|   0.000) I: (pulseaudio) alsa-util.c: Successfully attached to mixer 'hw:1'
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Added 3 ports
(   0.266|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.266|   0.000) D: (pulseaudio) module-switch-on-port-available.c: Switching initial port for source 'alsa_input.pci-0000_00_1b.0.analog-stereo' to 'analog-input-front-mic'
(   0.266|   0.000) I: (pulseaudio) source.c: Created source 2 "alsa_input.pci-0000_00_1b.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.resolution_bits = "16"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.api = "alsa"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.class = "sound"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.class = "generic"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.subclass = "generic-mix"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.name = "ALC892 Analog"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.id = "ALC892 Analog"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.subdevice = "0"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.subdevice_name = "subdevice #0"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.device = "0"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.card = "1"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.card_name = "HDA Intel PCH"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.long_card_name = "HDA Intel PCH at 0xefd30000 irq 29"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.driver_name = "snd_hda_intel"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.bus_path = "pci-0000:00:1b.0"
(   0.266|   0.000) I: (pulseaudio) source.c:     sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card1"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.bus = "pci"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.vendor.id = "8086"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.vendor.name = "Intel Corporation"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.product.id = "8ca0"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.product.name = "9 Series Chipset Family HD Audio Controller"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.form_factor = "internal"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.string = "front:1"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.buffering.buffer_size = "65536"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.buffering.fragment_size = "32768"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.access_mode = "mmap+timer"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.profile.name = "analog-stereo"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.profile.description = "Analog Stereo"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.description = "Built-in Audio Analog Stereo"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.mixer_name = "Realtek ALC892"
(   0.266|   0.000) I: (pulseaudio) source.c:     alsa.components = "HDA:10ec0892,1849c892,00100302"
(   0.266|   0.000) I: (pulseaudio) source.c:     module-udev-detect.discovered = "1"
(   0.266|   0.000) I: (pulseaudio) source.c:     device.icon_name = "audio-card-pci"
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Using 2,0 fragments of size 32768 bytes (185,76ms), buffer size is 65536 bytes (371,52ms)
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Time scheduling watermark is 20,00ms
(   0.266|   0.000) D: (pulseaudio) alsa-source.c: hwbuf_unused=0
(   0.266|   0.000) D: (pulseaudio) alsa-source.c: setting avail_min=15502
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Activating path analog-input-front-mic
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Path analog-input-front-mic (Front Microphone), direction=2, priority=85, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=46, min_dB=-16, max_dB=60
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Element Front Mic Boost, direction=2, switch=0, volume=1, volume_limit=-1, enumeration=0, required=0, required_any=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Element Input Source, direction=2, switch=0, volume=0, volume_limit=-1, enumeration=1, required=0, required_any=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Option Front Mic (analog-input-microphone-front/analog-input-microphone-front) index=0, priority=0
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Element Rear Mic Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Element Line Boost, direction=2, switch=0, volume=2, volume_limit=-1, enumeration=0, required=0, required_any=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Front Mic, alsa_name='Front Mic Jack', detection possible
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Jack Front Mic Phantom, alsa_name='Front Mic Phantom Jack', detection unavailable
(   0.266|   0.000) D: (pulseaudio) alsa-mixer.c: Setting analog-input-microphone-front (analog-input-microphone-front) priority=0
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Successfully enabled deferred volume.
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Hardware volume ranges from -16,00 dB to 60,00 dB.
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Fixing base volume to -60,00 dB
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Using hardware volume control. Hardware dB scale supported.
(   0.266|   0.000) I: (pulseaudio) alsa-source.c: Using hardware mute control.
(   0.266|   0.000) D: (pulseaudio) alsa-util.c: snd_pcm_dump():
(   0.266|   0.000) D: (pulseaudio) alsa-util.c: Hardware PCM card 1 'HDA Intel PCH' device 0 subdevice 0
(   0.266|   0.000) D: (pulseaudio) alsa-util.c: Its setup is:
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   stream       : CAPTURE
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   access       : MMAP_INTERLEAVED
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   format       : S16_LE
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   subformat    : STD
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   channels     : 2
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   rate         : 44100
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   exact rate   : 44100 (44100/1)
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   msbits       : 16
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   buffer_size  : 16384
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   period_size  : 8192
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   period_time  : 185759
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_mode  : ENABLE
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   tstamp_type  : MONOTONIC
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   period_step  : 1
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   avail_min    : 15502
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   period_event : 0
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   start_threshold  : -1
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   stop_threshold   : 4611686018427387904
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   silence_threshold: 0
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   silence_size : 0
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   boundary     : 4611686018427387904
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   appl_ptr     : 0
(   0.266|   0.000) D: (pulseaudio) alsa-util.c:   hw_ptr       : 0
(   0.266|   0.000) D: (pulseaudio) alsa-source.c: Read hardware volume: front-left: 44652 /  68% / -10,00 dB,   front-right: 44652 /  68% / -10,00 dB
(   0.266|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: Thread starting up
(   0.268|   0.001) D: (alsa-source-ALC892 Analog) core-util.c: RealtimeKit worked.
(   0.268|   0.000) I: (alsa-source-ALC892 Analog) core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
(   0.268|   0.000) I: (alsa-source-ALC892 Analog) alsa-source.c: Starting capture.
(   0.268|   0.000) I: (pulseaudio) module.c: Loaded "module-alsa-card" (index: #7; argument: "device_id="1" name="pci-0000_00_1b.0" card_name="alsa_card.pci-0000_00_1b.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
(   0.268|   0.000) I: (pulseaudio) module-udev-detect.c: Card /devices/pci0000:00/0000:00:1b.0/sound/card1 (alsa_card.pci-0000_00_1b.0) module loaded.
(   0.268|   0.000) I: (pulseaudio) module-udev-detect.c: Found 2 cards.
(   0.268|   0.000) I: (pulseaudio) module.c: Loaded "module-udev-detect" (index: #5; argument: "").
(   0.268|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-jackdbus-detect.so': failure
(   0.268|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-bluetooth-policy.so': success
(   0.268|   0.000) I: (pulseaudio) module.c: Loaded "module-bluetooth-policy" (index: #8; argument: "").
(   0.268|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-bluetooth-discover.so': success
(   0.269|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-bluez5-discover.so': success
(   0.269|   0.000) D: (pulseaudio) dbus-util.c: Successfully connected to D-Bus system bus 4a0caeaf69095a57dfbe8cfe56baf7de as :1.152
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-bluez5-discover" (index: #10; argument: "").
(   0.270|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-bluez4-discover.so': failure
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-bluetooth-discover" (index: #9; argument: "").
(   0.270|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-esound-protocol-unix.so': failure
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-native-protocol-unix" (index: #11; argument: "").
(   0.270|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-gconf.so': failure
(   0.270|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.270|   0.000) I: (pulseaudio) module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51'.
(   0.270|   0.000) D: (pulseaudio) core-subscribe.c: Dropped redundant event due to change event.
(   0.270|   0.000) I: (pulseaudio) module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_00_1b.0.analog-stereo'.
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-default-device-restore" (index: #12; argument: "").
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-rescue-streams" (index: #13; argument: "").
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-always-sink" (index: #14; argument: "").
(   0.270|   0.000) I: (pulseaudio) module.c: Loaded "module-intended-roles" (index: #15; argument: "").
(   0.271|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_03.0.hdmi-stereo becomes idle, timeout in 5 seconds.
(   0.271|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51 becomes idle, timeout in 5 seconds.
(   0.271|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
(   0.271|   0.000) I: (pulseaudio) module.c: Loaded "module-suspend-on-idle" (index: #16; argument: "").
(   0.271|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-console-kit.so': failure
(   0.271|   0.000) D: (pulseaudio) module.c: Checking for existence of '/usr/lib/pulse-6.0/modules/module-systemd-login.so': success
(   0.271|   0.000) I: (pulseaudio) client.c: Created 0 "Login Session c2"
(   0.271|   0.000) D: (pulseaudio) module-systemd-login.c: Added new session c2
(   0.271|   0.000) I: (pulseaudio) module.c: Loaded "module-systemd-login" (index: #17; argument: "").
(   0.271|   0.000) I: (pulseaudio) module.c: Loaded "module-position-event-sounds" (index: #18; argument: "").
(   0.271|   0.000) I: (pulseaudio) module.c: Loaded "module-filter-heuristics" (index: #19; argument: "").
(   0.271|   0.000) I: (pulseaudio) module.c: Loaded "module-filter-apply" (index: #20; argument: "").
(   0.271|   0.000) D: (pulseaudio) main.c: Got org.PulseAudio1!
(   0.272|   0.000) D: (pulseaudio) main.c: Got org.pulseaudio.Server!
(   0.272|   0.000) I: (pulseaudio) main.c: Daemon startup complete.
(   0.272|   0.000) D: (pulseaudio) module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.272|   0.000) D: (pulseaudio) module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_03.0.
(   0.272|   0.000) D: (pulseaudio) module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
(   0.272|   0.000) D: (pulseaudio) module-udev-detect.c: Resuming all sinks and sources of card alsa_card.pci-0000_00_1b.0.
(   0.291|   0.019) E: (alsa-sink-) alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
(   0.291|   0.019) E: (alsa-sink-) alsa-sink.c: Most likely this is a bug in the ALSA driver '(null)'. Please report this issue to the ALSA developers.
(   0.291|   0.019) E: (alsa-sink-) alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
(   0.787|   0.496) D: (pulseaudio) conf-parser.c: Parsing configuration file '/home/casa/.config/pulse/client.conf'
(   0.788|   0.000) I: (pulseaudio) client.c: Created 1 "Native client (UNIX socket client)"
(   0.788|   0.000) D: (pulseaudio) protocol-native.c: Protocol version: remote 30, local 30
(   0.788|   0.000) I: (pulseaudio) protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.788|   0.000) D: (pulseaudio) protocol-native.c: SHM possible: yes
(   0.788|   0.000) D: (pulseaudio) protocol-native.c: Negotiated SHM: yes
(   0.788|   0.000) D: (pulseaudio) protocol-native.c: Disabling srbchannel, reason: Must be enabled by module parameter
(   0.788|   0.000) D: (pulseaudio) module-augment-properties.c: Looking for .desktop file for indicator-sound-service
(   3.792|   3.004) I: (pulseaudio) client.c: Created 2 "Native client (UNIX socket client)"
(   3.792|   0.000) D: (pulseaudio) protocol-native.c: Protocol version: remote 30, local 30
(   3.792|   0.000) I: (pulseaudio) protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   3.792|   0.000) D: (pulseaudio) protocol-native.c: SHM possible: yes
(   3.792|   0.000) D: (pulseaudio) protocol-native.c: Negotiated SHM: yes
(   3.792|   0.000) D: (pulseaudio) protocol-native.c: Disabling srbchannel, reason: Must be enabled by module parameter
(   3.793|   0.000) D: (pulseaudio) module-augment-properties.c: Looking for .desktop file for pavucontrol
(   3.793|   0.000) D: (pulseaudio) module-augment-properties.c: Found /usr/share/applications/pavucontrol.desktop.
(   3.793|   0.000) D: (pulseaudio) conf-parser.c: Parsing configuration file '/usr/share/applications/pavucontrol.desktop'
(   3.839|   0.046) D: (pulseaudio) module-stream-restore.c: Not restoring device for stream source-output-by-application-id:org.PulseAudio.pavucontrol, because already set
(   3.839|   0.000) D: (pulseaudio) module-intended-roles.c: Not setting device for stream Rilevato picco, because already set.
(   3.839|   0.000) D: (pulseaudio) source-output.c: Negotiated format: pcm, format.sample_format = "\"float32le\""  format.rate = "25"  format.channels = "1"  format.channel_map = "\"mono\""
(   3.839|   0.000) I: (pulseaudio) source-output.c: Trying to change sample rate
(   3.839|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_03.0.hdmi-stereo becomes busy, resuming.
(   3.839|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_03.0.hdmi-stereo becomes idle, timeout in 5 seconds.
(   3.839|   0.000) D: (pulseaudio) resampler.c: Resampler:
(   3.839|   0.000) D: (pulseaudio) resampler.c:   rate 44100 -> 25 (method peaks)
(   3.839|   0.000) D: (pulseaudio) resampler.c:   format s16le -> float32le (intermediate s16le)
(   3.839|   0.000) D: (pulseaudio) resampler.c:   channels 2 -> 1 (resampling 1)
(   3.839|   0.000) D: (pulseaudio) resampler.c: Channel matrix:
(   3.839|   0.000) D: (pulseaudio) resampler.c:        I00   I01 
(   3.839|   0.000) D: (pulseaudio) resampler.c:     +------------
(   3.839|   0.000) D: (pulseaudio) resampler.c: O00 | 0,500 0,500
(   3.839|   0.000) I: (pulseaudio) remap.c: Using stereo to mono remapping
(   3.839|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(   3.839|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(   3.839|   0.000) I: (pulseaudio) source-output.c: Created output 0 "Rilevato picco" on alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor with sample spec float32le 1ch 25Hz and channel map mono
(   3.839|   0.000) I: (pulseaudio) source-output.c:     media.name = "Rilevato picco"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.name = "Regolazione del volume PulseAudio"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     native-protocol.peer = "UNIX socket client"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     native-protocol.version = "30"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.id = "org.PulseAudio.pavucontrol"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.icon_name = "audio-card"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.version = "3.0"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.process.id = "1850"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.process.user = "casa"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.process.host = "stufa"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.process.binary = "pavucontrol"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.language = "it_IT.UTF-8"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     window.x11.display = ":0.0"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.process.machine_id = "adbef842f549a8c77a0abd52563e6f2e"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     application.process.session_id = "c2"
(   3.839|   0.000) I: (pulseaudio) source-output.c:     module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"
(   3.839|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=4194304, tlength=0, base=4, prebuf=1, minreq=0 maxrewind=0
(   3.839|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=4194304, tlength=4194304, base=4, prebuf=4, minreq=4 maxrewind=0
(   3.839|   0.000) I: (pulseaudio) protocol-native.c: Final latency 60,00 ms = 40,00 ms + 20,00 ms
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Latency set to 20,00ms
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: hwbuf_unused=62008
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: setting avail_min=15944
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Requesting rewind due to latency change.
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Latency set to 20,00ms
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: hwbuf_unused=62008
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: setting avail_min=15944
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Requested to rewind 65536 bytes.
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Limited to 56768 bytes.
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: before: 14192
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: after: 14192
(   3.839|   0.000) D: (alsa-sink-HDMI 0) alsa-sink.c: Rewound 56768 bytes.
(   3.839|   0.000) D: (alsa-sink-HDMI 0) sink.c: Processing rewind...
(   3.839|   0.000) D: (alsa-sink-HDMI 0) source.c: Processing rewind...
(   3.839|   0.000) D: (pulseaudio) module-stream-restore.c: Not restoring device for stream source-output-by-application-id:org.PulseAudio.pavucontrol, because already set
(   3.839|   0.000) D: (pulseaudio) module-intended-roles.c: Not setting device for stream Rilevato picco, because already set.
(   3.839|   0.000) D: (pulseaudio) source-output.c: Negotiated format: pcm, format.sample_format = "\"float32le\""  format.rate = "25"  format.channels = "1"  format.channel_map = "\"mono\""
(   3.839|   0.000) I: (pulseaudio) source-output.c: Trying to change sample rate
(   3.839|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51 becomes busy, resuming.
(   3.839|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51 becomes idle, timeout in 5 seconds.
(   3.839|   0.000) D: (pulseaudio) resampler.c: Resampler:
(   3.839|   0.000) D: (pulseaudio) resampler.c:   rate 44100 -> 25 (method peaks)
(   3.839|   0.000) D: (pulseaudio) resampler.c:   format s16le -> float32le (intermediate s16le)
(   3.839|   0.000) D: (pulseaudio) resampler.c:   channels 6 -> 1 (resampling 1)
(   3.839|   0.000) D: (pulseaudio) resampler.c: Channel matrix:
(   3.839|   0.000) D: (pulseaudio) resampler.c:        I00   I01   I02   I03   I04   I05 
(   3.839|   0.000) D: (pulseaudio) resampler.c:     +------------------------------------
(   3.839|   0.000) D: (pulseaudio) resampler.c: O00 | 0,167 0,167 0,167 0,167 0,167 0,167
(   3.840|   0.000) I: (pulseaudio) remap.c: Using generic matrix remapping
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=12, prebuf=0, minreq=1 maxrewind=0
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=33554436, tlength=33554436, base=12, prebuf=0, minreq=12 maxrewind=0
(   3.840|   0.000) I: (pulseaudio) source-output.c: Created output 1 "Rilevato picco" on alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51.monitor with sample spec float32le 1ch 25Hz and channel map mono
(   3.840|   0.000) I: (pulseaudio) source-output.c:     media.name = "Rilevato picco"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.name = "Regolazione del volume PulseAudio"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     native-protocol.peer = "UNIX socket client"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     native-protocol.version = "30"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.id = "org.PulseAudio.pavucontrol"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.icon_name = "audio-card"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.version = "3.0"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.id = "1850"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.user = "casa"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.host = "stufa"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.binary = "pavucontrol"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.language = "it_IT.UTF-8"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     window.x11.display = ":0.0"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.machine_id = "adbef842f549a8c77a0abd52563e6f2e"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.session_id = "c2"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=4194304, tlength=0, base=4, prebuf=1, minreq=0 maxrewind=0
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=4194304, tlength=4194304, base=4, prebuf=4, minreq=4 maxrewind=0
(   3.840|   0.000) I: (pulseaudio) protocol-native.c: Final latency 640,00 ms = 320,00 ms + 320,00 ms
(   3.840|   0.000) D: (pulseaudio) module-stream-restore.c: Not restoring device for stream source-output-by-application-id:org.PulseAudio.pavucontrol, because already set
(   3.840|   0.000) D: (pulseaudio) module-intended-roles.c: Not setting device for stream Rilevato picco, because already set.
(   3.840|   0.000) D: (pulseaudio) source-output.c: Negotiated format: pcm, format.sample_format = "\"float32le\""  format.rate = "25"  format.channels = "1"  format.channel_map = "\"mono\""
(   3.840|   0.000) I: (pulseaudio) source-output.c: Trying to change sample rate
(   3.840|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo becomes busy, resuming.
(   3.840|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Source alsa_input.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
(   3.840|   0.000) D: (pulseaudio) resampler.c: Resampler:
(   3.840|   0.000) D: (pulseaudio) resampler.c:   rate 44100 -> 25 (method peaks)
(   3.840|   0.000) D: (pulseaudio) resampler.c:   format s16le -> float32le (intermediate s16le)
(   3.840|   0.000) D: (pulseaudio) resampler.c:   channels 2 -> 1 (resampling 1)
(   3.840|   0.000) D: (pulseaudio) resampler.c: Channel matrix:
(   3.840|   0.000) D: (pulseaudio) resampler.c:        I00   I01 
(   3.840|   0.000) D: (pulseaudio) resampler.c:     +------------
(   3.840|   0.000) D: (pulseaudio) resampler.c: O00 | 0,500 0,500
(   3.840|   0.000) I: (pulseaudio) remap.c: Using stereo to mono remapping
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
(   3.840|   0.000) I: (pulseaudio) source-output.c: Created output 2 "Rilevato picco" on alsa_input.pci-0000_00_1b.0.analog-stereo with sample spec float32le 1ch 25Hz and channel map mono
(   3.840|   0.000) I: (pulseaudio) source-output.c:     media.name = "Rilevato picco"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.name = "Regolazione del volume PulseAudio"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     native-protocol.peer = "UNIX socket client"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     native-protocol.version = "30"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.id = "org.PulseAudio.pavucontrol"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.icon_name = "audio-card"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.version = "3.0"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.id = "1850"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.user = "casa"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.host = "stufa"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.binary = "pavucontrol"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.language = "it_IT.UTF-8"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     window.x11.display = ":0.0"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.machine_id = "adbef842f549a8c77a0abd52563e6f2e"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     application.process.session_id = "c2"
(   3.840|   0.000) I: (pulseaudio) source-output.c:     module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=4194304, tlength=0, base=4, prebuf=1, minreq=0 maxrewind=0
(   3.840|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=4194304, tlength=4194304, base=4, prebuf=4, minreq=4 maxrewind=0
(   3.840|   0.000) I: (pulseaudio) protocol-native.c: Final latency 60,00 ms = 40,00 ms + 20,00 ms
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: latency set to 20,00ms
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: hwbuf_unused=62008
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: setting avail_min=442
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: latency set to 20,00ms
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: hwbuf_unused=62008
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: setting avail_min=442
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: Requested volume: front-left: 44652 /  68% / -10,00 dB,   front-right: 44652 /  68% / -10,00 dB
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: Got hardware volume: front-left: 44652 /  68% / -10,00 dB,   front-right: 44652 /  68% / -10,00 dB
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: Calculated software volume: front-left: 65536 / 100% / 0,00 dB,   front-right: 65536 / 100% / 0,00 dB (accurate-enough=yes)
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) source.c: Volume not changing
(   3.840|   0.000) I: (alsa-source-ALC892 Analog) alsa-source.c: Increasing minimal latency to 1,00 ms
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: latency set to 20,00ms
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: hwbuf_unused=62008
(   3.840|   0.000) D: (alsa-source-ALC892 Analog) alsa-source.c: setting avail_min=442
(  19.186|  15.345) I: (pulseaudio) client.c: Created 3 "Native client (UNIX socket client)"
(  19.186|   0.000) D: (pulseaudio) protocol-native.c: Protocol version: remote 30, local 30
(  19.186|   0.000) I: (pulseaudio) protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  19.186|   0.000) D: (pulseaudio) protocol-native.c: SHM possible: yes
(  19.186|   0.000) D: (pulseaudio) protocol-native.c: Negotiated SHM: yes
(  19.186|   0.000) D: (pulseaudio) protocol-native.c: Disabling srbchannel, reason: Must be enabled by module parameter
(  19.186|   0.000) D: (pulseaudio) module-augment-properties.c: Looking for .desktop file for mplayer
(  19.186|   0.000) D: (pulseaudio) module-intended-roles.c: Not setting device for stream audio stream, because it lacks role.
(  19.186|   0.000) D: (pulseaudio) sink-input.c: Negotiated format: pcm, format.sample_format = "\"s16le\""  format.rate = "48000"  format.channels = "2"  format.channel_map = "\"front-left,front-right\""
(  19.186|   0.000) I: (pulseaudio) sink-input.c: Trying to change sample rate
(  19.186|   0.000) I: (pulseaudio) sink.c: Cannot update rate, monitor source is RUNNING
(  19.186|   0.000) I: (pulseaudio) module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:mplayer2.
(  19.186|   0.000) I: (pulseaudio) module-stream-restore.c: Restoring mute state for sink input sink-input-by-application-name:mplayer2.
(  19.186|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51 becomes busy, resuming.
(  19.186|   0.000) D: (pulseaudio) resampler.c: Resampler:
(  19.186|   0.000) D: (pulseaudio) resampler.c:   rate 48000 -> 44100 (method speex-float-1)
(  19.186|   0.000) D: (pulseaudio) resampler.c:   format s16le -> s16le (intermediate float32le)
(  19.186|   0.000) D: (pulseaudio) resampler.c:   channels 2 -> 6 (resampling 2)
(  19.186|   0.000) D: (pulseaudio) resampler.c: Channel matrix:
(  19.186|   0.000) D: (pulseaudio) resampler.c:        I00   I01 
(  19.186|   0.000) D: (pulseaudio) resampler.c:     +------------
(  19.186|   0.000) D: (pulseaudio) resampler.c: O00 | 1,000 0,000
(  19.186|   0.000) D: (pulseaudio) resampler.c: O01 | 0,000 1,000
(  19.186|   0.000) D: (pulseaudio) resampler.c: O02 | 1,000 0,000
(  19.186|   0.000) D: (pulseaudio) resampler.c: O03 | 0,000 1,000
(  19.186|   0.000) D: (pulseaudio) resampler.c: O04 | 0,500 0,500
(  19.186|   0.000) D: (pulseaudio) resampler.c: O05 | 0,500 0,500
(  19.186|   0.000) I: (pulseaudio) remap.c: Using generic matrix remapping
(  19.186|   0.000) D: (pulseaudio) resampler.c:   lfe filter activated (LR4 type), the crossover_freq = 120Hz
(  19.186|   0.000) I: (pulseaudio) speex.c: Choosing speex quality setting 1.
(  19.186|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=12, prebuf=0, minreq=1 maxrewind=0
(  19.186|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=33554436, tlength=33554436, base=12, prebuf=0, minreq=12 maxrewind=0
(  19.186|   0.000) I: (pulseaudio) sink-input.c: Created input 0 "audio stream" on alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51 with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     media.name = "audio stream"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.name = "mplayer2"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     native-protocol.peer = "UNIX socket client"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     native-protocol.version = "30"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.process.id = "7415"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.process.user = "casa"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.process.host = "stufa"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.process.binary = "mplayer"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.language = "C"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     window.x11.display = ":0.0"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.process.machine_id = "adbef842f549a8c77a0abd52563e6f2e"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     application.process.session_id = "c2"
(  19.186|   0.000) I: (pulseaudio) sink-input.c:     module-stream-restore.id = "sink-input-by-application-name:mplayer2"
(  19.186|   0.000) I: (pulseaudio) protocol-native.c: Requested tlength=1000,00 ms, minreq=20,00 ms
(  19.186|   0.000) D: (pulseaudio) protocol-native.c: Traditional mode enabled, modifying sink usec only for compat with minreq.
(  19.186|   0.000) D: (pulseaudio) protocol-native.c: Requested latency=960,00 ms, Received latency=320,00 ms
(  19.186|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=4194304, tlength=192000, base=4, prebuf=188164, minreq=3840 maxrewind=0
(  19.186|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=4194304, tlength=192000, base=4, prebuf=188164, minreq=3840 maxrewind=0
(  19.186|   0.000) I: (pulseaudio) protocol-native.c: Final latency 1320,00 ms = 960,00 ms + 2*20,00 ms + 320,00 ms
(  19.193|   0.006) D: (pulseaudio) module-intended-roles.c: Not setting device for stream Rilevato picco, because already set.
(  19.193|   0.000) D: (pulseaudio) source-output.c: Negotiated format: pcm, format.sample_format = "\"float32le\""  format.rate = "25"  format.channels = "1"  format.channel_map = "\"mono\""
(  19.193|   0.000) I: (pulseaudio) source-output.c: Trying to change sample rate
(  19.193|   0.000) I: (pulseaudio) source.c: Cannot update rate, SOURCE_IS_RUNNING, will keep using 44100 Hz
(  19.193|   0.000) D: (pulseaudio) module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51 becomes busy, resuming.
(  19.193|   0.000) D: (pulseaudio) resampler.c: Resampler:
(  19.193|   0.000) D: (pulseaudio) resampler.c:   rate 44100 -> 25 (method peaks)
(  19.193|   0.000) D: (pulseaudio) resampler.c:   format s16le -> float32le (intermediate s16le)
(  19.193|   0.000) D: (pulseaudio) resampler.c:   channels 6 -> 1 (resampling 1)
(  19.193|   0.000) D: (pulseaudio) resampler.c: Channel matrix:
(  19.193|   0.000) D: (pulseaudio) resampler.c:        I00   I01   I02   I03   I04   I05 
(  19.193|   0.000) D: (pulseaudio) resampler.c:     +------------------------------------
(  19.193|   0.000) D: (pulseaudio) resampler.c: O00 | 0,167 0,167 0,167 0,167 0,167 0,167
(  19.193|   0.000) I: (pulseaudio) remap.c: Using generic matrix remapping
(  19.193|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=12, prebuf=0, minreq=1 maxrewind=0
(  19.193|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=33554436, tlength=33554436, base=12, prebuf=0, minreq=12 maxrewind=0
(  19.193|   0.000) I: (pulseaudio) source-output.c: Created output 3 "Rilevato picco" on alsa_output.pci-0000_00_1b.0.iec958-ac3-surround-51.monitor with sample spec float32le 1ch 25Hz and channel map mono
(  19.193|   0.000) I: (pulseaudio) source-output.c:     media.name = "Rilevato picco"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.name = "Regolazione del volume PulseAudio"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     native-protocol.peer = "UNIX socket client"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     native-protocol.version = "30"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.id = "org.PulseAudio.pavucontrol"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.icon_name = "audio-card"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.version = "3.0"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.process.id = "1850"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.process.user = "casa"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.process.host = "stufa"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.process.binary = "pavucontrol"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.language = "it_IT.UTF-8"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     window.x11.display = ":0.0"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.process.machine_id = "adbef842f549a8c77a0abd52563e6f2e"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     application.process.session_id = "c2"
(  19.193|   0.000) I: (pulseaudio) source-output.c:     module-stream-restore.id = "source-output-by-application-id:org.PulseAudio.pavucontrol"
(  19.193|   0.000) D: (pulseaudio) memblockq.c: memblockq requested: maxlength=4194304, tlength=0, base=4, prebuf=1, minreq=0 maxrewind=0
(  19.194|   0.000) D: (pulseaudio) memblockq.c: memblockq sanitized: maxlength=4194304, tlength=4194304, base=4, prebuf=4, minreq=4 maxrewind=0
(  19.194|   0.000) I: (pulseaudio) protocol-native.c: Final latency 640,00 ms = 320,00 ms + 320,00 ms
(  19.197|   0.003) D: (alsa-sink-) protocol-native.c: Requesting rewind due to end of underrun.
(  19.197|   0.000) D: (alsa-sink-) alsa-sink.c: Requested to rewind 0 bytes.
(  19.197|   0.000) D: (alsa-sink-) alsa-sink.c: Mhmm, actually there is nothing to rewind.
(  25.270|   6.072) E: (pulseaudio) bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
(  25.439|   0.169) E: (alsa-sink-) xmalloc.c: Assertion 'size > 0' failed at pulse/xmalloc.c:60, function pa_xmalloc(). Aborting.


```

---

### Post by Yellow Pasque on 2016-02-10
This doesn't look right:
```
  19.193|   0.000) D: (pulseaudio) resampler.c: Resampler:
(  19.193|   0.000) D: (pulseaudio) resampler.c:   rate 44100 -> 25 (method peaks)
(  19.193|   0.000) D: (pulseaudio) resampler.c:   format s16le -> float32le (intermediate s16le)
(  19.193|   0.000) D: (pulseaudio) resampler.c:   channels 6 -> 1 (resampling 1)
```

I suggest deleting the asound.conf and finding this line in /etc/pulse/daemon.conf
```
;alternate-sample-rate = 48000
```
Uncomment it by removing the ';' and restart pulseaudio (or log out/in):
```
pulseaudio -k
```
This will allow pulseaudio to playback at 48 kHz without resampling (assuming no other streams are concurrently running at 44.1kHz).

---

### Post by leodp on 2016-02-10
Temüjin: 
it works, but by deleting /etc/asound.conf I loose 5.1 digital surround. 
Just uncommenting the line in daemon.conf is not enough if asound.conf is not removed.

Alternatively, I added the line in daemon.conf:
default-sample-rate = 48000
instead of the previously commented entry:
; default-sample-rate = 44100
and kept asound.conf as it is.

Now everything works fine.
I can also avoid keeping pavucontrol open.
I can play two streams at the same time, one with 48kHz and one with 44.1kHz, and they keep going, unless I change the volume on one. But the PC is a single user station and I rarely watch two movies at the same time.

Thanks for the input. I'll add a new reply if problems arise with other conditions, but for what concerns me I see the point as solved.

---

