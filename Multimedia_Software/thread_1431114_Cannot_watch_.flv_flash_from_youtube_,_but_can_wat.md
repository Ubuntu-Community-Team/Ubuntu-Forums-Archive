---
title: "Cannot watch .flv flash from youtube , but can watch using firefox"
date: 2010-03-16
forum: Multimedia Software
---

### Post by ubfu on 2010-03-16
Downloaded a video clip from youtube which the flash is encoded with AVC , ACC .No matter what player I am using , it still doesn't play

```
mediainfo

General
Complete name                    : /media/Local Disk_/video_002.flv
Format                           : Flash Video
File size                        : 30.3 MiB
Duration                         : 6mn 19s
Overall bit rate                 : 671 Kbps
httphostheader                   : v20.lscache4.c.youtube.com

Video
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : Main@L2.2
Format settings, CABAC           : Yes
Format settings, ReFrames        : 3 frames
Muxing mode                      : Container profile=Unknown@2.2
Duration                         : 6mn 19s
Bit rate                         : 568 Kbps
Width                            : 576 pixels
Height                           : 432 pixels
Display aspect ratio             : 4:3
Frame rate                       : 15.000 fps
Resolution                       : 8 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Bits/(Pixel*Frame)               : 0.152
Stream size                      : 25.7 MiB (85%)

Audio
Format                           : AAC
Format/Info                      : Advanced Audio Codec
Format version                   : Version 4
Format profile                   : LC
Format settings, SBR             : No
Duration                         : 6mn 19s
Bit rate                         : 96.6 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 44.1 KHz
Stream size                      : 4.36 MiB (14%)

```


```

ffmpeg -i video_002.flv


[flv @ 0xb7ee6110]Unsupported video codec (7)
[flv @ 0xb7ee6110]Unsupported video codec (7)
[flv @ 0xb7ee6110]Unsupported video codec (7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, flv, from 'video_002.flv':
  Duration: 00:06:18.6, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: 0x0007, 15.00 fps(r)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Must supply at least one output file

```

Hoping someone can guide me through.I had install ffmpeg using 8.04 Hardy.
Thanks

---

### Post by Jose Catre-Vandis on 2010-03-16
So what output do you get if you try mplayer or vlc through the terminal, e.g.

```
 mplayer video_002.flv

or

vlc video_002.flv


```

---

### Post by ubfu on 2010-03-16
> **Jose Catre-Vandis said:**
> So what output do you get if you try mplayer or vlc through the terminal, e.g.

```
 mplayer video_002.flv

or

vlc video_002.flv


```

Mplayer
```

[flv @ 0x8804094]Unsupported video codec (7)
[flv @ 0x8804094]Unsupported video codec (7)
[flv @ 0x8804094]Unsupported video codec (7)
[flv @ 0x8804094]Unsupported video codec (7)
[flv @ 0x8804094]skipping flv packet: type 97, size 7627016, flags 0
[flv @ 0x8804094]skipping flv packet: type 92, size 2021487, flags 0
[flv @ 0x8804094]skipping flv packet: type 97, size 3088933, flags 0
[flv @ 0x8804094]skipping flv packet: type 6, size 11573135, flags 0
[flv @ 0x8804094]skipping flv packet: type 69, size 9129175, flags 0
[flv @ 0x8804094]skipping flv packet: type 208, size 1882832, flags 0
[flv @ 0x8804094]skipping flv packet: type 186, size 13898455, flags 0
[flv @ 0x8804094]skipping flv packet: type 163, size 15270039, flags 0
[flv @ 0x8804094]skipping flv packet: type 241, size 8569150, flags 0
[flv @ 0x8804094]skipping flv packet: type 130, size 1463246, flags 0
[flv @ 0x8804094]skipping flv packet: type 117, size 11432747, flags 0
[flv @ 0x8804094]skipping flv packet: type 246, size 6247921, flags 0
[flv @ 0x8804094]skipping flv packet: type 163, size 7594917, flags 0
[flv @ 0x8804094]skipping flv packet: type 51, size 1690185, flags 0
[flv @ 0x8804094]skipping flv packet: type 188, size 7431248, flags 0
[flv @ 0x8804094]skipping flv packet: type 157, size 13069340, flags 0
[flv @ 0x8804094]skipping flv packet: type 131, size 11972969, flags 0
[flv @ 0x8804094]skipping flv packet: type 25, size 16624566, flags 0
[flv @ 0x8804094]skipping flv packet: type 0, size 12320635, flags 0
[flv @ 0x8804094]skipping flv packet: type 225, size 1412633, flags 0
[flv @ 0x8804094]skipping flv packet: type 112, size 16627939, flags 0
[flv @ 0x8804094]skipping flv packet: type 116, size 12702712, flags 0
[flv @ 0x8804094]skipping flv packet: type 55, size 4025530, flags 0
[flv @ 0x8804094]skipping flv packet: type 82, size 3332711, flags 0
[flv @ 0x8804094]skipping flv packet: type 114, size 13318591, flags 0
[flv @ 0x8804094]skipping flv packet: type 2, size 16104431, flags 0
[flv @ 0x8804094]skipping flv packet: type 41, size 3380023, flags 0
[flv @ 0x8804094]skipping flv packet: type 3, size 8310649, flags 0
[flv @ 0x8804094]skipping flv packet: type 162, size 8124322, flags 0
[flv @ 0x8804094]skipping flv packet: type 167, size 873385, flags 0
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  []  0x0  0bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Cannot find codec matching selected -vo and video format 0x7.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmspdmod.dll, /usr/lib/win32/wmspdmod.dll, /usr/local/lib/win32/wmspdmod.dll
IMediaObject ERROR: 0x88ac029  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmspdmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: wmavds32.ax, /usr/lib/win32/wmavds32.ax, /usr/local/lib/win32/wmavds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=wmavds32.ax, r=0x0)
ERROR: Could not open required DirectShow codec wmavds32.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video


Exiting... (End of file)
```

VLC

```
[flv @ 0xb1fea110]Unsupported video codec (7)
[flv @ 0xb1fea110]Unsupported video codec (7)
[flv @ 0xb1fea110]Unsupported video codec (7)
[flv @ 0xb1fea110]Unsupported video codec (7)
[00000357] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.
[00000397] main decoder error: no suitable decoder module for fourcc `undf'.
VLC probably does not support this sound or video format.

```

---

### Post by mc4man on 2010-03-16
It's probable that the version of the ffmpeg libs used in hardy is too old (though not the only possible reason

similar errors on hardy (a bit convoluted because poster was using several diff. ver, of the same video

[http://ubuntuforums.org/showthread.php?t=1117283&page=7](http://ubuntuforums.org/showthread.php?t=1117283&page=7)

If desired to try the latest mplayer, then I'd build one, guide here (uses it's own internal ffmpeg libs for decoding
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

For the latest ffmpeg -  guide here (choose the hardy guide
[http://microsoft_rules.ubuntuforums.org/showthread.php?t=786095](http://microsoft_rules.ubuntuforums.org/showthread.php?t=786095)

There is a newer mplayer pre-built in this ppa (by the dev of smplayer), 

[https://launchpad.net/~rvm/+archive/mplayer?field.series_filter=hardy](https://launchpad.net/~rvm/+archive/mplayer?field.series_filter=hardy)

for hardy you'd need to click on the "Technical details about this PPA " and copy this line into System -> Admin -> Software Sources -> Third Party -> Add, then click close and *reload *
(will complain about signing key, I never bother to add, doesn't matter, nor do I know about adding signing keys - probably not hard to do if wanted

```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu hardy main
```

Then you'd find a new mplayer update avail. in update manager or synaptic

---

### Post by ubfu on 2010-03-16
> **mc4man said:**
> It's probable that the version of the ffmpeg libs used in hardy is too old (though not the only possible reason

similar errors on hardy (a bit convoluted because poster was using several diff. ver, of the same video

[http://ubuntuforums.org/showthread.php?t=1117283&page=7](http://ubuntuforums.org/showthread.php?t=1117283&page=7)

If desired to try the latest mplayer, then I'd build one, guide here (uses it's own internal ffmpeg libs for decoding
[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

For the latest ffmpeg -  guide here (choose the hardy guide
[http://microsoft_rules.ubuntuforums.org/showthread.php?t=786095](http://microsoft_rules.ubuntuforums.org/showthread.php?t=786095)

There is a newer mplayer pre-built in this ppa (by the dev of smplayer), 

[https://launchpad.net/~rvm/+archive/mplayer?field.series_filter=hardy](https://launchpad.net/~rvm/+archive/mplayer?field.series_filter=hardy)

for hardy you'd need to click on the "Technical details about this PPA " and copy this line into System -> Admin -> Software Sources -> Third Party -> Add, then click close and *reload *
(will complain about signing key, I never bother to add, doesn't matter, nor do I know about adding signing keys - probably not hard to do if wanted

```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu hardy main
```

Then you'd find a new mplayer update avail. in update manager or synaptic

Sorry , I dont understand how do it.Which step I need to start frist ? how to compile and install some lib ? 
Newbie ,sorry .

---

### Post by ubfu on 2010-03-24
I am having issue on step 7 
[http://ubuntuforums.org/showpost.php?p=6963607](http://ubuntuforums.org/showpost.php?p=6963607)
> Install FFmpeg
7. Get the most current source files from the official FFmpeg svn, compile, and install. Run "./configure --help" to see what features or codecs you can enable/disable and which have a native implementation. If you are behind a firewall or unable to use subversion, then nightly FFmpeg snapshots are also available.
Code:
```
cd
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
make
sudo checkinstall --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --backup=no --default
```

The problem I am having is 

```

svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg


Fetching external item into 'ffmpeg/libswscale'
Checked out external at revision 30955.

Checked out revision 22652.

Makefile:1: config.mak: No such file or directory
libavutil/Makefile:1: libavutil/../config.mak: No such file or directory
libavutil/../subdir.mak:96: warning: overriding commands for target `libavutil/'
libavutil/../subdir.mak:26: warning: ignoring old commands for target `libavutil/'
libavutil/../subdir.mak:96: warning: overriding commands for target `libavutil/'
libavutil/../subdir.mak:96: warning: ignoring old commands for target `libavutil/'
make: *** No rule to make target `libavutil/../config.mak'.  Stop.
ng@ng-desktop:~/ffmpeg$ sudo checkinstall --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --backup=no --default

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu-desktop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ ffmpeg ]
3 -  Version: [ 3:0.svn20100324-12ubuntu3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ffmpeg ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Makefile:1: config.mak: No such file or directory
libavutil/Makefile:1: libavutil/../config.mak: No such file or directory
libavutil/../subdir.mak:96: warning: overriding commands for target `libavutil/'
libavutil/../subdir.mak:26: warning: ignoring old commands for target `libavutil/'
libavutil/../subdir.mak:96: warning: overriding commands for target `libavutil/'
libavutil/../subdir.mak:96: warning: ignoring old commands for target `libavutil/'
make: *** No rule to make target `libavutil/../config.mak'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

Any help ? why I can't make the file ?

---

### Post by Chronon on 2010-03-24
Can you post everything?  I see where you check out the code from SVN.  I don't see you changing directory or running the configure command or make.

---

