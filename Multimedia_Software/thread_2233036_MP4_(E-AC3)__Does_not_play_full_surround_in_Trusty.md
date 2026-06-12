---
title: "MP4 (E-AC3)  Does not play full surround in Trusty 64Bit"
date: 2014-07-05
forum: Multimedia Software
---

### Post by geemac2 on 2014-07-05
Hello,

After I did a fresh install of Trusty 64bit from a 32bit version , I was finally at the point of testing my surround system and found that I do not have the 5.1 surround out of these two MP4 (E- AC3) videos.  The MP4 videos surround output were fine through both S/PDIF and HDMI on the old 32bit install.  This is not the case anymore with the 64bit install.  When things were working I must have played the BeardyMan video to death demonstrating the full surround sound to my friends.  It is a wild video... 

I have tried other surround sound files that produce AC3, DTS, DTS-Digital Dolby Digital, [COLOR=#333333][FONT=verdana]Dolby Digital Plus,[/FONT][/COLOR] [COLOR=#333333][FONT=verdana]Dolby TrueHD[/FONT][/COLOR] from a studio audio test dvd to my Onkyo [COLOR=#333333][FONT=verdana]TX-SR606 receiver [/FONT][/COLOR]and the surround sound is working as it should except the MP4 files.  Channelcheck-large.mp4 and beardyman-large.mp4 are in the same format as posted below in the mediainfo output and shows as a E-AC3 which my Onkyo [COLOR=#333333][FONT=verdana]TX-SR606[/FONT][/COLOR] is capable of playing.  Is it possible that something was re-coding the MP4 in the old install? 

Any hlep would be appreciated and thanks in advance.

 _***[Click Here]("http://www.dolby.com/in/en/consumer/technology/home-theater/dolby-digital-plus-download.html")***_ for a link to these videos. I am not promoting these videos, the link is for those that want to see if they can reproduce my issue.

 
```

mediainfo -l beardyman-large.mp4
General
Complete name                            : beardyman-large.mp4
Format                                   : dby1
Codec ID                                 : dby1
File size                                : 178 MiB
Duration                                 : 4mn 1s
Overall bit rate mode                    : Variable
Overall bit rate                         : 6 183 Kbps
Encoded date                             : UTC 2011-09-21 23:27:47
Tagged date                              : UTC 2011-09-21 23:27:47
Writing application                      : Audio: Dolby Digital Plus Encoder 2.2.2 Video: Dolby Impact H.264 Encoder 2.4.7.26 (win64)


Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Baseline@L3.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 1 frame
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 4mn 1s
Bit rate mode                            : Variable
Bit rate                                 : 6 001 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Standard                                 : Component
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.272
Stream size                              : 171 MiB (96%)
Encoded date                             : UTC 2011-09-21 23:27:47
Tagged date                              : UTC 2011-09-21 23:27:47


Audio
ID                                       : 2
Format                                   : E-AC-3
Format/Info                              : Audio Coding 3
Format settings, Endianness              : Big
Codec ID                                 : ec-3
Duration                                 : 4mn 1s
Bit rate mode                            : Constant
Bit rate                                 : 224 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 6.45 MiB (4%)
Encoded date                             : UTC 2011-09-21 23:27:47
Tagged date                              : UTC 2011-09-21 23:27:47

```

---

### Post by geemac2 on 2014-07-08
[SIZE=3][COLOR=#006400][I][B]Update...
[/B][/I][/COLOR][/SIZE]
I just did a check to see if the codecs were installed for MP4, both these tests showed that MP4 codec are installed.


HTPC:~$** ffmpeg -formats | grep mp4**
***results:***
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime / MOV
 E mp4             MP4 (MPEG-4 Part 14)[I]
_____________________________________________________________________________

[/I]HTPC:~$ avconv -codecs
[I][B]results:
[/B][/I]DEV.L. mpeg4                MPEG-4 part 2 (decoders: mpeg4 mpeg4_vdpau ) (encoders: mpeg4 libxvid )
DEVI.S rawvideo             raw video
D.V.L. msmpeg4v1            MPEG-4 part 2 Microsoft variant version 1
DEV.L. msmpeg4v2            MPEG-4 part 2 Microsoft variant version 2
DEV.L. msmpeg4v3            MPEG-4 part 2 Microsoft variant version 3 (decoders: msmpeg4 ) (encoders: msmpeg4 )
DEV.LS h264                 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (decoders: h264 h264_vdpau ) (encoders: libx264 )
D.A..S mp4als               MPEG-4 Audio Lossless Coding (ALS) (decoders: als )

[I]**Table for above:**
[/I]D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec
 ..S... = Subtitle codec
 ...I.. = Intra frame-only codec
 ....L. = Lossy compression
 .....S = Lossless compression


Now to figure why they are not working via VLC or any other media player including XBMC.
Anyone??

Thanks

[I][B][COLOR=#006400]Update2...

[/COLOR][/B][/I]In XBMC under Settings > System > Audio Output.  I had to turn Enable Passthrough on/off a few times and then Enable Dolby Digital Transcode appeared, once that became visible I switched it on and now the MP4 plays full surround sound 5.1.
As for any other regular media player; still no go, just stereo.

---

### Post by SeijiSensei on 2014-07-09
[SMPlayer]("http://smplayer.sourceforge.net/") is a front-end for mplayer (actually mplayer2 in Ubuntu) that allows you to choose the number of channels to use (Options > Preferences > General > Audio).  SMPlayer is in the repositories; you can install it with "sudo apt-get install smplayer".

---

### Post by geemac2 on 2014-07-09
Thanks SeijSensei,

I gave SMPlayer a try and it is the same issue as in VLC Media Player which I spent roughly an hour yesterday trying to get to play the 5.1 surround mp4 files as it did when I was running 32 bit Trusty.  All it did is keep switching to stereo.  There is apparently something missing in the 64 bit install that is not letting these players play a mp4 surround sound file except in stereo.  I can see my stereo switch from stereo to something then switch back again within a second of the MP4 file playing.
As I mentioned above I did get the MP4 files to play full surround in XBMC but apparently it is using transcoding to play these files.  Apparently there is something I am missing or something is different between 32 bit and 64 bit when it comes to the codecs and or setup.

Thanks again for your input.

---

### Post by SeijiSensei on 2014-07-09
Now that you have mplayer installed (as a dependency to smplayer), try playing one of the files from the command prompt with the -v (verbose) switch:
```
$ mplayer -v /path/to/the/axolotl.mp4
```
You'll get a whole lot of output.  What matters most is at the top concerning the structure of the file, the codecs used, etc.  Hit Ctrl-C to stop the player.

---

### Post by geemac2 on 2014-07-20
Thanks again for your reply and help SejiSensei,

Apparently my earlier reply did not save last week.  Below is the info from the mp4 video file.  Apparently none of the players will play the MP4 in surround , only stereo.
Below is the verbose of the video file from Mplayer.  It is showing what I expected as if the file is stereo / 2-Channels.  Very strange since XBMC is fine for surround.
___________________________________________________________
```


mplayer -v ~/Videos/Surround_Test/beardyman-large.mp4
Reading config file /etc/mplayer/mplayer.conf
: No such file or directory
get_path('') -> '/home/HTPC/.mplayer/'
get_path('config') -> '/home/HTPC/.mplayer/config'
Reading config file /home/HTPC/.mplayer/config
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ (Family: 15, Model: 107, Stepping: 1)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
Compiled against libavutil version 52.3.0
Compiled against libavcodec version 54.35.0
Compiled against libavformat version 54.20.3 (runtime 54.20.4)
Compiled against libswscale version 2.1.1
get_path('codecs.conf') -> '/home/HTPC/.mplayer/codecs.conf'
No optional codecs config file: /home/HTPC/.mplayer/codecs.conf
No optional codecs config file: /etc/mplayer/codecs.conf
163 audio & 363 video codecs
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --enable-translation --extra-cflags=-g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2 --extra-ldflags=-Wl,-Bsymbolic-functions -Wl,-z,relro --enable-debug=3 --enable-runtime-cpudetection
CommandLine: '-v' '/home/HTPC/Videos/Surround_Test/beardyman-large.mp4'
get_path('fonts') -> '/home/HTPC/.mplayer/fonts'
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/HTPC/.mplayer/fonts'
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE)
[ass] Initialized
get_path('fonts') -> '/home/HTPC/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/HTPC/.mplayer/subfont.ttf'
[ass] Updating font cache
Using nanosleep() timing
get_path('input.conf') -> '/home/HTPC/.mplayer/input.conf'
Cannot open file '/home/HTPC/.mplayer/input.conf': No such file or directory
Failed to open /home/HTPC/.mplayer/input.conf.
Can't open input config file /home/HTPC/.mplayer/input.conf.
Cannot open file '/etc/mplayer/input.conf': No such file or directory
Failed to open /etc/mplayer/input.conf.
Can't open input config file /etc/mplayer/input.conf.
Falling back on default (hardcoded) input config
Setting up LIRC support...
Failed to open LIRC support. You will not be able to use your remote control.
get_path('beardyman-large.mp4.conf') -> '/home/HTPC/.mplayer/beardyman-large.mp4.conf'


Playing /home/HTPC/Videos/Surround_Test/beardyman-large.mp4.
get_path('sub/') -> '/home/HTPC/.mplayer/sub/'
[file] File size is 186612607 bytes
STREAM: [file] /home/HTPC/Videos/Surround_Test/beardyman-large.mp4
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: QuickTime / MOV
Detected file format: QuickTime / MOV (libavformat)
==> Found video stream: 0
======= VIDEO Format ======
  biSize 100
  biWidth 1280
  biHeight 720
  biPlanes 0
  biBitCount 24
  biCompression 875967048='H264'
  biSizeImage 2764800
Unknown extra header dump: [1] [42] [c0] [1f] [ff] [e1] [0] [2d] [67] [42] [c0] [1f] [96] [74] [2] [80] [2d] [d8] [a] [4] [0] [0] [f] [a0] [0] [2] [ed] [43] [a3] [0] [5] [b9] [0] [1] [6e] [3a] [f7] [be] [34] [60] [0] [b7] [20] [0] [2d] [c7] [5e] [f7] [c1] [e1] [10] [8d] [40] [1] [0] [4] [68] [de] [3c] [80] 
===========================
[lavf] stream 0: video (h264), -vid 0
==> Found audio stream: 1
======= WAVE Format =======
Format Tag: 16709 (0x4145)
Channels: 6
Samplerate: 48000
avg byte/sec: 28000
Block align: 1
bits/sample: 16
cbSize: 0
==========================================================================
[lavf] stream 1: audio (eac3), -aid 0, -alang und
LAVF: 1 audio and 1 video streams found
[ass] Raster: FreeType 2.5.2
[ass] Shaper: FriBidi 0.19.6 (SIMPLE)
[ass] Initialized
get_path('fonts') -> '/home/HTPC/.mplayer/fonts'
get_path('subfont.ttf') -> '/home/HTPC/.mplayer/subfont.ttf'
[ass] Updating font cache
[V] filefmt:41  fourcc:0x34363248  size:1280x720  fps:23.976  ftime:=0.0417
Clip info:
 major_brand: dby1
 minor_version: 0
 compatible_brands: isommp42dby1
 creation_time: 2011-09-21 23:27:47
 encoder: Audio: Dolby Digital Plus Encoder 2.2.2 Video: Dolby Impact H.264 Encoder 2.4.7.26 (win64)
Load subtitles in /home/HTPC/Videos/Surround_Test/
get_path('sub/') -> '/home/HTPC/.mplayer/sub/'
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1920x1080 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[vdpau] Error when calling vdp_device_create_x11: 1
vo: uninit ...
X11 opening display: :0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1920x1080 with depth 24 and 32 bpp (":0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[VO_XV] Using Xv Adapter #0 (NV17 Video Texture)
[xv common] Drawing no colorkey.
[xv common] Maximum source image dimensions: 4096x4096
[vo] query(Planar YV12) -> 437
[ass] auto-open
Opening video decoder: [ffmpeg] libavcodec video codecs
Asking decoder to use 2 threads if supported.
Selected video codec: H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 [libavcodec]
Video codecs.conf entry: ffh264 (FFmpeg H.264)  vfm: ffmpeg
Opening audio decoder: [ffmpeg] libavcodec audio decoders
dec_audio: Allocating 8192 + 65536 = 73728 bytes for output buffer.
INFO: libavcodec "eac3" init OK!
(Re)initializing libavresample format conversion...
Selected audio codec: ATSC A/52B (AC-3, E-AC-3) [libavcodec]
Audio codecs.conf entry: ffeac3 (FFmpeg E-AC-3)  afm: ffmpeg
AUDIO: 48000 Hz, 2 ch, floatle, 224.0 kbit/7.29% (ratio: 28000->384000)
Building audio filter chain for 48000Hz/2ch/floatle -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 0Hz/0ch/??
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 0Hz/0ch/??
Trying every known audio driver...
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
AO: Description: PulseAudio audio output
AO: Author: Lennart Poettering
Building audio filter chain for 48000Hz/2ch/floatle -> 48000Hz/2ch/floatle...
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 48000Hz/2ch/floatle
[dummy] Was reinitialized: 48000Hz/2ch/floatle
Audio filter chain:
  [in] 48000Hz/2ch/floatle
  [dummy] 48000Hz/2ch/floatle
  [out] 48000Hz/2ch/floatle
Starting playback...
[ffmpeg] aspect_ratio: 1.777778
VIDEO:  1280x720  23.976 fps  5961.8 kbps (745.2 kB/s)
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
Trying filter chain: ass vo
VDec: using Planar YV12 as output csp (no 0)
VO Config (1280x720->1280x720,flags=0,0x32315659)
REQ: flags=0x437  req=0x0  
VO: [xv] 1280x720 => 1280x720 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x59565955 (UYVY) packed
Xvideo image format: 0x30323449 (I420) planar
using Xvideo port 505 for hw scaling
xv_set_eq called! (bt_709, 100)
xv_get_eq called! (bt_709, 100)
*** [ass] Exporting mp_image_t, 1280x720x12bpp YUV planar, 1382400 bytes
*** [vo] Allocating mp_image_t, 1280x720x12bpp YUV planar, 1382400 bytes
Increasing filtered audio buffer size from 0 to 4096
Increasing filtered audio buffer size from 4096 to 69632
Increasing filtered audio buffer size from 69632 to 135168
Increasing filtered audio buffer size from 135168 to 200704
Increasing filtered audio buffer size from 200704 to 266240
Increasing filtered audio buffer size from 266240 to 331776
Increasing filtered audio buffer size from 331776 to 388096
A:  47.5 V:  47.5 A-V: -0.000 ct:  0.001   0/  0  3%  5%  1.3% 0 0 
  =====  PAUSE  =====




```

---

### Post by geemac2 on 2014-07-20
VLC Verbos
This does the same with other 5.1 mp4 files.  I just use this file since it produces the best 5.1 surround in XBMC. 

```


vlc -v ~/Videos/Surround_Test/beardyman-large.mp4
VLC media player 2.1.5 Rincewind (revision 2.1.5+ppa1)
[0x2444118] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
"sni-qt/12460" WARN  13:11:24.648 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
[0x7f06f8c01628] mp4 stream warning: unknown box type dec3 (incompletely loaded)
[0x7f06f8c01628] mp4 stream warning: Unknown uuid type box
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f06e0001248] main vout display error: Failed to resize display
[0x7f06f8c5d488] avcodec decoder warning: disabling direct rendering
[0x7f06f0013c38] main video output warning: picture is too late to be displayed (missing 39 ms)
[0x7f06f8c01628] mp4 stream warning: cannot free box ec-3, type unknown




```

---

### Post by mc4man on 2014-07-21
Haven't had a ss setup for a couple of years so just a shot in the dark - maybe try installing libasound2-plugins-extra

---

### Post by geemac2 on 2014-07-24
Hello  Mc4man

Thanks for the suggestion.
I installed the extra libraries.  It gave me a few extra options for the audio out on VLC , but still only playing in stereo.
My main issue here was when I went from 12.04 LTS to 13.10 when it first was released and after that new install the HDMI stopped passing Dolby Surround 5.1. That has not been fixed.  I even filed a bug report.  The devs keep telling me that is due to my chipset.  Well they are quite wrong about that.  My HDMI and S/PDIF both pass 5.1 with the original HTPC software under Suse.  That company went out of business.  So I installed 12.04 LTS and all was fine with the audio.
At this time the S/PDIF Coaxial output is what is connected from the computer to my receiver and since the Onkyo receiver has a known issue with bad capacitors in the HDMI switching, I have the HDMI directly to the TV.  For now XBMC is fine with 5.1 via S/PDIF, all the other media players are not playing the 5.1 surround.
I am not throwing any blame on the Ubuntu 14.x for this specific issue, it is something I have done or not have done when I reinstalled 14.x 64bit after using the 32it version that was working.  Just can't figure what I am missing.

---

### Post by mc4man on 2014-07-24
As mentioned I no longer have a ss setup & when I did, (several yr.s ago) things may have been different
(- to use pulseaudio one needed to jump thru some hoops. Also I only used audacious for audio & mplayer for video surround files. The former was set up thru it's extensive audio output selections, the later thru a specific command.

Just to ck., (if you wish), does beardyman (small) work right when in a mkv?
[http://www.datafilehost.com/d/37333141](http://www.datafilehost.com/d/37333141)

---

### Post by geemac2 on 2014-07-24
[I]quick update

[/I]I just opened SMPlayer and went to Options > Audio > Output driver
I selected Alsa and when I played the video file I saw the Onkyo receiver switch Dolby D (Digital) as it should with this video, but I could not hear any audio.
If I switch to Pulse it switches to Dolby D for a second then back to stereo with audio 
Apparently something is up with Alsa or the way it pipes through Pulse.  I went into Alsamixer and Pulse Volume and everything is set properly.

---

### Post by geemac2 on 2014-07-25
Hi Mc4man

Good suggestion on the smaller file.  By the way,  odd thing, I did not see you suggestion of the smaller mkv file until today.  That may explain why the last post looked out of sync to your posts.  strange...

Lol...  I always looked at the video and audio files as the bigger they are the more information was packed in. Not always the case though.  I tried the file out and still the same issue, XBMC plays it fine in 5.1 and all the other players only play stereo.

I did find one thing during this issue, apparently Alsa does not have the a/52 plugin installed.  I tried the steps given to compile the code and install the plugin, they were quite simple.  The issue with the a/52 plugin is they did not update the package for Ubuntu 13.10 and up.  I found a couple of sites explaining how to compile the plugin but I get errors while compiling (make).  The errors are mostly compatibility issues and some missing directories that don't get made during the process.

I'm pretty sure now that a/52 is the issue since it is used for Alsa to stream Dolby Digital 5.1 through the 2 channels and then your receiver does the 5.1 decoding.  I just wish that the devs of both Alsa and Pulseaudio would put their heads together and come up with one audio package.
If they would just make one full package there would be no need for the hoops then, and not only just hoops, but flaming hoops.

Thanks again

---

### Post by geemac2 on 2014-08-13
*[COLOR=#b22222]**Closed...**[/COLOR]*

This is a Alsa issue not taking the a/52 plugin install in Ubuntu 13.10 and 14.04 that would  normally carry the Dolby 5.1 code in the Stereo Digital stream of the S/PDIF.
All is fine in XBMC, the other players I can just do without the 5.1 surround.

Thanks

---

### Post by ben2talk on 2015-02-21
> **mc4man said:**
> As mentioned I no longer have a ss setup & when I did, (several yr.s ago) things may have been different
(- to use pulseaudio one needed to jump thru some hoops. Also I only used audacious for audio & mplayer for video surround files. The former was set up thru it's extensive audio output selections, the later thru a specific command.

Just to ck., (if you wish), does beardyman (small) work right when in a mkv?
[http://www.datafilehost.com/d/37333141](http://www.datafilehost.com/d/37333141)

I use Plex Home Theatre and have Plex Server running. Under the server, my TV limits sound to Dolby Digital and so pressure was on to get it playing direct for DTS and others...

Beardyman should come up as Dolby Digital + on the receiver... after reading that Pulse messes it all up (Audacious handling my DTS music well - straight passthrough) and my audio set to Digital Stereo HDMI... 

Final solution for me was:
ben: [~] sudo dpkg-reconfigure linux-sound-base 

Select ALSA, use Plex Home Theatre for your vids... but VLC also passes through the DTS from a VOB file I just tested...

All in all it is a touch flaky. I find the simplest solution (rather than troubleshooting) when I lose it is simply to log out and in again. Problems like this are what prevent Linux competing with Mac OSX or Windows in the real desktop world... such a shame.

---

