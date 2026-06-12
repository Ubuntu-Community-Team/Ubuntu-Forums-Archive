---
title: "VLC and Mplayer produce a pure green window"
date: 2013-06-06
forum: Multimedia Software
---

### Post by kornelix on 2013-06-06
I just changed computers to an Intel Haswell with integrated GPU. VLC and Mplayer are no longer able to play a DVD: the video is a pure green window, but the audio works OK. Totem works OK for both video and audio. Mplayer complains about a missing codec but does not say what codec is missing. This is Ubuntu 13.04. 

Anybody know what is wrong?

---

### Post by andrew.46 on 2013-06-06
Can you give the terminal output for MPlayer that shows the error? An easy way is to use SMPlayer and then post the MPlayer logs from 'Options --> View Logs --> MPlayer'.

---

### Post by Yellow Pasque on 2013-06-06
> I just changed computers to an Intel Haswell with integrated GPU. 
What were you using before?
For VLC, go into the Video options (Tools -> Options) and try playing with different video outputs? Any difference?

---

### Post by kornelix on 2013-06-07
Here is the requested MPlayer log

/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao pulse -nokeepaspect -framedrop -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 46137379 -monitorpixelaspect 1 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/mico/.config/smplayer/styles.ass -font Arial -subfont-autoscale 0 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 50 -dvd-device /dev/dvd -dvdangle 1 -nocache -osdlevel 0 -vf-add screenshot -noslices -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 dvd://2


MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.


Playing dvd://2.
libdvdread: Using libdvdcss version 1.2.12 for DVD access
ID_DVD_TITLES=6
ID_DVD_TITLE_1_CHAPTERS=1
ID_DVD_TITLE_1_ANGLES=1
ID_DVD_TITLE_2_CHAPTERS=7
ID_DVD_TITLE_2_ANGLES=1
ID_DVD_TITLE_3_CHAPTERS=7
ID_DVD_TITLE_3_ANGLES=1
ID_DVD_TITLE_4_CHAPTERS=7
ID_DVD_TITLE_4_ANGLES=1
ID_DVD_TITLE_5_CHAPTERS=7
ID_DVD_TITLE_5_ANGLES=1
ID_DVD_TITLE_6_CHAPTERS=25
ID_DVD_TITLE_6_ANGLES=1
ID_DVD_TITLE_1_LENGTH=0.480
ID_DVD_TITLE_2_LENGTH=2980.480
ID_DVD_TITLE_3_LENGTH=2957.480
ID_DVD_TITLE_4_LENGTH=2794.480
ID_DVD_TITLE_5_LENGTH=2560.480
ID_DVD_TITLE_6_LENGTH=11291.480
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_03_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_04_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_05_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_06_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_07_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_08_0.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VTS_09_0.IFO failed
ID_DVD_DISC_ID=A0F6B508BD14DA61E192443405EB7ACA
ID_DVD_VOLUME_ID=BBCDVD1180
There are 6 titles on this DVD.


ID_DVD_CURRENT_TITLE=2
There are 1 angles in this DVD title.


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000126
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001a436
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x0001a436)
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001a43b
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0001a43b)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0001a48f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0001ae27
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 1
audio stream: 0 format: ac3 (stereo) language: en aid: 128.


ID_AUDIO_ID=128
ID_AID_128_LANG=en
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en


ID_SUBTITLE_ID=0
ID_SID_0_LANG=en
subtitle ( sid ): 1 language: en


ID_SUBTITLE_ID=1
ID_SID_1_LANG=en
number of subtitles on disk: 2


CHAPTERS: 00:00:00.000,00:11:14.880,00:23:02.760,00:32:19.760,00:39:24.000,00:43:11.440,00:49:40.000,
ID_VIDEO_ID=0
Detected file format: MPEG-PS
ID_AUDIO_ID=128
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  9400.0 kbps (1175.0 kbyte/s)
ID_FILENAME=dvd://2
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000002
ID_VIDEO_BITRATE=9400000
ID_VIDEO_WIDTH=720
ID_VIDEO_HEIGHT=576
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_START_TIME=0.29
ID_LENGTH=2980.48
ID_SEEKABLE=1
ID_CHAPTERS=7
ID_CHAPTER_ID=0
ID_CHAPTER_0_START=18446744073709550616
ID_CHAPTER_ID=1
ID_CHAPTER_1_START=18446744073709550616
ID_CHAPTER_ID=2
ID_CHAPTER_2_START=18446744073709550616
ID_CHAPTER_ID=3
ID_CHAPTER_3_START=18446744073709550616
ID_CHAPTER_ID=4
ID_CHAPTER_4_START=18446744073709550616
ID_CHAPTER_ID=5
ID_CHAPTER_5_START=18446744073709550616
ID_CHAPTER_ID=6
ID_CHAPTER_6_START=18446744073709550616
[ass] auto-open
Opening video filter: [screenshot]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 8 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
ID_VIDEO_CODEC=ffmpeg2
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[ac3 @ 0x7f154d664320]frame sync error
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
ID_AUDIO_BITRATE=192000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffac3
[Mixer] No hardware mixing, inserting volume filter.
Starting playback...
[mpeg2video @ 0x7f154d664320]ac-tex damaged at 39 4
[mpeg2video @ 0x7f154d664320]Warning MVs not available
[mpeg2video @ 0x7f154d664320]concealing 1440 DC, 1440 AC, 1440 MV errors
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
ID_VIDEO_ASPECT=1.3333
VO: [xv] 720x576 => 768x576 Planar YV12 


ID_VIDEO_TRACK=0
ID_VIDEO_TRACK=0


ID_AUDIO_TRACK=128


ID_SUBTITLE_ID=0

---

### Post by kornelix on 2013-06-08
Results of changing the video output method in VLC:
+ default: green window
+ direct FB: black window
+ X11: Worked OK !

Thanks for the help.

Before the Haswell CPU I was using a Sandy Bridge Core i5 and a low budget Nvidia GPU.

---

### Post by kornelix on 2013-06-08
How the heck does one mark a problem as SOLVED?

---

### Post by BlinkinCat on 2013-06-08
> **kornelix said:**
> How the heck does one mark a problem as SOLVED?

Hi,

Here's how to mark your first post as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by Iowan on 2013-06-08
> **kornelix said:**
> How the heck does one mark a problem as SOLVED?Edit the first post and change the prefix.
We installed a "Solved" plug-in, but had issues.  Dunno if they got fixed.

---

