---
title: "VLC = (Pitch Black) NO Video, Only Sound."
date: 2013-02-16
forum: Multimedia Software
---

### Post by TimeCrank on 2013-02-16
Ok, I have been having a hard frustrating  time finding out what is wrong with my video player (**VLC**). I'm not just having problems with **VLC **but with all available video players for **Xubuntu** through **Ubuntu Software Center**.  VLC and some other video players will open a video file, play sound and  show black screen ( NO logo just black screen). Also some video players  I installed like **Parole** and others will not even open the video  files (some might open but crashes). I have view countless forums and  try so many solutions that just lead me back to a dead end. I have tried  reinstalling **Xubuntu** , **VLC.** Also downloaded and tried several codecs  and things of that nature.  ](*,)


_**HERE ARE SOME SPECS & ERROR CODES I GET:**_

[COLOR=Green] **_[COLOR=Red]PC Specs:[/COLOR]_**

VGA compatible controller[/COLOR]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

[COLOR=Green]CPU :[/COLOR] GenuineIntel Intel(R) Celeron(R) CPU 2.70GHz

[COLOR=Red]**_Video Info:_**[/COLOR]

[COLOR=Green]Type:[/COLOR] Video
[COLOR=Green]Codec:[/COLOR] MPEG-4 Video (XVID)
[COLOR=Green]Resolution:[/COLOR] 640x272
[COLOR=Green]Frame rate:[/COLOR] 23.976043
[COLOR=Green]Dcoded format:[/COLOR] Planar 4:2:0 YUV

NOTE: ( All my video filles are .AVI, I don't use any other video file type)

[COLOR=Red]ERROR CODES:[/COLOR]

[COLOR=Indigo][B]~$ vlc -v Desktop/zz.avi
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)
[0x82d1908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb5104e58] avcodec decoder warning: threaded frame decoding is not compatible with ffmpeg-hw, disabled
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/i915_drv_video.so
libva: va_openDriver() returns -1
[0xb5104e58] avcodec decoder warning: Failed to open VA API
[0xb5104e58] avcodec decoder warning: disabling direct rendering
[0xb5304bf0] main audio output warning: PTS is out of range (-9103), dropping buffer
[0xb5304bf0] main audio output warning: PTS is out of range (-32231), dropping buffer
[0xb5304bf0] pulse audio output warning: starting late (-15293 us)
[0xb5304bf0] pulse audio output warning: too early by 40561 us
[0xb5304bf0] pulse audio output warning: too early by 41084 us
[0x86e2958] main video output warning: picture is too late to be displayed (missing 450 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 410 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 369 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 329 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 289 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 248 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 207 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 166 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 124 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 83 ms)
[0x86e2958] main video output warning: picture is too late to be displayed (missing 427 ms)
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[mpeg4 @ 0xb51125e0] header damaged
[/B][/COLOR]:-k

IF you need more info just ask
[COLOR=Blue]THANKS IN ADVANCE: [/COLOR]:grin:

---

### Post by andrew.46 on 2013-02-17
For vlc try *un*checking the box for 'Accelerated Video Output (overlay)'. If that makes no difference leave it unchecked and experiment with some other video output devices. These settings are all in Tools --> Preferences --> Video.

Have you tried any media files on your machine rather than dvd?

---

### Post by TimeCrank on 2013-02-17
I have tried unchecking Accelerated video outpuy (overlay) , and messed around with all the video outputs with no luck. Some people tell me to try OpenGL output ,but when i tried that and it crashes. Also the only video files i have on my machine is .avi , i have converted one of the .avi to a .mp4 , but when i play the .mp4 it acts the same as if i was opening the .avi nothing changes. when i insert DVD and try to play its the same thing.

---

### Post by JoeHallenbeck on 2013-08-10
TimeCrank, how did you solve the problem? You have solved it,  haven't you? :) I just ran into the same thing.

Thanks in advance!

---

### Post by Rob Sayer on 2013-08-10
Apparently, there have been problems with that gpu in linux but they've been fixed by intel.  Since the desktop gui seems to work, I'd try different vlc video output module settings.

See:

[http://www.videolan.org/doc/vlc-user-guide/en/ch02.html#id330667](http://www.videolan.org/doc/vlc-user-guide/en/ch02.html#id330667)

Or, try the videolan forums.

---

### Post by jc4 on 2013-08-15
I had the same problem using xubuntu 12.04 on an old P4. But also on a new machine running xubuntu in a virtual machine. The solution for me was to go into VLC tools > preferences > video settings   and change the output to X11

---

