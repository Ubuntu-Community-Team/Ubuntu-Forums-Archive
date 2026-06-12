---
title: "No video playing any format of movie"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by Pizzaburgers on 2007-03-12
Hi,

I cannot get video on any format of movie that I try to play except for .mpg.  For all other formats (.avi, .wmv, .flv, etc.)   I get audio, but no video.  I've tried every player / codec I could find on the web.  VLC, Mplayer, Totem, Xine, w32-all, gstreamer plugins, and whatever else I could install, but nothing seems to work.  I think I've gone and uninstalled everything except for VLC and Totem, but to be honest since I'm a linux newbie I'm not really sure.

I'm running on an IBM T30 laptop with 512MB of ram and  Radeon Mobility M7 LW [Radeon 7500] video driver (auto-detected by Ubuntu).  For some reason I have it in my head that the T30's use an Intel video card, I'm gonna have to check on that...

Not sure what else to try... Whats really odd is that I get the first frame of the movie on the icon, so I'm pretty sure Ubuntu knows how to decode it somehow...

Thanks in advance for any assistance you can provide.

-Pizzaburgers

---

### Post by panch0 on 2007-03-13
Since you say you can play mpegs there's probably no video output problem. Install MPlayer and libavcodec + libavformat and run from the console:

mplayer movie.avi

If it doesn't work, post the output you get from MPlayer.

---

### Post by kroiz on 2007-03-13
I got the same problem. I posted about a week ago. no solution yet :(
BTW I too have a IBM laptop, T41.
only I did not try any mpg I tried some mpeg but it does not play either.

---

### Post by Pizzaburgers on 2007-03-13
Ok, so I installed Mplayer and the gstreamer ffmpeg codecs which should have the libavcodec (I think(?) Remember I'm a newbie).  If not, then I don't know how to install the libav stuff and searching online wasn't all that helpful either.

Below is the output from mplayer.  It looks like its picking the right audio and video codecs, but it fails to find /dev/mga_vid/ which would make sense since I don't have an MGA video card (and I checked and /dev/mga_vid doesn't exist).  Is there a config file I should change to point to my actual video output device? 

MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:    Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing a.avi.
AVI file format detected.
AVI: ODML: Building ODML index (2 superindexchunks).
VIDEO:  [XVID]  640x480  12bpp  23.976 fps  856.1 kbps (104.5 kbyte/s)
Clip info:
 Software: Windows Movie Maker 2.1
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
alsa-init: using device default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12

---

### Post by Pizzaburgers on 2007-03-13
Here's something interesting.  I have been using an external monitor this whole time and if I unhook the external screen and use the laptop screen I get audio and video using mplayer from the command line.

If I double click on the video file it opens in Totem and I get video but no audio.

If I try to open mplayer and then open the video I get "Error opening/initializing the selected video_out (-vo) device."

I would have no problem just running mplayer from the command line and being done with it, but cmd line mplayer seems to not bring up the controls (pause, back, forward, etc).  Plus it would be nice if I could just double click and have the file play properly.

:confused:

---

### Post by geirha on 2007-03-13
mplayer -vo xv movie.avi 

does that work?

---

### Post by Pizzaburgers on 2007-03-13
Nope, "mplayer -vo xv movie.avi " exhibits the same behavior on the external monitor.

-Pizzaburgers

---

### Post by geirha on 2007-03-13
> **Pizzaburgers said:**
> I would have no problem just running mplayer from the command line and being done with it, but cmd line mplayer seems to not bring up the controls (pause, back, forward, etc).  Plus it would be nice if I could just double click and have the file play properly.

It's actually not that hard using mplayer without the gui
to skip backwards and forward: arrow left/right (~ 10 sec), arrow up/down (~ 1 min), page up/down (~ 10 min)
volume is / and * on the numpad,
play/pause is space
f toggles fullscreen
and q quits

those are just the most used controls, a full list you'll find by reading the manpage (man mplayer)

> **Pizzaburgers said:**
> Nope, "mplayer -vo xv movie.avi " exhibits the same behavior on the external monitor.

what output does it give though?

And also, if you type **mplayer -vo help** it will list all available video outputs, you could experiment and see if any of them work

---

### Post by Pizzaburgers on 2007-03-13
When using the external monitor I get the mplayer window, but just a black screen instead of video.  On the laptop monitor itself, I get the expected output.  

If this was the windows world, I'd say my "acceleration features" weren't getting sent out of the external vga port.  Similar as to how it used to be that you couldnt take a screenshot with Windows Media Player unless you turned off all video acceleration features.

I'd really be ok (but not as happy) with just the laptop screen, but I don't want to go into the console every time I want to play a movie.  A simple double click should do it.  Why does mplayer exhibit different behavior on a "file -> open" vs a command line launch with no swithces?

-Pizzaburgers

---

### Post by geirha on 2007-03-13
> **Pizzaburgers said:**
> When using the external monitor I get the mplayer window, but just a black screen instead of video.  On the laptop monitor itself, I get the expected output.  

Ah, then I misunderstood earlier, thought you got a "file not found" error or something similar

> If this was the windows world, I'd say my "acceleration features" weren't getting sent out of the external vga port.  Similar as to how it used to be that you couldnt take a screenshot with Windows Media Player unless you turned off all video acceleration features.

Yes, it sounds like your external display don't have the overlay (which is the term in xorg). So it sounds like you hafto edit xorg.conf to make it work. I would suggest you look at this page:
[http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver](http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver)
or paste your xorg.conf here, and maybe someone can figure it out.

> I'd really be ok (but not as happy) with just the laptop screen, but I don't want to go into the console every time I want to play a movie.  A simple double click should do it.  Why does mplayer exhibit different behavior on a "file -> open" vs a command line launch with no swithces?

Don't quite understand what you mean, but I would right click the movie-file in nautilus, select properties, then on the "open with" tab I would add the command "mplayer" or "mplayer -fs" (fs for fullscreen). But if you get the xorg configuration sorted, it will probably play in "all" players...

---

### Post by Jim_ubun on 2007-03-14
Yes, i cann't find one video playing can play all the movie of differernt formats.

---

### Post by panch0 on 2007-03-14
> **Jim_ubun said:**
> Yes, i cann't find one video playing can play all the movie of differernt formats.

MPlayer does that. For GUI I use KPlayer rather MPlayer's own GUI. On KDE KPlayer is by far the best I've found.

---

### Post by Masterj15 on 2007-03-14
That happened to me also. I use totem to play back things. If you have ubuntu edjy eft it should come with totem. The plugins are the problem. What I did is I went and download all the gstreamer 10.0 debian packages from the house computer.( I am just a kid am my mom will not allow me to have internet) this means you have to download

gstreamer0.10-pitfdll 
gstreamer0.10-ffmpeg 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse 
gstreamer0.10-plugins-ugly 
gstreamer0.10-plugins-ugly-multiverse 
gxine l
ibxine-main1 l
ibxine-extracodecs 
ogle 
ogle-gui

Just so you know they have to be in .deb file and they will open with Gebidi package manager.
Their may be some missing dependes that you will have to get. Your best choice is [www.debian.com](www.debian.com) and just search their. Make sure when your search that the distrubion is under any. that way you can get the ones. you need. If want to know all the dependes for some code go to the terminal and type in sudo dpkg -i then copy and paste the acutal package into the terminal to have the exact root of the file. ( make sure you have a space after the -i) it will try to install but it will say why it is unconfigured, and they will either tell you that the package is missing or the you have the wrong version. Then go into synaptic package manger to remove the broken package. if they say you will have to remove some things also then go into the terminal and type sudo aptitude and that should bring you to the aptitdue manger. Type in / to search files then search the one that you had install incorectly.(I say that beacuse the package that you installed in the terminal did not have all its dependes) then after that hylight the package and press g. also make sure you have you ubuntu cd in you cd drive. after that you should be able to install more dependes from debian.com

(note all of the ones at the top dont have to be installed. I did not install gxine and gstreamer0.10-plugins-ugly) The plugins that will get you to work mpegs are the bad set.(I think). Just make sure you have gstreamer0.10-pitfdll 
gstreamer0.10-ffmpeg 
gstreamer0.10-plugins-bad 
gstreamer0.10-plugins-bad-multiverse

and their dependes that they say.
Besides libpango10.0-common(that screwd my computer and I had to use sudo aptitide)

Hope this helps out.:) :)

---

### Post by rennen01 on 2007-03-18
Thanks for the info.  The above worked for my Totem.  I still can't get mplayer to play mpegs from gui though.  If I command line launch it, the mpegs play.

---

### Post by kroiz on 2007-03-19
Thanks Masterj15 that helped me.
only since I got internet I just reinstalled the packages from your list. (only those I had, I did not had the last five)

---

