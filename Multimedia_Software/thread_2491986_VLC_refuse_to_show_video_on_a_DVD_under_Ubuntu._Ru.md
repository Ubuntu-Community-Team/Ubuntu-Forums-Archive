---
title: "VLC refuse to show video on a DVD under Ubuntu. Runs fine on Windows on same hardware"
date: 2023-10-27
forum: Multimedia Software
---

### Post by georgesgiralt on 2023-10-27
Hello Guys
Yesterday, I was trying to play The Interpreter from Sydney Pollack. It is a region 02 DVD (I live in France) on my 22.04.3 LTS fully up to date Ubuntu laptop.
VLC showed the DVD menu and when I hit "film", stayed with the menu displayed on the screen but the sound of the movie played on. 
See the log :
```

$ vlc
VLC media player 3.0.16 Vetinari (revision 3.0.13-8-g41878ff4f2)
[00005619cd674580] main libvlc: Lancement de vlc avec l'interface par défaut. Utiliser «*cvlc*» pour démarrer VLC sans interface.
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
[00005619cd715d50] main playlist: playlist is empty
[00007fde60001130] dvdnav demux: DVD Title: INTERPRETE
[00007fde60001130] dvdnav demux: DVD Serial Number: c70b19ce      
[00007fde60001130] dvdnav demux: DVD Title (Alternative): INTERPRETE
[00007fde60001130] dvdnav demux: DVD disk reports itself with Region mask 0x00fd0000. Regions: 02
[00007fde60001130] dvdnav demux: Attempting to retrieve all CSS keys
[00007fde60001130] dvdnav demux: This can take a _long_ time, please be patient
[00005619cd7501d0] main audio output error: too low audio sample frequency (0)
[00007fde601af3e0] main decoder error: failed to create audio output
[00005619cd7501d0] vlcpulse audio output error: digital pass-through stream connection failure: Non pris en charge
[00005619cd7501d0] main audio output error: module not functional
[00007fde601af3e0] main decoder error: failed to create audio output
[00007fde4c003e70] gl gl: Initialized libplacebo v4.192.1 (API v192)
libva info: VA-API version 1.14.0
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)
[00007fde4c003e70] glconv_vaapi_x11 gl error: vaInitialize: unknown libva error
libva info: VA-API version 1.14.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_14
libva info: va_openDriver() returns 0
[00007fde6006e530] avcodec decoder: Using Intel iHD driver for Intel(R) Gen Graphics - 22.3.1 () for hardware decoding
[00007fde4c1c97e0] vaapi_filters filter error: vaCreateContext: unknown libva error
[00007fde600560f0] avcodec decoder: Using Intel iHD driver for Intel(R) Gen Graphics - 22.3.1 () for hardware decoding
[00007fde4c1c97e0] vaapi_filters filter error: vaCreateContext: unknown libva error
[00005619cd7501d0] main audio output error: too low audio sample frequency (0)
[00007fde6006e530] main decoder error: failed to create audio output
[00005619cd7501d0] main audio output error: too low audio sample frequency (0)
[00007fde6006e530] main decoder error: failed to create audio output
[00005619cd7501d0] vlcpulse audio output error: digital pass-through stream connection failure: Non pris en charge
[00005619cd7501d0] main audio output error: module not functional
[00007fde6006e530] main decoder error: failed to create audio output
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[00007fde600560f0] main decoder error: buffer deadlock prevented
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] Failed to end picture decode after error: 18 (invalid parameter).
[mpeg2video @ 0x7fde54002840] hardware accelerator failed to decode first field
[mpeg2video @ 0x7fde54002840] Failed to upload decode parameters: 18 (invalid parameter).
.........
QObject::~QObject: Timers cannot be stopped from another thread
g:~$

```
It is strange as mplayer plays it flawlessly : 
```
$ mplayer dvd://1 -dvd-device  /dev/sr0
MPlayer 1.4 (Debian), built with gcc-11 (C) 2000-2019 MPlayer Team
do_connect: could not connect to socket
connect: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 9 titles on this DVD.
There are 1 angles in this DVD title.
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000142
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00007639
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001e6e1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0031b332
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0031fd0d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003aefdd
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003aefe2
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0
audio stream: 0 format: ac3 (stereo) language: fr aid: 128.
audio stream: 1 format: ac3 (5.1) language: fr aid: 129.
audio stream: 2 format: ac3 (5.1) language: en aid: 130.
audio stream: 3 format: ac3 (stereo) language: en aid: 131.
audio stream: 4 format: ac3 (stereo) language: fr aid: 132.
number of audio channels on disk: 5.
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 3 language: fr
subtitle ( sid ): 5 language: fr
number of subtitles on disk: 3

MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  5000.0 kbps (625.0 kbyte/s)
X11 error: BadMatch (invalid parameter attributes)
GPU at BusId 0x2c doesn't have a supported video decoder
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 58.134.100 (external)
[mpeg2video @ 0x7f06185db380]Requested frame threading with a custom get_buffer2() implementation which is not marked as thread safe. This is not supported anymore, make your callback thread-safe.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, floatle, 320.0 kbit/10.42% (ratio: 40000->384000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
Starting playback...
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
[mpeg2video @ 0x7f06185db380]ac-tex damaged at 15 32
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
A: 214.3 V: 214.3 A-V:  0.000 ct:  0.032 5358/10716  4%  1%  0.8% 0 0 

Exiting... (Quit)

```
As I do not like mplayer (I have trouble remembering the keyboard commands), I switched to Windows and ran vlc to play this same DVD flawlessly on the very same hardware. 
In the logs I've seen that there has been ffmpeg and libavcodec58 libavdevice58 libavutil56 libavformat58 libavfilter7 libraries updates recently.  
I could not say this update broke something nor if the previous versions of these libraries were able to play this DVD or if mplayer use these or not.
I would be delighted to have help from you to solve this issue. 
Many thanks in advance for your help.

---

### Post by Holger_Gehrke on 2023-10-27
Those errors from vlc look like there's something wrong with hardware decoding. You might want to try again using a different decoding method; should be found in the settings under 'Tools'->'Preferences'->'Video'->'Output'.

Holger

---

### Post by georgesgiralt on 2023-10-27
Well, both settings are set to "Automatic". And I do not know what to set/try. 
Add to this that this DVD is the only one behaving like that. And I've tried another one and it work fine and flawlessly....
I'm puzzled.

---

### Post by qyot27 on 2023-10-27
Use mpv, not mplayer.  SMPlayer can provide the GUI if you want.

---

### Post by georgesgiralt on 2023-10-27
Hello,
I spend some time setting one video output method after another until I found one providing proper visualisation of this movie.
Some settings gave a flickering rectangular panels in the window of VLC, other painted the whole window red and nothing else. 
Finally, using "Xvideo (XCB)" did the trick. I did not go further and test other settings to see if they work. 
But, I thought all DVD shared the same video format, mpeg something. So how come this particular one needs a specialised setting to be displayed ? And last but not least, why the Windows VLC version does not need to be set other than "automatic" ? 
Anyway, thanks for your help and the smplayer app, I did not know about !

---

### Post by qyot27 on 2023-10-27
> **georgesgiralt said:**
> But, I thought all DVD shared the same video format, mpeg something. So how come this particular one needs a specialised setting to be displayed ?
All DVDs use MPEG-2 video, correct.  But there might be streams that aren't 100% compliant (not usually a problem for commercial discs) or the stream might be compliant but the OS' driver to enable hardware decoding on the GPU might be problematic and certain streams (compliant or not) are able to trip them up and throw the error.  Disabling hardware decoding would therefore avoid the issue entirely (why mplayer worked and VLC didn't).  My guess is that "Xvideo (XCB)" doesn't enable hardware decoding and just uses software.  Or maybe it's a case where you need to install the nonfree Intel driver, the way I need to do if I want AV1 hardware decoding.

> And last but not least, why the Windows VLC version does not need to be set other than "automatic" ?
Windows' drivers are completely different and VLC may have no issue enabling hardware acceleration under DirectX.  Or as above, it's just disabling hardware decoding and using a software decoder.  MPEG-2 is not a hardware intensive format on any even somewhat remotely modern computer, especially not at DVD resolution.  Even a Raspberry Pi could probably play 1080p MPEG-2 (like from a broadcast capture) in software and not break a sweat.

---

### Post by georgesgiralt on 2023-10-27
> 
Or maybe it's a case where you need to install the nonfree Intel driver,
I would like to do that, but how ? But I wonder if it will be useful as VLC experienced the same misbehaviour using the NVidia driver (my laptop has an Optimus NVidia card)...

---

### Post by qyot27 on 2023-10-27
How old is this laptop?  Because the nonfree Intel driver is only for Gen 8 (Coffee Lake) and higher CPUs.  So anything older than late 2017 wouldn't be able to use it.

Regardless, the particular option for hardware decoding in VLC is detailed here:
[https://wiki.videolan.org/VLC_HowTo/Hardware_acceleration/](https://wiki.videolan.org/VLC_HowTo/Hardware_acceleration/)

---

### Post by georgesgiralt on 2023-10-28
Hello,
3 years old ? the CPU is "11th Gen Intel(R) Core(TM) i5-1135G7 @ 2.40GHz".... So eligible to a proprietary driver ...
I'll have a look at the Videolan Wiki. Thank you.

---

