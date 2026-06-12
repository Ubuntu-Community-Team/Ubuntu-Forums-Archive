---
title: "mplayer won't play ISOs"
date: 2015-02-15
forum: Multimedia Software
---

### Post by ray field on 2015-02-15
It used to work fine, but now when I try to play ISO files (through Universal Media Server onto my PS3, or in a terminal), mplayer comes up empty.

 ```
mplayer -v VIDEO_TS/
MPlayer SVN-r37356 (C) 2000-2012 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM) i3-4130 CPU @ 3.40GHz (Family: 6, Model: 60, Stepping: 3)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSE3: 1 SSSE3: 1 SSE4: 1 SSE4.2: 1 AVX: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/raphael/.mplayer/codecs.conf'
Reading optional codecs config file /home/raphael/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/raphael/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --enable-xmga --enable-mga --enable-joystick --enable-libopencore_amrnb --enable-libopencore_amrwb --disable-decoder=amrnb --language=all --disable-mencoder --enable-radio --enable-radio-capture --extra-libs=-ldl -lvorbisenc -lvorbis --enable-xvmc --with-xvmclib=XvMCW --disable-gui --enable-runtime-cpudetection
CommandLine: '-v' 'VIDEO_TS/'
Using nanosleep() timing
get_path('input.conf') -> '/home/raphael/.mplayer/input.conf'
Reading optional input config file /home/raphael/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
get_path('.conf') -> '/home/raphael/.mplayer/.conf'

Playing VIDEO_TS/.
get_path('sub/') -> '/home/raphael/.mplayer/sub/'
[file] File size is 0 bytes
STREAM: [file] VIDEO_TS/
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavformat version 56.18.101 (internal)
Configuration: --enable-gpl --enable-postproc
LAVF_check: no clue about this gibberish!
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename VIDEO_TS/ ext: (null)
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
stream_seek: WARNING! Can't seek to 0x4 !
AVS: avs_check_file - attempting to open file VIDEO_TS/
AVS: failed to load avisynth.dll
AVS: Init failed
Checking for PVA
Checking for MPEG-TS...
THIS DOESN'T LOOK LIKE AN MPEG-TS FILE!
TRIED UP TO POSITION 0, FOUND ffffff00, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
LMLM4 Stream Format not found
MPEG Stream reached EOF
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
MPEG Stream reached EOF
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 3
Not MPEG System Stream format... (maybe Transport Stream?)
ds_fill_buffer: EOF reached (stream: video)  
LAVF_check: no clue about this gibberish!
Checking for DV
demux_aac_probe, failed to detect an AAC stream

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
```

Somewhat more disturbing, UMS reports "mplayer was not compiled with DVD support," which doesn't make sense to me since it was working a few months ago.

I have also tried running

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

to no effect.

---

### Post by ray field on 2015-02-17
any ideas where to begin troubleshooting?

---

### Post by mc4man on 2015-02-17
Well it appears mplayer no longer uses internal dvdnav (I saw it dropped internel libdvdcss, missed that..
So maybe that's the issue. 
Wait a couple of hr's & there should be a new package available (svn37373
(which ppa, it's in 2, one would use dvdnav4 (5.0), the other either 4 or 5 though built off of 4.0

---

### Post by ray field on 2015-02-17
> **mc4man said:**
> Well it appears mplayer no longer uses internal dvdnav (I saw it dropped internel libdvdcss, missed that..
So maybe that's the issue. 
Wait a couple of hr's & there should be a new package available (svn37373
(which ppa, it's in 2, one would use dvdnav4 (5.0), the other either 4 or 5 though built off of 4.0

kind thanks for the prompt attention, Mr. McMahon, but it hurts me to have to report it still doesn't seem to work --
```

mplayer -v VIDEO_TS
MPlayer SVN-r37373 (C) 2000-2012 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM) i3-4130 CPU @ 3.40GHz (Family: 6, Model: 60, Stepping: 3)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSE3: 1 SSSE3: 1 SSE4: 1 SSE4.2: 1 AVX: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/raphael/.mplayer/codecs.conf'
Reading optional codecs config file /home/raphael/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/raphael/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --enable-xmga --enable-mga --enable-joystick --enable-libopencore_amrnb --enable-libopencore_amrwb --disable-decoder=amrnb --language=all --disable-mencoder --enable-radio --enable-radio-capture --extra-libs=-ldl -lvorbisenc -lvorbis --enable-xvmc --with-xvmclib=XvMCW --disable-gui --enable-runtime-cpudetection
CommandLine: '-v' 'VIDEO_TS'
Using nanosleep() timing
get_path('input.conf') -> '/home/raphael/.mplayer/input.conf'
Reading optional input config file /home/raphael/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
get_path('VIDEO_TS.conf') -> '/home/raphael/.mplayer/VIDEO_TS.conf'

Playing VIDEO_TS.
get_path('sub/') -> '/home/raphael/.mplayer/sub/'
[file] File size is 0 bytes
STREAM: [file] VIDEO_TS
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
libavformat version 56.22.100 (internal)
Configuration: --enable-gpl --enable-postproc
LAVF_check: no clue about this gibberish!
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename VIDEO_TS ext: (null)
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
stream_seek: WARNING! Can't seek to 0x4 !
AVS: avs_check_file - attempting to open file VIDEO_TS
AVS: failed to load avisynth.dll
AVS: Init failed
Checking for PVA
Checking for MPEG-TS...
THIS DOESN'T LOOK LIKE AN MPEG-TS FILE!
TRIED UP TO POSITION 0, FOUND ffffff00, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
LMLM4 Stream Format not found
MPEG Stream reached EOF
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
MPEG Stream reached EOF
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 3
Not MPEG System Stream format... (maybe Transport Stream?)
ds_fill_buffer: EOF reached (stream: video)  
LAVF_check: no clue about this gibberish!
Checking for DV
demux_aac_probe, failed to detect an AAC stream

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)

```

happy to test builds if you want me to install a PPA...

-r

---

### Post by mc4man on 2015-02-17
That's unfortunate. ppa's usually don't hold more than 1 build back or so, so no help there.
I do have 1 older source here,  svn 37242. This has the internal dvdnav & read. The big issue with svn mplayer is you have to match up the internal ffmpeg source to the svn mplayer source so it's not easy to go back if you don't have both from same time period.

In other words, -  this one will be all I've got..
Don't bother adding ppa. (the build isn't an upgrade & no telling what I may place there in the future
Just expand the dropdown on this page > Source , download the mplayer package for your arch.
[https://launchpad.net/~mc3man/+archive/ubuntu/get-diff1/+packages](https://launchpad.net/~mc3man/+archive/ubuntu/get-diff1/+packages)

Then either remove current & install the dl'ed .deb with gdebi or maybe even software-center or better yet just use dpkg to install
sudo dpkg -i /path/to/nameofthe.deb

(easiest is to open dl folder, not maxed. Then open terminal type in - 
sudo dpkg -i 
hit the space bar, then DnD the dl'ed .deb on to terminal. click on terminal to return focus, press enter to install

[]()

If that doesn't work maybe try mplayer2 from repo or a local build

---

### Post by ray field on 2015-02-17
Boy, that was quick. Many thanks for trying!

I used Synaptic to uninstall mplayer, then removed mplayer2 (this time with apt-get remove) because dpkg complained about conflicts when I tried to install the mplayer .deb file. Finally installed from the .deb file, but still aborts, though it seems to get a little farther

```

mplayer -v VIDEO_TS/
MPlayer SVN-r37242 (C) 2000-2012 MPlayer Team
CPU vendor name: GenuineIntel  max cpuid level: 13
CPU: Intel(R) Core(TM) i3-4130 CPU @ 3.40GHz (Family: 6, Model: 60, Stepping: 3)
extended cpuid-level: 8
extended cache-info: 16801856
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNowExt: 0 SSE: 1 SSE2: 1 SSE3: 1 SSSE3: 1 SSE4: 1 SSE4.2: 1 AVX: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/raphael/.mplayer/codecs.conf'
Reading optional codecs config file /home/raphael/.mplayer/codecs.conf: No such file or directory
Reading optional codecs config file /etc/mplayer/codecs.conf: No such file or directory
Using built-in default codecs.conf.
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/raphael/.mplayer/fonts'
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --enable-xmga --enable-mga --enable-joystick --enable-libopencore_amrnb --enable-libopencore_amrwb --disable-decoder=amrnb --language=all --disable-libdvdcss-internal --disable-mencoder --enable-radio --enable-radio-capture --extra-libs=-ldl -lvorbisenc -lvorbis --enable-xvmc --with-xvmclib=XvMCW --disable-gui --enable-runtime-cpudetection
CommandLine: '-v' 'VIDEO_TS/'
Using nanosleep() timing
get_path('input.conf') -> '/home/raphael/.mplayer/input.conf'
Reading optional input config file /home/raphael/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 92 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
get_path('.conf') -> '/home/raphael/.mplayer/.conf'

Playing VIDEO_TS/.
get_path('sub/') -> '/home/raphael/.mplayer/sub/'
[file] File size is 0 bytes
STREAM: [file] VIDEO_TS/
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
stream_seek: WARNING! Can't seek to 0x0 !
libavformat version 55.49.100 (internal)
Configuration: --enable-gpl --enable-postproc
LAVF_check: no clue about this gibberish!
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
Checking for YUV4MPEG2
stream_seek: WARNING! Can't seek to 0x0 !
ASF_check: not ASF guid!
stream_seek: WARNING! Can't seek to 0x0 !
Checking for REAL
stream_seek: WARNING! Can't seek to 0x0 !
Checking for SMJPEG
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
Searching demuxer type for filename VIDEO_TS/ ext: (null)
stream_seek: WARNING! Can't seek to 0x0 !
Checking for Nullsoft Streaming Video
stream_seek: WARNING! Can't seek to 0x0 !
Checking for MOV
stream_seek: WARNING! Can't seek to 0x0 !
Checking for VIVO
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x4 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
AVS: avs_check_file - attempting to open file VIDEO_TS/
AVS: failed to load avisynth.dll
AVS: Init failed
stream_seek: WARNING! Can't seek to 0x0 !
Checking for PVA
stream_seek: WARNING! Can't seek to 0x0 !
Checking for MPEG-TS...
THIS DOESN'T LOOK LIKE AN MPEG-TS FILE!
TRIED UP TO POSITION 0, FOUND ffffff00, packet_size= 0, SEEMS A TS? 0
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
Checking for LMLM4 Stream Format
LMLM4 Stream Format not found
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
MPEG Stream reached EOF
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 0
Not MPEG System Stream format... (maybe Transport Stream?)
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
MPEG Stream reached EOF
MPEG packet stats: p100: 0  p101: 0 p1B6: 0 p12x: 0 sli: 0 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 0, synced: 3
Not MPEG System Stream format... (maybe Transport Stream?)
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
stream_seek: WARNING! Can't seek to 0x0 !
ds_fill_buffer: EOF reached (stream: video)  
stream_seek: WARNING! Can't seek to 0x0 !
LAVF_check: no clue about this gibberish!
stream_seek: WARNING! Can't seek to 0x0 !
Checking for DV
stream_seek: WARNING! Can't seek to 0x0 !
demux_aac_probe, failed to detect an AAC stream

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)
```


is this indeed a symptom of a bad ffmpeg match? Unfortunately after I went from Quantal to Trusty I spent months in the desert dealing with multiple ffmpeg versions and builds which didn't work, so since I finally have one which allows me to stream to my tv set, I'm loath to swap it out.

---

### Post by mc4man on 2015-02-18
Not sure what you're up to - you mentioned iso files & dvdnav
So a quick check here shows mplayer (now) is just fine playing a dvd_video iso file, ex.
```
$ mplayer -vo xv dvdnav:// -dvd-device  /home/doug/medium.iso 
MPlayer SVN-r37373 (C) 2000-2012 MPlayer Team
Loading protocol-related profile 'protocol.dvdnav'

Playing dvdnav://.
libdvdnav: Using dvdnav version 5.0.0
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6
Remember to disable MPlayer's cache when playing dvdnav:// streams (adding -nocache to your command line)

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000012f
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
DVDNAV, switched to title: 1
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: en aid: 129.
audio stream: 2 format: dts (5.1) language: en aid: 2.
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
audio stream: 4 format: ac3 (stereo) language: en aid: 132.
audio stream: 5 format: ac3 (stereo) language: en aid: 133.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
subtitle ( sid ): 3 language: unknown

MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9801.6 kbps (1225.2 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 56.22.100 (internal)
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 384.0 kbit/12.50% (ratio: 48000->384000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
[ac3 @ 0x7f4eadeeee40]exponent out-of-range
[ac3 @ 0x7f4eadeeee40]error decoding the audio block
[ac3 @ 0x7f4eadeeee40]frame sync error
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
[mpeg2video @ 0x7f4eadeeee40]ac-tex damaged at 18 3
[mpeg2video @ 0x7f4eadeeee40]Warning MVs not available
[mpeg2video @ 0x7f4eadeeee40]concealing 1215 DC, 1215 AC, 1215 MV errors in I frame
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 854x480 Planar YV12 
A:3838.4 V:3838.6 A-V: -0.207 ct:  0.000   2/  2 ??% ??% ??,?% 0 0 

demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
A:3840.9 V:3840.9 A-V: -0.004 ct: -0.166  60/ 57  4%  0%  0.4% 0 0 
```

---

### Post by ray field on 2015-02-18
I beg your pardon, mc -- I had the command-line usage wrong; just checked UMS on my PS3 and sure enough, r37373 streams DVD images successfully. 

sorry about that -- I try my best not to be an errant user but don't always succeed. many thanks for your work.

---

### Post by mc4man on 2015-02-18
> **ray field said:**
> I beg your pardon, mc -- I had the command-line usage wrong; just checked UMS on my PS3 and sure enough, r37373 streams DVD images successfully. 

sorry about that -- I try my best not to be an errant user but don't always succeed. many thanks for your work.
No problem & thanks for the heads up about needing to enable dvdnav (external) now in mplayer

---

### Post by andrew.46 on 2015-02-19
> **mc4man said:**
> 
```

Loading protocol-related profile 'protocol.dvdnav'
 
```


What do you have in your dvdnav protocol? My own is pretty basic:

```

[protocol.dvdnav]
profile-desc="Profile for reading DVD menus"
mouse-movements=yes
nocache=yes

```

which I have 'borrowed' from here:

[http://www.andrews-corner.org/topten.html](http://www.andrews-corner.org/topten.html)

:)

---

### Post by mc4man on 2015-02-19
> **andrew.46 said:**
> What do you have in your dvdnav protocol? My own is pretty basic:

```

[protocol.dvdnav]
profile-desc="Profile for reading DVD menus"
mouse-movements=yes
nocache=yes

```

which I have 'borrowed' from here:

[http://www.andrews-corner.org/topten.html](http://www.andrews-corner.org/topten.html)

:)
This is a fairly new install to a new ssd so I haven't set much of anything up yet.  Consequently the .mplayer/config is empty though what you have seems like a good addition.
Maybe mplayer checks/reports based on command?

---

