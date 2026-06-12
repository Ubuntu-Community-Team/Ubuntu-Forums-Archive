---
title: "HD Video Stuttering After 11.10 Upgrade"
date: 2011-10-23
forum: Mythbuntu
---

### Post by wjanik on 2011-10-23
After upgrading both my Mythbuntu backend and front-end from 11.04 to 11.10, I'm having trouble with HD video playback in MythTV.  Prior to the upgrade it was perfectly smooth, but now it stutters every 5 seconds or so.

I'm running an nVidia ION on the front-end, and a quick look at top shows the box largely idle (CPU-wise) with little-to-no IO wait.  I'm pretty sure the problem lies in the front-end because I have another front-end running the same hardware that I didn't upgrade and it works great.  A quick look at nvidia-settings, xorg.conf, and the MythTV playback settings shows nothing really different config-wise.

Anyone else having similar problems?  Googling only seemed to turn up older config issues worked through prior to the upgrade that don't seem to apply.

---

### Post by wjanik on 2011-10-24
A little more info...  I pulled the following from the mythfrontend.log file presumably pointing to the problem:

```
'video_output' mean = '36364.65', std. dev. = '6451.07', fps = '27.50'
'video_output' mean = '33364.57', std. dev. = '213.43', fps = '29.97'
2011-10-24 20:49:35.342 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.342 AO: Pause 1
2011-10-24 20:49:35.347 AO: Pause 0
2011-10-24 20:49:35.349 AO: OutputAudioLoop: Play Event
2011-10-24 20:49:35.381 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.382 AO: Pause 1
2011-10-24 20:49:35.387 AO: Pause 0
2011-10-24 20:49:35.390 AO: OutputAudioLoop: Play Event
2011-10-24 20:49:35.487 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.487 AO: Pause 1
2011-10-24 20:49:35.491 AO: OutputAudioLoop: audio paused
2011-10-24 20:49:35.497 AO: Pause 0
2011-10-24 20:49:35.531 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.531 AO: Pause 1
2011-10-24 20:49:35.536 AO: Pause 0
2011-10-24 20:49:35.586 Player(1): Video is 3.45178 frames ahead of audio,
			doubling video frame interval to slow down.
2011-10-24 20:49:35.619 AO: OutputAudioLoop: Play Event
2011-10-24 20:49:35.637 Player(1): Video is 5.82566 frames ahead of audio,
			doubling video frame interval to slow down.
...
2011-10-24 20:49:36.787 Player(1): Video is 3.08994 frames ahead of audio,
			doubling video frame interval to slow down.
```

What I don't understand is whether this is an audio or a video problem.  The messages above indicate the video is ahead of the audio, but prior to that it appears to be waiting for video.

---

### Post by nickrout on 2011-10-25
> **wjanik said:**
> A little more info...  I pulled the following from the mythfrontend.log file presumably pointing to the problem:

```
'video_output' mean = '36364.65', std. dev. = '6451.07', fps = '27.50'
'video_output' mean = '33364.57', std. dev. = '213.43', fps = '29.97'
2011-10-24 20:49:35.342 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.342 AO: Pause 1
2011-10-24 20:49:35.347 AO: Pause 0
2011-10-24 20:49:35.349 AO: OutputAudioLoop: Play Event
2011-10-24 20:49:35.381 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.382 AO: Pause 1
2011-10-24 20:49:35.387 AO: Pause 0
2011-10-24 20:49:35.390 AO: OutputAudioLoop: Play Event
2011-10-24 20:49:35.487 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.487 AO: Pause 1
2011-10-24 20:49:35.491 AO: OutputAudioLoop: audio paused
2011-10-24 20:49:35.497 AO: Pause 0
2011-10-24 20:49:35.531 Player(1): Waiting for video buffers...
2011-10-24 20:49:35.531 AO: Pause 1
2011-10-24 20:49:35.536 AO: Pause 0
2011-10-24 20:49:35.586 Player(1): Video is 3.45178 frames ahead of audio,
			doubling video frame interval to slow down.
2011-10-24 20:49:35.619 AO: OutputAudioLoop: Play Event
2011-10-24 20:49:35.637 Player(1): Video is 5.82566 frames ahead of audio,
			doubling video frame interval to slow down.
...
2011-10-24 20:49:36.787 Player(1): Video is 3.08994 frames ahead of audio,
			doubling video frame interval to slow down.
```

What I don't understand is whether this is an audio or a video problem.  The messages above indicate the video is ahead of the audio, but prior to that it appears to be waiting for video.

What video card are you using?
What playback profile are you using?

---

### Post by wjanik on 2011-10-25
> **nickrout said:**
> What video card are you using?
What playback profile are you using?

It's an nVidia ION, which I believe roughly translates to a 9400M.  The CPU is the Atom 230.

I've got a custom playback profile that uses VDPAU with no deinterlacing.  When I use the 'Slim' profile, I get similar results.  When I use the higher quality VDPAU profiles, I get these additional messages that don't show up in 'Slim' or my 'No Deinterlacing' profiles:
```
Player(3): Video is 3.52332 frames behind audio (too slow), dropping frame to catch up.
AO: Pause 1
```

Maybe this is indicating an audio problem?

---

### Post by Gremlyn1 on 2011-11-03
I am experiencing this exact same issue with a Pentium G860 Sandy Bridge HTPC on 11.10 (fresh install). Seems like my HD playback is dropping frames from the live video feed. I can play HD movies and other downloaded content just fine, so it has to be a specific setting. I have the problem with the live video whether I am in MythTV or running in VLC.

---

### Post by rulet on 2011-11-03
I have this problem with video playback on usual ubuntu 11.10 installation with vlc, mplayer and totem. Setting compiz-config doesn't help as on the previuose versions of ubuntu.
There is no solution for this issue at this time.
Nvidia GF9500 GT.

---

### Post by wjanik on 2011-11-03
I did try a few other things to try to isolate the problem.  I was able to downgrade MythTV to the latest version packaged for Mythbuntu 11.04, but it didn't solve the problem.  I tried to downgrade the nVidia driver but ran into problems so I wasn't able to actually test that.

Next, I performed a clean Mythbuntu 11.10 install to try to take upgrade or configuration issues off the table.  This didn't fix the problem either.  I tried downgrading MythTV again, but still no joy.

Finally, I did a clean Mythbuntu 11.04 install and made sure every package was as up-to-date as the "standard" repos offer.  That fixed it right up.

Note that my back-end is still running Mythbuntu 11.10, but I needed to downgrade the front-end to 11.04 to get things working.  Given my experiments with downgrading MythTV, I'm guessing the problem (for me at least) is not MythTV but rather something else packaged in 11.10.  Maybe the video driver or some Xorg update?

---

### Post by Gremlyn1 on 2011-11-03
There have been some other video issues in 11.10 as well, one I ran into involved libmpeg2 and purple lines over the video. Unfortunately I can't downgrade the system to 11.04 because I am running a Sandy Bridge processor and need the hardware acceleration support that 11.10 provides. It has to be something to do the specific decoding used for the stream since playing other video files are just fine.

Since it seems the issue occurs in VLC too, I might be able to try some different things to narrow down the problem?

---

### Post by nickrout on 2011-11-04
> **Gremlyn1 said:**
> I am experiencing this exact same issue with a Pentium G860 Sandy Bridge HTPC on 11.10 (fresh install). Seems like my HD playback is dropping frames from the live video feed. I can play HD movies and other downloaded content just fine, so it has to be a specific setting. I have the problem with the live video whether I am in MythTV or running in VLC.

Log files?

---

### Post by nickrout on 2011-11-04
> **rulet said:**
> I have this problem with video playback on usual ubuntu 11.10 installation with vlc, mplayer and totem. Setting compiz-config doesn't help as on the previuose versions of ubuntu.
There is no solution for this issue at this time.
Nvidia GF9500 GT.

Log files?

---

### Post by rulet on 2011-11-04
What log files?

 ... Well, I don't know which logs you were talking about, but here is example of output when playing one of the videos which stutters in vlc and mplayer(this is in Unity3D):
> 
 r@ngf:~$ vlc 2.mkv
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x826392c] main libvlc: &#1047;&#1072;&#1087;&#1091;&#1089;&#1082; vlc &#1089; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1086;&#1084; &#1087;&#1086; &#1091;&#1084;&#1086;&#1083;&#1095;&#1072;&#1085;&#1080;&#1102;. &#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1081;&#1090;&#1077; 'cvlc' &#1076;&#1083;&#1103; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1072; vlc &#1073;&#1077;&#1079; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1072;.
Blocked: call to setlocale(6, "")
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Blocked: call to setlocale(6, "")

(process:3903): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(vlc:3903): Gtk-WARNING **: &#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084;&#1099;&#1081; &#1084;&#1086;&#1076;&#1091;&#1083;&#1100; &#1090;&#1077;&#1084; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085; &#1074; module_path: «pixmap»,

(vlc:3903): Gtk-WARNING **: &#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084;&#1099;&#1081; &#1084;&#1086;&#1076;&#1091;&#1083;&#1100; &#1090;&#1077;&#1084; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085; &#1074; module_path: «pixmap»,

(vlc:3903): Gtk-WARNING **: &#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084;&#1099;&#1081; &#1084;&#1086;&#1076;&#1091;&#1083;&#1100; &#1090;&#1077;&#1084; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085; &#1074; module_path: «pixmap»,

(vlc:3903): Gtk-WARNING **: &#1047;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1084;&#1099;&#1081; &#1084;&#1086;&#1076;&#1091;&#1083;&#1100; &#1090;&#1077;&#1084; &#1085;&#1077; &#1085;&#1072;&#1081;&#1076;&#1077;&#1085; &#1074; module_path: «pixmap»,
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
xdg-screensaver: Window 0x036001d6 does not exist
r@ngf:~$

 
> r@ngf:~$ mplayer 2.mkv
mplayer: Symbol `ff_codec_bmp_tags' has different size in shared object, consider re-linking
MPlayer SVN-r33713-4.6.1 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2.mkv.
libavformat file format detected.
[matroska,webm @ 0x8d09080] max_analyze_duration reached
[matroska,webm @ 0x8d09080] Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: video (h264), -vid 0, Planeta.Zemlya.(02.chast.iz.11).Goru.2006.x264.HDDVDRip.(720p)
[lavf] stream 1: audio (ac3), -aid 0, -alang rus, &#1072;&#1074;&#1090;&#1086;&#1088;&#1089;&#1082;&#1080;&#1081; (&#1053;&#1080;&#1082;&#1086;&#1083;&#1072;&#1081; &#1044;&#1088;&#1086;&#1079;&#1076;&#1086;&#1074;)
VIDEO:  [H264]  1280x720  0bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Load subtitles in ./
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 6 ch, s16le, 384.0 kbit/8.33% (ratio: 48000->576000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 6ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x720 => 1280x720 H.264 VDPAU acceleration  [fs]
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:  33.1 V:  33.1 A-V: -0.000 ct:  0.042   0/  0  0%  0%  0.7% 2 0 

Exiting... (Quit)
r@ngf:~$

---

### Post by Gremlyn1 on 2011-11-04
> **nickrout said:**
> Log files?

I didn't include any yet from MythTV as I am farly confident I will see the same that wjanik did, though I will verify this later. I assume I can get some output log from VLC as well, so I will see what comes of that and post up when I have it.

---

### Post by BicyclerBoy on 2011-11-04
If you are using ubuntu 11.10, you are stuck with compiz composite unity desktop.

Composite, Xorg & nVidia don't work well together.

VDPAU playback is internally sync to the actual refresh rate of that current video mode.
The composite manager redirects each rendered frame to add its effects; this timing seems to not work correctly.

You can try running:
ccsm
select composite tab: tick undirect full screen
select opengl tab: try changing the refresh rate detect to/from detect.
select workarounds tab: tick legacy full screen

Be very careful with any settings in ccsm; Unity is incomplete..Learn how to reset from terminal.

Mythbuntu 11.10 is still built using Xfce ?
This probably uses mutter/clutter branch of metacity

There must be a config program for mutter/metacity..
It is possible that composite is at fault here as well.

Or you can (for nVidia) disable composite in /etc/X11/xorg.conf.

---

### Post by rulet on 2011-11-04
Changes in ccsm doesn't help anymore.

---

### Post by Gremlyn1 on 2011-11-15
I had to table this issue for a bit, but am backing looking today. I don't see the same error as wjank, at least not in the mythfrontend.log. I ran a session, fired up Watch TV, and copied the log over to pastebin: [http://pastebin.com/62m5T2rw](http://pastebin.com/62m5T2rw)

Couple of weird things in there, like starting at line 40:
```

2011-11-15 15:16:05.346 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-11-15 15:16:05.365
2011-11-15 15:16:05.346 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-11-15 15:16:05.365


unsupported attribute
 
 
2011-11-15 15:16:05.365
 
 
unsupported attribute

```

No idea what it means, and I haven't find much useful information on the error through Google yet.

Here is m hard info report if you're curious about any system specs: [http://dl.dropbox.com/u/1628974/hardinfo_report.html](http://dl.dropbox.com/u/1628974/hardinfo_report.html)

---

### Post by Gremlyn1 on 2011-11-15
OK, some new info: I recorded a TV show, tried to watch it in MythTV and had the same result as the live stream. I then tried to watch the file in VLC and it looked exactly the same there as well.

I have zero problems with playback of .mkv, .avi, .wmv, and .mp4 files, so could it be related to the .mpg? It would be interesting to find a .mpg file recorded on a different computer and see if I get the same playback problems. I might try converting one of my existing files over to .mpg (I assume HandBrake can do that).

Update: I just checked the video stream played directly in VLC, and it is much cleaner. There is still a very slight stuttering, but it is at least watchable, unlike the stream in MythTV. I played around with the options and nothing seemed to make it better nor worse in VLC.

---

### Post by Slate8 on 2011-11-18
Have you tried disabling compositing in your xorg.conf? I have to do this on my ION based setup to stop tearing and other graphical weirdness. I am not running 11.10 but 10.10 however. Still, may be worth a try.

To do this I usually get nvidia-settings to create an xorg.conf file for me. Then edit it and add the following to the end:

```

Section "Extensions"
    Option         "Composite" "Disabled"
EndSection

```

---

### Post by Gremlyn1 on 2011-11-18
> **Slate8 said:**
> Have you tried disabling compositing in your xorg.conf? I have to do this on my ION based setup to stop tearing and other graphical weirdness. I am not running 11.10 but 10.10 however. Still, may be worth a try.

To do this I usually get nvidia-settings to create an xorg.conf file for me. Then edit it and add the following to the end:

```

Section "Extensions"
    Option         "Composite" "Disabled"
EndSection

```

Well I wasn't running an nVidia card before, just the integrated graphics of my CPU. Since I hadn't gotten any response here or the other forums I was seeking help on, I decided to go buy myself a reasonably priced video card. I ended up with a Zotac GT520 1GB card. After applying all the nVidia fixes, everything is working as I would have hoped. 

My suggestion to anyone having problems with the integrated graphics of the Sandy Bridge processors is to just drop the $30 and get a proper graphics card!

---

### Post by nickrout on 2011-11-19
Sandybridge is not fully supported on linux.

Speak to the manufacturer, the only reason hardware doesn't work on linux is if the manufacturer is tight assed with their documentation.

---

