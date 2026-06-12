---
title: "mplayer video extra wide on xgl"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by precinto on 2007-04-22
Since I upgraded to Feisty everytime I open a video with mplayer the video window appears hugely long, largely traspassing the limit of my worskspace and without the window frame. When I resize it the windows frame appears, but activating fullscreen video gets me an unproportioned fullscreen where you can't see anything.

I had to downgrade beryl to beryl 2.0 because the ubuntu version is incompatible with Xgl (so they say).

Anyone?

Thanks.

---

### Post by SpanishFranks on 2007-04-23
I hate to add a 'me too' post, but me too.

 precinto, if you change the mplayer video driver to x11what happens? Can you get fullscreen or enlarge the video size? My video remains the same size, even in fullscreen.

---

### Post by precinto on 2007-04-23
The mplayer driver is set to xv. I've however tried with other options to no avail.

Not being able to set the fullscreen with mplayer (or having a black fullscreen with a small video) is another different problem, I think. And the solution is somewhere on this forums (I had that problem on... Dapper, I guess).

---

### Post by biochip2k on 2007-04-24
Hi,
I have the same behavior that you guys with playing videos with mplayer and xgl, but it seem that is only with gmplayer (the gui frondend of mplayer).

if I play the video file from terminal as $ mplayer [videofile], the aspect ration is correct and all see normal as before with edgy even fullscreen.

I had make a nautilus script just as a workaround.
```

#!/bin/sh
mplayer $@

```
and save the file as mplayer in [home]/.gnome2/nautilus-scripts, chmod to execute the file and reload the folder in nautilus.

then just right click on the file a select on popmenu scripts>mplayer

---

### Post by precinto on 2007-04-26
You're right, starting mplayer from the terminal works ok (although all options must be set manually). 

This is the error I get when I start gmplayer from a terminal and select fullscreen (then mplayer exits, it doesn't even go on unproportioned fullscreen):

```
gmplayer
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".

Playing /media/cdrom0/NewLaar.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  12bpp  23,976 fps  994,7 kbps (121,4 kbyte/s)
Clip info:
 Software: VirtualDub
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128,0 kbit/8,33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1,77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
[ws] Error in display.  0,008 ct: -0,008  38/ 38  8%  4% 12,6% 2 0                      
[ws]  Error code: 2 ( BadValue (integer parameter out of range for operation) )
[ws]  Request code: 137
[ws]  Minor code: 19
[ws]  Modules: flip_page

```

---

### Post by biochip2k on 2007-05-03
Ok. This it is my second attempt for normal use of mplayer under xgl with ati restricted driver.

Select X11 Driver in >preferences>Video>X11 X11 ( XImage/Shm )
and exit from mplayer or edit the following line in ~/.mplayer/gui.conf

```
vo_driver = "x11"
```

with this you can see in normal size windows, for full screen you need to edit ~/.mplayer/config and add the following line

```
zoom=yes
```

looks like it almost work BUT it also need to be mark the Enable frame dropping in >preferences>Video since it get to lost sync with A/V in fullscreen.

Regards

---

### Post by hotani on 2007-05-06
Mine is not going past the screen or anything, but the aspect ratio is too wide. If i change mplayer to "4:3" (I have a widescreen monitor, go figure), then it is perfect. After I close it, the setting is gone. So in order to watch anything via the gui player, I would have to open it, then change the setting to 4:3. 

Oh, and VLC has broken sound, and Totem freezes the system when I use the keyboard or remote volume. Good, good times.

---

### Post by biochip2k on 2007-05-09
Hi hotami, I also use a widescreen monitor,

to use the correct aspect ratio in your widescreen monitor just add the following line to ~/.mplayer/config file
ej. gedit .mplayer/config
```
monitoraspect="16:10"
```

Then you don' t need to select 4:3 each time you start mplayer.

also has a extra tip
```
fontconfig = yes
font = "Arial Unicode MS"
```
add good size and quality font to subtitle.

regards

---

### Post by getaceres on 2007-05-12
It's the same for me. Totem and VLC works well but VLC sometimes has artifacts and they don't have a good support for WMV as MPlayer has. It's a shame but ATI has lost a customer. I bought a Radeon 9000, then a 9700, recently I bought a laptop and the first thing I did was to discard all the ones that had an ATI card. Now I'm a happy NVidia user in my laptop but still my desktop suffers this kind of things. All I can say for anyone:

DON'T BUY AMD/ATI CARDS IF YOU WANT TO USE LINUX.

---

### Post by GrejpFrut on 2007-05-16
I am also having this issue with mplayer.  If I use X11 for the video drivers, the video plays very choppy.  Also if I go into fullscreen with X11, the video does not go fullscreen, but there it is surrounded by black borders on all sides.  With the xv video drivers I get much better performance, but like others have said, the video will be extremely wide.  And when going into fullscreen the video is unwatchable due to how much it is stretched.  

I also have the same error output as precinto does.  

My belief is that this is happening because of how the workspace is being used in beryl.  If you have noticed, when you put something on any other side of the cube, it shows up on the workspace viewer that it is on that specific side.  This did not work for awhile in beryl.  The cube would only use one workspace and it would be updated depending on which side of the cube you were on.  So I believe mplayer is trying to strech across all the side of the cube.  

I really hope we are able to find a solution because it would be a huge pain if videos can not be played properly just because of beryl.

---

### Post by GrejpFrut on 2007-05-17
Well I have found a way around this.  I decided to log into my Gnome session instead of the XGL session.  While in my Gnome session, I can use the xv video drivers to play videos.  This resulted in similar performance to what I had in Edgy.

However, Beryl seems a bit sluggish now.  Minimizing and maximizing windows freezes a bit at the end of the animation.  Is this due to being in the Gnome session?  Also what is the reason for the mplayer error not happening in the Gnome session even though I can run Beryl?

---

### Post by biochip2k on 2007-05-24
Hi GrepjpFrut,

I use X11 output in mplayer and find ok the video playback also in fullscreen with resolution of 1920x1200 @ 24-bits. I may think probably in the video driver, I use the last one from AMD/ATI home page instead of the ones that come in the repositories (ver. 8.36.5)

beryl nether is from the repositories.

Regards

---

### Post by GrejpFrut on 2007-05-24
biochip2k:

Thanks for the information.  I am also running at that resolution and bit depth.  I used the video drivers from nvidia's website which are still the most recent drivers.  I did, however, install beryl from repository and followed this guide:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

In that guide it says to force to version 2.0 for beryl-core.  I will try and find some time to try the newest version of beryl from svn and see what happens from there.  Thanks for the reply bioship2k.

---

### Post by biochip2k on 2007-05-25
Hi GrejpFrut,

I see that you have a Nvidia graphic card, all ATI user know that Nvidia have better driver support in Linux that ATI (and that I would like to have one instead of my card that come _integrated_ with my pc).

Thats why all ATI user have to install XGL so we can enable beryl eye candy. But with Nvidia (wherever I know) it is not necessary since it work with a better composite manager that is AIGLX and comes included with the X server of Feisty.

I may suggest remove the XGL server
```
sudo apt-get remove xserver-xgl
```
and follow this [how to ubutnu-nvidia-beryl]("http://ubuntu-tutorials.com/2007/02/06/install-beryl-on-ubuntu-feisty-with-aiglx-for-nvidia-ubuntu-704/")

I installed beryl in my old (but good) laptop PIII @ 256 ram! with an INTEL graphic card and like Nvidia, intel drivers support AIGLX and I can watch videos with no problems with mplayer.

good luck

---

