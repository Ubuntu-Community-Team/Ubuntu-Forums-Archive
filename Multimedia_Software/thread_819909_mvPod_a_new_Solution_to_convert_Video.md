---
title: "mvPod a new Solution to convert Video"
date: 2008-06-05
forum: Multimedia Software
---

### Post by ikus060 on 2008-06-05
Hi every one,

Every week I see tone of post related to conversion of video file. Usually, there is always a command line tool to do the job. For experienced user it's fine but for other people like me it's annoying and we prefer a GUI tool that are user friendly.

To solve this problem under linux, I develop a small application that use mplayer/mencoder to preview and encode video file. This application are in active development and I release it in alpha version on June 03, 2008.

The current version only support the well known iPod. 

I really want to support more than one output video format and the application are design for that. I'm just waiting for you suggestion. Fill ticket with Preset request and depending on the difficulty to implement it, it's will be release in version final 0.1 release.

Any one that are interested, go visit [http://mvpod.sourceforge.net](http://mvpod.sourceforge.net)

ikus060

---

### Post by kostkon on 2008-06-06
Nice project you have there! I currently use *FFmpeg* with the *WiFF* frontend but I'll give your app a try, it looks really good. :)

---

### Post by ikus060 on 2008-06-06
Thanks !

Let me know if you have any problem getting it started. I test it in a lot of environment but linux can alway be surprising !

I also thinks it's a good project and it's can be very useful for a lot of people using Linux because, at this time, there is no easy way to convert a video with all the scalability that mvPod offer.

The alpha version are ready to convert video for iPod, I just complete this morning a conversion of all my video of different size and format and it's work without a problem.

---

### Post by yuv656 on 2008-07-03
I tried adding a video file, but I get this error:
Impossible to find mplayer

I have installed mplayer, and verified that its executable is in /usr/bin as configured in mvpod's preferences, but it still doesn't work.

Nevertheless, the application looks promising! If there's something I would recommend, it is to get a person to check the English

---

### Post by yuv656 on 2008-07-03
Ah, I see I need to install gpac, trying that now..

---

### Post by yuv656 on 2008-07-03
Nope, that didn't fix it. Any ideas?

---

### Post by jedthehumanoid on 2008-07-14
> **yuv656 said:**
> Nope, that didn't fix it. Any ideas?

You'll have to install mencoder in addition to mplayer, the error message is a little cryptic

I have gotten a little longer, the video succesfully converts, but eventough itunes swallows it without complaining it never shows up in library...am I missing something?

---

### Post by blaise69 on 2008-07-28
Hi ikus060,

I'm keen to try out mvPod but I'm not sure how to build the files I downloaded from the website.

I followed the installation instructions, but they stopped short at actually how to install mvPod!?

Any help here would be really appreciated.

---

### Post by ikus060 on 2008-07-29
Hi everyone,
Sorry for the long delay, I didn't receive any e-mail notification for your post.

Starting from the first reply
> I tried adding a video file, but I get this error:
Impossible to find mplayer

I have installed mplayer, and verified that its executable is in /usr/bin as configured in mvpod's preferences, but it still doesn't work.

As mention by jedthehumanoid you have to install mencoder, gpac, and other dependencies. I suggest you follow the instruction present on the web site [http://mvpod.homeip.net:8080/wiki/mvPodInstallInstruction]("http://mvpod.homeip.net:8080/wiki/mvPodInstallInstruction"). In case you follow the instruction and it's doesn't work. Send me the logs generate by mvPod. You can get the logs by executing mvPod in a terminal.

> Nevertheless, the application looks promising! If there's something I would recommend, it is to get a person to check the English.

I know, I'm English is terrible ! I try to do my best ... 
If you want, you can help me to "correct" this problem.

---

### Post by ikus060 on 2008-07-29
> **jedthehumanoid said:**
> You'll have to install mencoder in addition to mplayer, the error message is a little cryptic

I have gotten a little longer, the video succesfully converts, but eventough itunes swallows it without complaining it never shows up in library...am I missing something?

Seriously, I'm not sure to understand you problem. You convert the video using mvPod and try to import it into iTunes library ?

If you can give me more detail it's will help me.

Thanks

---

### Post by ikus060 on 2008-07-29
> **blaise69 said:**
> Hi ikus060,

I'm keen to try out mvPod but I'm not sure how to build the files I downloaded from the website.

I followed the installation instructions, but they stopped short at actually how to install mvPod!?

Any help here would be really appreciated.


If you try to install mvPod from the distribution package available from SourceForge, you can use the installation instruction present on the web site.

If you get the source code of mvPod from the SVN, it's a bit more complicated than installing it.

I plan to make available a nightly build of mvPod. Maybe it's will be more interesting for you ?

If really want to compile mvPod from source Code, I will write the documentation to do so.

---

### Post by ikus060 on 2008-07-29
I check the docs present on the web site. I already document the installation from SVN. Read section Installation from SVN. If I remember well, I test it on a fresh installation. So it's should work without problem.

---

### Post by blaise69 on 2008-07-29
Thanks iksus060 you made me check the sourceforge page again, it turns out I downloaded the src files accidently.

---

### Post by ikus060 on 2008-07-29
> **blaise69 said:**
> Thanks iksus060 you made me check the sourceforge page again, it turns out I downloaded the src files accidently.
It's make sense !
Tell me if you got any problem getting mvPod work properly.

---

### Post by ikus060 on 2008-08-04
> **blaise69 said:**
> Thanks iksus060 you made me check the sourceforge page again, it turns out I downloaded the src files accidently.

Hi blaise69,

I want to inform you that a nightly build are available. It's not a release version, but it's more stable then previous alpha version release.

ikus060

---

### Post by franzb on 2008-08-11
Hi!

I've tried out mvPod and like it. It is a great alternative for tools like Videora or Handshake. Thanks for the work to the programmers!

What I am missing is the possibility to choose the dimension for the iPod Touch, 480x320. It would be great if it was added.

Sincerely,

Franz

---

### Post by ikus060 on 2008-08-11
> **franzb said:**
> Hi!

I've tried out mvPod and like it. It is a great alternative for tools like Videora or Handshake. Thanks for the work to the programmers!

What I am missing is the possibility to choose the dimension for the iPod Touch, 480x320. It would be great if it was added.

Sincerely,

Franz


Great that you like the application. I didn't know that iPod support video with such dimension. It's will not take very long time to add this feature, but please, can you add a ticket on mvPod web site : [http://mvpod.sf.net](http://mvpod.sf.net)

It's will be available in the nightly build until I release the beta version.

Thanks

---

### Post by franzb on 2008-08-11
Thank you for your quick reply. I have created a ticket.

Franz

---

### Post by fcastillo on 2008-10-21
I'm trying to use mvPod, but I after trying to convert some video, only at the end it gave me an error. I'd like to use an svn version, but the mvPod website is down, and in sourceforge.net there isn't any information on svn, or a bug tracker or anything at all. Is the project still being developed?

---

### Post by Pinejoker on 2008-10-21
the links its not working?:confused::confused:

---

### Post by ikus060 on 2008-10-21
Hi fcastillo,

Sorry if the mvPod web site are still down. I'm in maintenance mode for this server and mvPod are not on my priority list. I have many service to migrate and I cannot migrate everything smoothly cause the other server just crash. :(

There version I suggest you to use are the one present on sourceforge.net or the nightly build : [http://mvpod.sourceforge.net/nightly/](http://mvpod.sourceforge.net/nightly/)


For the problem you have. Please, execute mvPod from command line ($ ./mvpod.sh). This way logs will be available in the terminal. Post this log on the forum and I will help you.

---

### Post by ikus060 on 2008-10-21
Hi,

I create for that mater a mailing list in SourceForge for this sort of discussion.

Here the link : [https://sourceforge.net/mail/?group_id=225701](https://sourceforge.net/mail/?group_id=225701)

In answer to fcastillo, mvPod still in developement. There is no final release yet ! mvPod are develop mainly by me, but other people give me some help.

---

### Post by mocha on 2008-10-22
ikus,

I really enjoy mvpod, it's the only mencoder frontend I can find that supports easy GUI batch encoding and 2 pass.  When are you planning to add a deinterlacing option?  Thanks.

---

### Post by ikus060 on 2008-10-22
> **mocha said:**
> ikus,

I really enjoy mvpod, it's the only mencoder frontend I can find that supports easy GUI batch encoding and 2 pass.  When are you planning to add a deinterlacing option?  Thanks.

It's really hard to answer this question. I have so many thing to work on. In November I should have spare time. I will invest some time to implement interesting feature. I plan to release a final version in December.

It's sure that it's will be in the final version.

Also, I invite any Java developer to help me. We are an open source community no ?

---

### Post by ikus060 on 2008-10-23
Hi fcastillo,

I want a know if you solve your problem.

Also, mvpod webSite are stable and running.

---

### Post by mocha on 2008-10-29
ikus060,

Regarding the nightly builds on your site, are there any differences on a daily basis?  I don't see any documented changes and the file names don't change in version number.  Are they just generated automatically by Trac?

---

### Post by ikus060 on 2008-10-29
> **mocha said:**
> ikus060,

Regarding the nightly builds on your site, are there any differences on a daily basis?  I don't see any documented changes and the file names don't change in version number.  Are they just generated automatically by Trac?


I have a server that recompile mvPod every night. The build number refer the the subversion revision. So if there is no change made during the day, the build number doesn't change.

---

### Post by Glendon on 2008-11-07
I just started using mvPod. 

I love it. It does exactly what I need it to do. 

I'm getting some failed conversions occasionally. I can't seem to figure out why.

The good news is that although mvPod reports the conversion as failed, the video works. So it's not really that big of an issue really. 

Thanks!

---

### Post by ikus060 on 2008-11-07
Hi Glendon,

I'm developing mvPod and I'm interest in your problem of failure. Next time you got a failure, can you send my the 'more info'. It's available by cliking on 'MoreInfo' in the job queue.

Regards

    Patrik Dufresne

---

### Post by Glendon on 2008-11-07
Just got another failure while trying to convert. I've got three AVI's in the Job Queue. 

I clicked More Info but the resulting dialog box doesn't contain any text. Just a red warning icon. 

Is there a way for me to turn on debugging?

---

### Post by craigni on 2008-11-23
Great app, many thanks.  Just a heads up for those who are installing--I'm running a quad core and so downloaded the current 64 bit build from the web page (mvPod-0.0.1.67-x86_64.tar.gz) which bombed out every time it tried to encode the audio track.  Just downloaded the latest nightly build (mvPod-0.0.1.71-x86_64.tar.gz) and it works just fine, but you have to install mp4creator which you can get by
```

sudo apt-get install mpeg4ip-server

```

---

### Post by ikus060 on 2008-11-23
> **craigni said:**
> Great app, many thanks.  Just a heads up for those who are installing--I'm running a quad core and so downloaded the current 64 bit build from the web page (mvPod-0.0.1.67-x86_64.tar.gz) which bombed out every time it tried to encode the audio track.  Just downloaded the latest nightly build (mvPod-0.0.1.71-x86_64.tar.gz) and it works just fine, but you have to install mp4creator which you can get by
```

sudo apt-get install mpeg4ip-server

```


Hi craigni,

Actually, installation of mp4creator is only mandatory for the nightly build. MP4Box was broken in Intrepid Ibex for this reason I move on and switch to mp4creator. Before the final release in December, I will change the documentation properly to reflect the use of mp4creator.

Have fun using mvPod.

ikus060

---

### Post by craigni on 2008-11-23
The installation strategy of mvpod seems to be just put it somewhere, and run it from that location.  Since I wanted a system wide installation, I wanted to put it in /opt/mvpod, and when I ran it from there installed as sudo, I got 'class not found' errors.  It took me a little while to figure out that there were some funky permissions in the file structure, so for those who want a system wide installation, here's what I ended up doing.  If anybody has a better solution, I'm all ears.  (Just replace /opt/mvpod with whatever directory you want to install to)
```

sudo mkdir /opt/mvpod
sudo tar -C /opt/mvpod -xvzf mvPod-0.0.1.71-x86_64.tar.gz 
sudo chmod a+rw /opt/mvpod/bin/mvpod.properties 
sudo chmod -R a+r /opt/mvpod

```
Add the following line to /etc/bash.bashrc
```

alias mvpod='/opt/mvpod/bin/mvpod &'

```

---

### Post by craigni on 2008-11-23
> 
Actually, installation of mp4creator is only mandatory for the nightly build

I needed the nightly build as the one on the main page (1.67) bombed out encoding the audio tracks.  I expect others may experience that as well, so I posted my experience.  Great app, keep up the great work!

---

### Post by ikus060 on 2008-11-23
> **craigni said:**
> The installation strategy of mvpod seems to be just put it somewhere, and run it from that location.  Since I wanted a system wide installation, I wanted to put it in /opt/mvpod, and when I ran it from there installed as sudo, I got 'class not found' errors.  It took me a little while to figure out that there were some funky permissions in the file structure, so for those who want a system wide installation, here's what I ended up doing.  If anybody has a better solution, I'm all ears.  (Just replace /opt/mvpod with whatever directory you want to install to)
```

sudo mkdir /opt/mvpod
sudo tar -C /opt/mvpod -xvzf mvPod-0.0.1.71-x86_64.tar.gz 
sudo chmod a+rw /opt/mvpod/bin/mvpod.properties 
sudo chmod -R a+r /opt/mvpod

```
Add the following line to /etc/bash.bashrc
```

alias mvpod='/opt/mvpod/bin/mvpod &'

```


Hi craigni,

It's interesting ... I'm gonna look into it.  I find it weird you need to set read-write permission on mvpod.properties. For other files, it's should work at is. Can you add a Ticket with this information .. I will try to figure out the problem before the final release.

Also, I don't suggest you to create an alias in bash.bashrc. It's better to create a symbolic link or add the directory to the $path variable.

Thanks

---

### Post by nstdnl on 2009-01-11
> **ikus060 said:**
> 
I find it weird you need to set read-write permission on mvpod.properties. For other files, it's should work at is. Can you add a Ticket with this information .. I will try to figure out the problem before the final release.
Thanks

Hej! I am interested if you found a solution, as I would like to be able to run mvpod from any folder as well.

At the moment I have the following error when starting mvpod (placed in /opt/):

```

daniel@datorn:~$ mvpod
searching default java
Starting application ...
Exception in thread "main" java.lang.NoClassDefFoundError: net/homeip/entreprisesmd/mvconv/gui/Main
Caused by: java.lang.ClassNotFoundException: net.homeip.entreprisesmd.mvconv.gui.Main
...

```

Thanks for any advice!

/Daniel

---

### Post by Ni85 on 2009-04-26
hey
i just tried to encode my first video for the ipod, but after the whole process was done, it gave me a "failed" message.. i tried with a couple of different files and it does the same.

i just followed the guide on the website, and everything seemed to run smoothly.

any advice?

this should be all the output i get

```
wrapper>> /usr/bin/mencoder /media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.avi -aid 1 -o /media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4 -ovc x264 -x264encopts bitrate=500:nocabac:direct_pred=auto:me=umh:frameref=1:level_idc=13:partitions=all:subq=6:threads=auto:trellis=1:vbv_maxrate=768:vbv_bufsize=244:bframes=0 -oac faac -faacopts br=128:mpeg=4:object=2 -channels 2 -srate 48000 -vf-add scale=640:-10 -vf-add harddup 

WARNING: OUTPUT FILE FORMAT IS _AVI_. See -of help.
x264 [info]: using SAR=1/1
x264 [warning]: frame MB size (40x30) > level limit (396)
x264 [warning]: MB rate (28771) > level limit (11880)
x264 [info]: using cpu capabilities: MMX MMXEXT SSE SSE2 SSE3 SSSE3 Cache64 

Skipping frame!
x264 [info]: slice I:281   Avg QP:25.58  size: 11609
x264 [info]: slice P:31462 Avg QP:21.18  size:  2461
x264 [info]: mb I  I16..4: 56.6%  0.0% 43.4%
x264 [info]: mb P  I16..4:  4.7%  0.0%  1.1%  P16..4: 30.2%  6.6%  0.9%  0.1%  0.0%    skip:56.3%
x264 [info]: final ratefactor: 23.51
x264 [info]: kb/s:487.6
wrapper>> /usr/bin/mplayer /media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi -v -msglevel identify=9 -vo null -ao null -frames 0 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/tado/.mplayer/codecs.conf'
Reading /home/tado/.mplayer/codecs.conf: Can't open '/home/tado/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --enable-runtime-cpudetection --prefix=/usr --confdir=/etc/mplayer --mandir=/usr/share/man --win32codecsdir=/usr/lib/win32 --enable-largefiles --disable-libdvdcss-internal --enable-smb --enable-ftp --enable-cdparanoia --enable-radio --enable-lirc --enable-joystick --enable-xf86keysym --disable-tremor-internal --enable-liba52 --enable-musepack --enable-speex --enable-libvorbis --enable-mad --enable-mp3lib --enable-theora --enable-libdv --enable-libmpeg2 --enable-tv-v4l2 --enable-alsa --enable-ossaudio --enable-esd --enable-arts --enable-pulse --enable-nas --enable-xinerama --enable-menu --enable-xv --enable-vm --enable-gl --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-sdl --enable-aa --enable-caca --enable-dxr3 --enable-xvmc --with-xvmclib=XvMCW --enable-ggi --enable-fbdev --disable-ivtv --enable-freetype --enable-gif --enable-png --enable-jpeg --enable-liblzo --enable-fribidi --enable-ladspa --enable-libamr_nb --enable-libamr_wb --enable-faac --enable-gui --enable-mencoder
CommandLine: '/media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi' '-v' '-msglevel' 'identify=9' '-vo' 'null' '-ao' 'null' '-frames' '0'
init_freetype
get_path('font/font.desc') -> '/home/tado/.mplayer/font/font.desc'
font: can't open file: /home/tado/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/tado/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/tado/.mplayer/input.conf'
Can't open input config file /home/tado/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 81 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi.conf') -> '/home/tado/.mplayer/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi.conf'

Playing /media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi.
get_path('sub/') -> '/home/tado/.mplayer/sub/'
[file] File size is 104172858 bytes
STREAM: [file] /media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
LAVF_check: avi format
AVI file format detected.
list_end=0x186
======= AVI Header =======
us/frame: 41708  (fps=23.976)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (2320) HAS_INDEX IS_INTERLEAVED TRUST_CKTYPE
frames  total: 31743   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  640 x 480
==========================
list_end=0x120
==> Found video stream: 0
ID_VIDEO_ID=0
[aviheader] Video stream found, -vid 0
====== STREAM Header =====
Type: vids   FCC: h264 (34363268)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 2997/125 = 23.976
Start: 0   Len: 31743
Suggested BufferSize: 17455
Quality 0
Sample size: 0
==========================
Found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 640
  biHeight 480
  biPlanes 1
  biBitCount 24
  biCompression 875967080='h264'
  biSizeImage 921600
===========================
======= Video Properties Header =======
Format: 0  VideoStandard: 0
VRefresh: 24  HTotal: 640  VTotal: 480
FrameAspect: 4:3  Framewidth: 640  Frameheight: 480
Fields: 1
  == Field 0 description ==
  CompressedBMHeight: 480  CompressedBMWidth: 640
  ValidBMHeight: 480  ValidBMWidth: 640
  ValidBMXOffset: 0  ValidBMYOffset: 0
  VideoXOffsetInT: 0  VideoYValidStartLine: 0
=======================================
list_end=0x186
==> Found audio stream: 1
ID_AUDIO_ID=1
[aviheader] Audio stream found, -aid 1
====== STREAM Header =====
Type: auds   FCC: mp (706D)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 24
Rate: 48000/1024 = 46.875
Start: 0   Len: 62064
Suggested BufferSize: 7168
Quality 0
Sample size: 0
==========================
Found 'wf', 18 bytes of 18
======= WAVE Format =======
Format Tag: 28781 (0x706D)
Channels: 2
Samplerate: 48000
avg byte/sec: 15992
Block align: 1024
bits/sample: 0
cbSize: 0
==========================================================================
list_end=0x1C2
hdr=Software  size=40
Software  : MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1
list_end=0x61EA642
Found movie at 0x100C - 0x61EA642
Reading INDEX block, 93807 chunks for 31743 frames (fpos=102671946).
AVI index offset: 0x1008 (movi=0x100C idx0=0x4 idx1=0x46)
Auto-selected AVI audio ID = 1
Auto-selected AVI video ID = 0
AVI: Searching for audio stream (id:1)
AVI video size=80697110 (31743) audio size=21173350 (62064)
VIDEO:  [h264]  640x480  24bpp  23.976 fps  487.6 kbps (59.5 kbyte/s)
[V] filefmt:3  fourcc:0x34363268  size:640x480  fps:23.98  ftime:=0.0417
Clip info:
 Software: MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1
ID_CLIP_INFO_NAME0=Software
ID_CLIP_INFO_VALUE0=MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1
ID_CLIP_INFO_N=1
get_path('sub/') -> '/home/tado/.mplayer/sub/'
ID_FILENAME=/media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi
ID_DEMUXER=avi
ID_VIDEO_FORMAT=h264
ID_VIDEO_BITRATE=487608
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.3333
ID_AUDIO_FORMAT=28781
ID_AUDIO_BITRATE=127928
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=1323.95
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
ID_VIDEO_CODEC=ffh264
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
dec_audio: Allocating 4608 bytes for input buffer.
dec_audio: Allocating 49152 + 65536 = 114688 bytes for output buffer.
XXX initial  v_pts=0.000  a_pos=426 (0.027) 

AAC_PROBE: 4608 bytes

AAC_PROBE: ret 0
FAAD: Decoder init done (4608Bytes)!
FAAD: Negotiated samplerate: 48000Hz  channels: 2
FAAD: got 127kbit/s bitrate from MP4 header!
AUDIO: 48000 Hz, 2 ch, s16le, 127.9 kbit/8.33% (ratio: 15991->192000)
ID_AUDIO_BITRATE=127928
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
[libaf] Adding filter dummy 
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
AO: Description: Null audio output
AO: Author: Tobias Diedrich <ranma+mplayer@tdiedrich.de>
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
[dummy] Was reinitialized: 48000Hz/2ch/s16le
[dummy] Was reinitialized: 48000Hz/2ch/s16le
ID_AUDIO_CODEC=faad
Starting playback...

Uninit audio filters...
[libaf] Removing filter dummy 
Uninit audio: faad
FAAD: Closing decoder!
Uninit video: ffmpeg
vo: x11 uninit called but X11 not inited..

Exiting... (End of file)
mp4muxer>> /usr/bin/MP4Box -aviraw video /media/METTES GUF/Series/Dilbert/Dilbert.02x17.Ethics.en.Output.mp4_1240738081069temp.avi 
*** buffer overflow detected ***: /usr/bin/MP4Box terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f0d23d1e887]
/lib/libc.so.6[0x7f0d23d1c750]
/usr/bin/MP4Box[0x408a88]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f0d23c3d466]
/usr/bin/MP4Box[0x406949]
======= Memory map: ========
00400000-00424000 r-xp 00000000 08:01 1176212                            /usr/bin/MP4Box
00624000-00628000 r--p 00024000 08:01 1176212                            /usr/bin/MP4Box
00628000-00629000 rw-p 00028000 08:01 1176212                            /usr/bin/MP4Box
018fd000-0191e000 rw-p 018fd000 00:00 0                                  [heap]
7f0d22d8a000-7f0d22da0000 r-xp 00000000 08:01 873244                     /lib/libgcc_s.so.1
7f0d22da0000-7f0d22fa0000 ---p 00016000 08:01 873244                     /lib/libgcc_s.so.1
7f0d22fa0000-7f0d22fa1000 r--p 00016000 08:01 873244                     /lib/libgcc_s.so.1
7f0d22fa1000-7f0d22fa2000 rw-p 00017000 08:01 873244                     /lib/libgcc_s.so.1
7f0d22fa2000-7f0d22fa4000 r-xp 00000000 08:01 873251                     /lib/libdl-2.8.90.so
7f0d22fa4000-7f0d231a4000 ---p 00002000 08:01 873251                     /lib/libdl-2.8.90.so
7f0d231a4000-7f0d231a5000 r--p 00002000 08:01 873251                     /lib/libdl-2.8.90.so
7f0d231a5000-7f0d231a6000 rw-p 00003000 08:01 873251                     /lib/libdl-2.8.90.so
7f0d231a6000-7f0d231bd000 r-xp 00000000 08:01 873262                     /lib/libpthread-2.8.90.so
7f0d231bd000-7f0d233bc000 ---p 00017000 08:01 873262                     /lib/libpthread-2.8.90.so
7f0d233bc000-7f0d233bd000 r--p 00016000 08:01 873262                     /lib/libpthread-2.8.90.so
7f0d233bd000-7f0d233be000 rw-p 00017000 08:01 873262                     /lib/libpthread-2.8.90.so
7f0d233be000-7f0d233c2000 rw-p 7f0d233be000 00:00 0 
7f0d233c2000-7f0d23525000 r-xp 00000000 08:01 1173030                    /usr/lib/libcrypto.so.0.9.8
7f0d23525000-7f0d23724000 ---p 00163000 08:01 1173030                    /usr/lib/libcrypto.so.0.9.8
7f0d23724000-7f0d23731000 r--p 00162000 08:01 1173030                    /usr/lib/libcrypto.so.0.9.8
7f0d23731000-7f0d23747000 rw-p 0016f000 08:01 1173030                    /usr/lib/libcrypto.so.0.9.8
7f0d23747000-7f0d2374b000 rw-p 7f0d23747000 00:00 0 
7f0d2374b000-7f0d23794000 r-xp 00000000 08:01 1173035                    /usr/lib/libssl.so.0.9.8
7f0d23794000-7f0d23994000 ---p 00049000 08:01 1173035                    /usr/lib/libssl.so.0.9.8
7f0d23994000-7f0d23995000 r--p 00049000 08:01 1173035                    /usr/lib/libssl.so.0.9.8
7f0d23995000-7f0d2399a000 rw-p 0004a000 08:01 1173035                    /usr/lib/libssl.so.0.9.8
7f0d2399a000-7f0d23a1e000 r-xp 00000000 08:01 873252                     /lib/libm-2.8.90.so
7f0d23a1e000-7f0d23c1d000 ---p 00084000 08:01 873252                     /lib/libm-2.8.90.so
7f0d23c1d000-7f0d23c1e000 r--p 00083000 08:01 873252                     /lib/libm-2.8.90.so
7f0d23c1e000-7f0d23c1f000 rw-p 00084000 08:01 873252                     /lib/libm-2.8.90.so
7f0d23c1f000-7f0d23d88000 r-xp 00000000 08:01 873248                     /lib/libc-2.8.90.so
7f0d23d88000-7f0d23f87000 ---p 00169000 08:01 873248                     /lib/libc-2.8.90.so
7f0d23f87000-7f0d23f8b000 r--p 00168000 08:01 873248                     /lib/libc-2.8.90.so
7f0d23f8b000-7f0d23f8c000 rw-p 0016c000 08:01 873248                     /lib/libc-2.8.90.so
7f0d23f8c000-7f0d23f91000 rw-p 7f0d23f8c000 00:00 0 
7f0d23f91000-7f0d23fa8000 r-xp 00000000 08:01 1175282                    /usr/lib/libz.so.1.2.3.3
7f0d23fa8000-7f0d241a7000 ---p 00017000 08:01 1175282                    /usr/lib/libz.so.1.2.3.3
7f0d241a7000-7f0d241a9000 rw-p 00016000 08:01 1175282                    /usr/lib/libz.so.1.2.3.3
7f0d241a9000-7f0d24427000 r-xp 00000000 08:01 1176147                    /usr/lib/libgpac-0.4.4.so
7f0d24427000-7f0d24627000 ---p 0027e000 08:01 1176147                    /usr/lib/libgpac-0.4.4.so
7f0d24627000-7f0d24629000 r--p 0027e000 08:01 1176147                    /usr/lib/libgpac-0.4.4.so
7f0d24629000-7f0d24631net.homeip.entreprisesmd.mvconv.mplayerwrapper.MPlayerException: 
	at net.homeip.entreprisesmd.mvconv.mplayerwrapper.muxer.MP4EncodingJob.extractVideo(MP4EncodingJob.java:219)
	at net.homeip.entreprisesmd.mvconv.mplayerwrapper.muxer.MP4EncodingJob.start(MP4EncodingJob.java:433)
	at net.homeip.entreprisesmd.mvconv.core.job.ConvertJob.run(ConvertJob.java:161)
	at net.homeip.entreprisesmd.mvconv.core.job.JobQueue$1.run(JobQueue.java:92)
	at java.lang.Thread.run(Unknown Source)



```

thanks

---

### Post by ikus060 on 2009-04-26
Hi Ni85,

I didn't work for a while on MvPod as I have other project. I don't event know if it's work on Jaunty. One thing I notice is that you run MvPod with MP4Box. As version 0.1.~65, mvPod doesn't use MP4Box.

I suggest you to try it with the nightly build. Some how, it's more stable than alpha version !

Keep me inform how it work. On my side, I will do some testing on different platform to verify that MvPod still working.

Regards,

Patrik Dufresne

---

### Post by PiotrOz on 2009-05-26
FYI, I installed mvPod (nightly build) with mpeg4ip-server (and mplayer, mencoder,gpac, java) on Jaunty and it works great.

---

### Post by mlebaron on 2009-12-19
Just want to say "thank you" for MVPod.  It is exactly what I needed as a very simple solution for getting my DVDs converted to a size that is just right for iPod.

Thanks!

---

### Post by ikus060 on 2009-12-19
Great. I've not been working on this project for a while. During chrismas time I will try to get it more on the map. If you have any suggestion of features, general improvement, etc. you're welcome.

---

### Post by tatung on 2011-05-05
Hi ikus060,
I really like your app. I've downloaded your app from sourceforge and tried to convert a video file. The problem is that I can convert it with the custom profile (it's your default choice) but the H264 and Xdiv is not working. It shows the message something like 
```

Encoding conversion failed. 
Output file /media/Data/MyVideo(1280x720 h264).Output.mp4 not found 

```
Can you give me any clue to fix this!
Thanks

---

