---
title: "[SOLVED] Strange problem: No player can handle .ogg files"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by geo909 on 2008-02-08
Hello everybody.

I recorded a desktop session in ogg format. The video file is fine:
I played it with MPlayer (Storm Codec) in Windows XP through VirtualBox and a friend of mine was able to play it with Totem on his Ubuntu 7.10

 Well, I have tried with totem (tried both gstreamer and xine), VLC, MPlayer Movie Player and Kaffeine in my Ubuntu 7.10 and none of them can handle the file..:confused:

 Kaffeinne shows a blue screen while the file is played and the other players close immediatelly after I load the file. 

 Again, the specific file is playable in both WIndows' MPlayer  and Totem, so the problem is mine..

Any ideas.. Please?!

---

### Post by Metaljaz on 2008-02-08
Scroll to the bottom and see if it helps any. Let us know:

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by geo909 on 2008-02-08
> Scroll to the bottom and see if it helps any. Let us know:

[http://www.ubuntugeek.com/install-mp...sy-gibbon.html](http://www.ubuntugeek.com/install-mp...sy-gibbon.html)

Indeed, I didn't have the w32 codecs but no, that didn't work...:(
This is quite frustrating because I thought ogg files should be supported by defeault...
I must have done something, but I don't know what.. 

Any ideas?

---

### Post by geo909 on 2008-02-08
I have recorded a desktop session, where I try to open this ogg file with VLC and MPlayer,
In case you want to see what exactly I am talking about.

That's 384 KB so it will be downloaded fastly
(The irony: It's in ogg format!!)

Here it is:

[http://rapidshare.com/files/90287411/ogg_problem.ogg.html]("http://rapidshare.com/files/90287411/ogg_problem.ogg.html")

---

### Post by Metaljaz on 2008-02-08
So you can't see the website when you click on it or what happens? Do you get an error message or what?

---

### Post by gsmanners on 2008-02-09
I suggest you open a console and type:

mplayer -v VB.ogg

Then post what that outputs.

---

### Post by geo909 on 2008-02-09
> **Metaljaz said:**
> So you can't see the website when you click on it or what happens? Do you get an error message or what?

The website is fine. I followed all the steps and installed both libraries Actually, for the "libdvd-something" one, it was just an upgrade. AFterwards, I tried opening the ogg video with all my players and like before, a window appeared for half a second and the player shut down.


> I suggest you open a console and type:

mplayer -v VB.ogg

Then post what that outputs. 

OK,  like before mplayer flashed in my eyes for half a second and then closed. Here's the console output:

```
jorge@jorge-desktop:~/Desktop$ mplayer -v VB.ogg
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/jorge/.mplayer/codecs.conf'
Reading /home/jorge/.mplayer/codecs.conf: Can't open '/home/jorge/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' 'VB.ogg'
init_freetype
get_path('font/font.desc') -> '/home/jorge/.mplayer/font/font.desc'
font: can't open file: /home/jorge/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Using nanosleep() timing
get_path('input.conf') -> '/home/jorge/.mplayer/input.conf'
Can't open input config file /home/jorge/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 67 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('VB.ogg.conf') -> '/home/jorge/.mplayer/VB.ogg.conf'

Playing VB.ogg.
get_path('sub/') -> '/home/jorge/.mplayer/sub/'
[file] File size is 16063749 bytes
STREAM: [file] VB.ogg
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
==> Found video stream: 0
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
======= VIDEO Format ======
  biSize 40
  biWidth 1280
  biHeight 1024
  biPlanes 3
  biBitCount 24
  biCompression 1868916852='theo'
  biSizeImage 3932160
===========================
Ogg stream length (granulepos): 65267
Ogg demuxer : found 0 audio stream, 1 video stream and 0 text stream
Ogg file format detected.
VIDEO:  [theo]  1280x1024  24bpp  15.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:1280x1024  fps:15.00  ftime:=0.0667
get_path('sub/') -> '/home/jorge/.mplayer/sub/'
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
Disabling DPMS
DPMSDisable stat: 1
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x010203).
[xv common] Maximum source image dimensions: 1920x1088
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88a96d8]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
INFO: Theora video init ok!
VDec: vo config request - 1280 x 1024 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.25:1 - prescaling to correct movie aspect.
VO Config (1280x1024->1280x1024,flags=0,'MPlayer',0x32315659)
VO: [xv] 1280x1024 => 1280x1024 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x30323449 (I420) planar
Xvideo image format: 0x59565955 (UYVY) packed
using Xvideo port 73 for hw scaling
[xv] dx: 0 dy: 0 dw: 1200 dh: 1024
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
*** [vo] Exporting mp_image_t, 1280x1024x12bpp YUV planar, 1966080 bytes
get_path('subfont.ttf') -> '/home/jorge/.mplayer/subfont.ttf'
Unicode font: 255 glyphs.
[xv] dx: 0 dy: 0 dw: 1200 dh: 947
X11 error: BadAlloc (insufficient resources for operation)
Type: 0, display: 0x89d4e70, resourceid: 3400001, serial: 6e
Error code: b, request code: 8c, minor code: 13


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
Uninit video: theora
Successfully enabled DPMS
gnome_screensaver_control()vo: uninit ...
jorge@jorge-desktop:~/Desktop$ 


```

---

### Post by gsmanners on 2008-02-09
Looks like a bug in xv. You may have to switch to x11 or opengl for your -vo setting.

---

### Post by geo909 on 2008-02-09
> **gsmanners said:**
> Looks like a bug in xv. You may have to switch to x11 or opengl for your -vo setting.

 Hmmm..
I declare noob!
Could you possibly explain me what that means or what I should do practically?

---

### Post by geo909 on 2008-02-09
Any ideas?
Anyone?

---

### Post by geo909 on 2008-02-09
:(Bump:(

---

### Post by gsmanners on 2008-02-09
If you use mplayer from a console, then you would type:

mplayer -vo x11 video.avi

or

mplayer -vo gl video.avi

---

### Post by geo909 on 2008-02-10
> **gsmanners said:**
> If you use mplayer from a console, then you would type:

mplayer -vo x11 video.avi

or

mplayer -vo gl video.avi

 Yes!  When I use the first command, my video file does play (jn full screen mode) and when I use the second command, it plays again in a window.

 So, that confirms that the video is OK and there must be some kind of problem with my settings (?).

 Anyway, do you know what should I do to make my .ogg files playable from my non-console players? Any additional info needed?

---

### Post by gsmanners on 2008-02-10
With GUI players, usually there is some option or advanced option in their Preferences for whatever Video Output module you wish to use. That would be how you would set that.

---

### Post by geo909 on 2008-02-10
And what video output module should I set in my case?

---

### Post by gsmanners on 2008-02-10
You should always try xv (or XVideo) first. If that doesn't work, then try x11, then gl or openGL.

---

### Post by eye208 on 2008-02-10
> **gsmanners said:**
> You should always try xv (or XVideo) first. If that doesn't work, then try x11, then gl or openGL.
No. XVideo first, then OpenGL, then X11.

Why? Because X11 always works but looks blocky when scaled. OpenGL is much better.

---

### Post by geo909 on 2008-02-10
Thank you both, guys!!

X11 did the job.
xv didn't and openGL's full screen mode wasn't that "full".
Though, when the video start playing, I get a message:
 " Codec not found" 
but I just click 'OK'the window close and I'm fine.

Just for curiosity reasons, do you know why I get this message?


 Thank sooo much again!

---

### Post by andrew.46 on 2008-02-11
Hi,

 Well I can play this quite successfully using mplayer:

```
andrew@ilium~/Desktop$ mplayer ogg_problem.ogg 
MPlayer dev-SVN-r25950-4.1.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing ogg_problem.ogg.
[Ogg] stream 0: video (Theora v3.2.0), -vid 0
Ogg file format detected.
VIDEO:  [theo]  1280x1024  24bpp  10.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x889b630]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 1280 x 1024 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 1280x1024 => 1366x1024 Planar YV12 
[ASPECT] Warning: No suitable new res found!
[ASPECT] Warning: No suitable new res found!
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
Audio: no sound
Starting playback...
V:  13.0 131/131  7%  1%  0.0% 0 0 

Exiting... (End of file)
andrew@ilium~/Desktop$ 

```

But I can see that you are using a fairly old copy of mplayer. Have you thought of upgrading a little:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

I see from previous posts that you have sorted out the video display problem, you can always put your most succesful -vo as a default in ~/.mplayer/config.

                Andrew

---

### Post by geo909 on 2008-02-11
Thanks, I'll try this out.
Though, I'm a bit scared  with all this manual work, but I'll try!

---

