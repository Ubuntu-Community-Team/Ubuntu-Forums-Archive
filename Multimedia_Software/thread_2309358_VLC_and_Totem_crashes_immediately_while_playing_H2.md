---
title: "VLC and Totem crashes immediately while playing H265/HEVC"
date: 2016-01-09
forum: Multimedia Software
---

### Post by sag3 on 2016-01-09
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"][/TD]
[/TR]
[/TABLE]
 
I was trying to play a video of H265 mkv format on ubuntu 14.04.  Whenever I  try to play the video on totem,the video goes on for a few  seconds and  then totem crashes.

  In VLC,the window crashes immediately.I have installed all the   plugins for playing H265 but both of the softwares are not playing the   video.

  output of vlc in terminal 

```
VLC media player 2.1.6 Rincewind (revision 2.1.6-0-gea01d28)
[0x8128190] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xacd05270] main input error: Invalid PCR value in ES_OUT_SET_(GROUP_)PCR !
Segmentation fault (core dumped)
```

i have installed vlc-plugin-libde265,gstreamer0.10-libde265 and libde265 from 
repository ppa:strukturag/libde265

having this problem for x265 codec files only other files play fine on both players.

---

### Post by mc4man on 2016-01-10
Regarding totem, you installed the wrong version plugin, use gstreamer1.0-libde265_0.1.12-...., then try again. If still no good then best would be to post or link to a sample vid that fails.

vlc in 14.04 works fine here though the one I've installed doesn't need the plugin so no real comment atm there. 
1st check if totem can play with proper plugin.

---

### Post by sag3 on 2016-01-10
hi
as u said i installed gstreamer1.0-libde265 (0.1.12-1ppa1~trusty1) from synaptic. and tried to run my file on it it crashed immediately giving me no sign. same thing happening with vlc. both app crashes only when i try to play x265 files.  
tried to run totem from terminal 
 
```
crsag@SAG:~$ totem
Segmentation fault (core dumped)
```

Mediainfo of file i tried to play.

```
General
Unique ID                                : 208500769715564323477468840336434968283 (0x9CDBC99EFE5A42478AF3B40902C8B6DB)
Complete name                            : /mnt/sda3/#TORRENT/Series/Vikings/Season 1/Vikings S01E01 Rites of Passage (1080p x265 Joy).mkv
Format                                   : Matroska
Format version                           : Version 4 / Version 2
File size                                : 464 MiB
Duration                                 : 46mn 36s
Overall bit rate                         : 1 392 Kbps
Encoded date                             : UTC 
Writing application                      : mkvmerge v8.5.2 ('Crosses') 64bit
Writing library                          : Lavf55.12.0
DURATION                                 : 00:46:31.705000000
NUMBER_OF_FRAMES                         : 450
NUMBER_OF_BYTES                          : 14148
_STATISTICS_WRITING_APP                  : mkvmerge v8.5.2 ('Crosses') 64bit
_STATISTICS_WRITING_DATE_UTC             : 2015-12-08 18:06:20
_STATISTICS_TAGS                         : BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES

Video
ID                                       : 1
Format                                   : HEVC
Format/Info                              : High Efficiency Video Coding
Codec ID                                 : V_MPEGH/ISO/HEVC
Duration                                 : 46mn 36s
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Default                                  : Yes
Forced                                   : No
DURATION                                 : 00:46:36.878000000
NUMBER_OF_FRAMES                         : 67058
NUMBER_OF_BYTES                          : 418571053
_STATISTICS_WRITING_APP                  : mkvmerge v8.5.2 ('Crosses') 64bit
_STATISTICS_WRITING_DATE_UTC             : 2015-12-08 18:06:20
_STATISTICS_TAGS                         : BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : HE-AAC / LC
Codec ID                                 : A_AAC
Duration                                 : 46mn 36s
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz / 24.0 KHz
Compression mode                         : Lossy
Delay relative to video                  : -105ms
Title                                    : Surround
Default                                  : Yes
Forced                                   : No
DURATION                                 : 00:46:36.885000000
NUMBER_OF_FRAMES                         : 65552
NUMBER_OF_BYTES                          : 67125249
_STATISTICS_WRITING_APP                  : mkvmerge v8.5.2 ('Crosses') 64bit
_STATISTICS_WRITING_DATE_UTC             : 2015-12-08 18:06:20
_STATISTICS_TAGS                         : BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES

Text #1
ID                                       : 3
Format                                   : ASS
Codec ID                                 : S_TEXT/ASS
Codec ID/Info                            : Advanced Sub Station Alpha
Compression mode                         : Lossless
Language                                 : English
Default                                  : No
Forced                                   : No
DURATION                                 : 00:44:12.150000000
NUMBER_OF_FRAMES                         : 473
NUMBER_OF_BYTES                          : 24292
_STATISTICS_WRITING_APP                  : mkvmerge v8.5.2 ('Crosses') 64bit
_STATISTICS_WRITING_DATE_UTC             : 2015-12-08 18:06:20
_STATISTICS_TAGS                         : BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES

Text #2
ID                                       : 4
Format                                   : ASS
Codec ID                                 : S_TEXT/ASS
Codec ID/Info                            : Advanced Sub Station Alpha
Compression mode                         : Lossless
Language                                 : Norwegian Nynorsk
Default                                  : No
Forced                                   : No
DURATION                                 : 00:46:31.704000000
NUMBER_OF_FRAMES                         : 450
NUMBER_OF_BYTES                          : 23212
_STATISTICS_WRITING_APP                  : mkvmerge v8.5.2 ('Crosses') 64bit
_STATISTICS_WRITING_DATE_UTC             : 2015-12-08 18:06:20
_STATISTICS_TAGS                         : BPS DURATION NUMBER_OF_FRAMES NUMBER_OF_BYTES

Text #3
ID                                       : 5
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Language                                 : Arabic
Default                                  : No
Forced                                   : No

Text #4
ID                                       : 6
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Language                                 : Danish
Default                                  : No
Forced                                   : No

Text #5
ID                                       : 7
Format                                   : UTF-8
Codec ID                                 : S_TEXT/UTF8
Codec ID/Info                            : UTF-8 Plain Text
Language                                 : Swedish
Default                                  : No
Forced                                   : No


```

---

### Post by mc4man on 2016-01-10
That vid (same or quite similar, see screen) works fine here in 14.04 in totem with the plugin. also works fine in vlc & mpv.
If desired read here carefully, if using ppa then follow instructions & note that for the vlc in there you must use inc. vlc-libde265 plugin (0.1.7-1ppa1~trusty1.1), as that vlc build uses libav9 which does not support hevc.
(there is a sister ppa that moves 14.04 to libav11 which does support hevc in vlc directly but don't think you need atm
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)


And or try mpv, can be had here though note there is a little learning curve & mpv benefits from adding some options to a~/.config/mpv/mpv.conf file
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

Otherwise as it stands maybe try making sure that vlc is not trying to use hwdec on hevc as it's likely not supported on your hardware & or 14.04

---

### Post by sag3 on 2016-01-11
hi there video files are just same as yours.
installed vlc-libde265 plugin (0.1.7-1ppa1~trusty1.1) from given repo but still having crash
here are my crash files
[https://drive.google.com/folderview?id=0B2eJOT8n1vrxMm1PUFc4OTdDMEk&usp=sharing](https://drive.google.com/folderview?id=0B2eJOT8n1vrxMm1PUFc4OTdDMEk&usp=sharing)
please review them. all plugins are same as you said.

---

### Post by mc4man on 2016-01-11
Those crash logs aren't of any value, it's possible if you installed the dbg packages something would show up. (3 dbg packages avail., 1 for the lib, 1 for gsreamer plugin, 1 for vlc plugin
It appears to be some local issue, I had reason to ck. something on 14.04 so put up a fresh install. 
Before doing anything added the strukturag ppa, installed the lib &  plugins, repo vlc (2.1.6), gst-libav plugin  & both totem & vlc played the file fine.

( you could try removing ~/.config/vlc folder, should always be done when upgrading versions but doubt it would help.

Edit: you can get rid of those crash files with - 
```
sudo rm /var/crash/*.*
```

---

### Post by sag3 on 2016-01-11
well those crash happen only after installing libde265([http://ppa.launchpad.net/strukturag/libde265/ubuntu).i](http://ppa.launchpad.net/strukturag/libde265/ubuntu).i) installed dbg plugin for x265 to find out what is happening.
anyway now i now situation is on half way. i tried to purge vlc and vlc-data and .congfig files. removed all plugin related to x265 and rebooted system and installed all again.
now i can play some of those files on both player which was unable to play/crashed. but now i can see thumbnails for file which are playable and for unsupported files i do not get any. Infect when i try to right click/properties for files without thumbnails nautilus crash immediately.
one strange thing i noticed is when i play some of unsupported files (in here files which do not have image thumbnails) first time on vlc it can play but then i play it on totem it got crashed and bang....now i open same file on vlc it got crashed / now when i try to see properties nautilus go crash. seems like totem is making logs for that files. and making unable for playing those files again.
any steps for completely remove totem from it core all its logs,conf,plugins,data and install it again.
  
#mpv player works fine also installed SMplayer it great too.but still i want to solve my query here. i love vlc using it from years so i want it back. 

[ATTACH=CONFIG]266661[/ATTACH][ATTACH=CONFIG]266662[/ATTACH][ATTACH=CONFIG]266663[/ATTACH]

---

### Post by mc4man on 2016-01-11
Don't see any connection between totem & vlc so something is amiss locally, maybe the file(s), maybe something else.
Ubuntu 16.04 will handle hevc without any plugins so consider using it down the road. (15.10 also handles now..

Maybe try a couple of the hevc files hosted here (r. click > save link as ..), note that some of the links are currently dead.
[http://jell.yfish.us/](http://jell.yfish.us/)

---

### Post by ScottAllyn on 2016-01-11
> **mc4man said:**
> Maybe try a couple of the hevc files hosted here (r. click > save link as ..), note that some of the links are currently dead.
[http://jell.yfish.us/](http://jell.yfish.us/)

Let me know which links are broken and I'll fix 'em asap.

**Edit**: Nevermind; I found and fixed 'em! They've apparently been broken for weeks. People need to tell me this stuff... ::grumble::  :D

Also note that you shouldn't need to r-click to download them if I set things up properly; a regular click should start a download. Let me know if that's not working.

---

### Post by mc4man on 2016-01-11
> **ScottAllyn said:**
> 

Also note that you shouldn't need to r-click to download them if I set things up properly; a regular click should start a download. Let me know if that's not working.
Yeah, I noticed that after posting. 
Thanks for the samples, have found them quite useful since i stumbled across the site some time back.

---

### Post by andrew.46 on 2016-01-12
> **ScottAllyn said:**
> Let me know which links are broken and I'll fix 'em asap.

Thanks for that :). These files were created with x265 on Windows? I had a look at the smaller ones and it really looks like hevc is on the way, beautiful! Pity about the licensing / fees mess at the moment....

**Edit:** And nice to see that you made the Jellyfish page by hand :

```

<meta name="Generator" content="NotePad++ ; Yes, I typed all this crap by hand. - ScottAllyn"/>

```

:)

---

### Post by Yellow Pasque on 2016-01-12
My initial hunch would be a problem with va-api since it works with mpv/mplayer. What GPU and driver are you using? These commands should give us the info if you don't know:
```
sudo apt-get install mesa-utils vainfo
glxinfo | grep -i string
vainfo
```

Have you tried different video output options in VLC?
Do you have gstreamer1.0-vaapi installed, and if so, does removing that package allow totem to function?

---

### Post by ScottAllyn on 2016-01-12
> **andrew.46 said:**
> Thanks for that :). These files were created with x265 on Windows? I had a look at the smaller ones and it really looks like hevc is on the way, beautiful! Pity about the licensing / fees mess at the moment....

**Edit:** And nice to see that you made the Jellyfish page by hand :

```

<meta name="Generator" content="NotePad++ ; Yes, I typed all this crap by hand. - ScottAllyn"/>

```

:)

Yea, I used x265 for Windows.

Nobody's ever noticed that meta tag before; it used to be a bit more... rude. :D  I have used HTML editors in the past, but for a simple page like [http://jell.yfish.us/](http://jell.yfish.us/) , a text editor is all that's necessary.

---

### Post by sag3 on 2016-01-13
hey mc4man
downlaoded couple of jellyfish sample
[ATTACH=CONFIG]266708[/ATTACH]
all i can plays are x264s and 10bit hevc.
im amused by mpv/smplayer it can handle almost anything from 3mbps to 300. 

@Temüjin
i dont have not selected any video output for vlc all settings are on its default value 
here is output for ur code
```
crsag@SAG:~$ glxinfo | grep -i string
server glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Desktop x86/MMX/SSE2
OpenGL version string: 2.1 Mesa 10.5.9
OpenGL shading language version string: 1.20
crsag@SAG:~$ vainfo
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_38
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.38 (libva 1.6.0.pre1)
vainfo: Driver version: Intel i965 driver for Intel(R) Ironlake Desktop - 1.6.1.pre1 (1.6.1.pre1)
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileNone                   :    VAEntrypointVideoProc


```
well i tried tweaking with video output in past on win10 and ended up with still image so after then i changed it to auto which was its default.
i dont have have any external graphic card so never tweaked after then.

---

