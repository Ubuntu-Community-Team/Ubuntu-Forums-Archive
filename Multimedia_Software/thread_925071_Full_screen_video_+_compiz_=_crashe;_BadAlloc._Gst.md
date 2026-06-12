---
title: "Full screen video + compiz = crashe; BadAlloc. Gstreamer-properties seg faults"
date: 2008-09-20
forum: Multimedia Software
---

### Post by memories on 2008-09-20
I cannot play videos in full screen while compiz is enabled. This happens on every player (mplayer, vlc, totem etc). 

Some people recommend going to Multimedia Systems Selector but any video setting I change there causes it to segfault. 

> 
$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
Segmentation fault

[I]
One workaround for the video problem is to enable desktop zoom and just zoom into the video to make it full screen. Quality is perfect but it's annoying to have to do this and keyboard input doesn't work. [/I]

I am using an nvidia geforce 6600GT and dual screen, but this problem occurred when I had single screen.

PLEASE HELP!

---

### Post by LilaQ on 2008-09-20
I have exactly the same problem. Sometime, but really rarely, fullscreen works. Most of the time if I try to switch to fullscreen (doesn't matter in which way, doubleclick, 'f', etc) the app tries to switch to fullscreen but instantly crashes.

I always get BadAlloc errors when I 'log' via terminal

Any clues on that? It's really annoying :(

---

### Post by Kprojekt on 2008-11-05
I'm getting this problem after a dist-upgrade to Ibex, all media players are affected, even the test video in Multimedia Selector crashes, and sometimes it happens regardless of fullscreen. 

Sometimes VLC will start, but whenever any Composting item is started (like the volume display) it will crash.

Here is some output running VLC - then crashes: 

kit@BigRock:~$ vlc /media/Superflous/MOVIES/Dexter/Dexter.S03E06.HDTV.XviD-LOL.avi 
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Remote control interface initialized. Type `help' for help.
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000428] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  144
  Current serial number in output stream:  145

(process:32183): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:32183): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(process:32183): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(process:32183): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
kit@BigRock:~$ cvlc /media/Superflous/MOVIES/Dexter/Dexter.S03E06.HDTV.XviD-LOL.avi 
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
Remote control interface initialized. Type `help' for help.
[00000412] dummy interface: using the dummy interface module...
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  647
  Current serial number in output stream:  648


Here is the Multi Media Selector crash: 

kit@BigRock:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 54 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault

---

### Post by Kprojekt on 2008-11-05
Just wanted to add, that this all goes away if extra effects (composting is turned off)

This is also a bump.

---

### Post by Kprojekt on 2008-11-05
This seems to be problems between gstreamer and the new Xorg.

---

### Post by JohnnieRico on 2008-11-09
I'm seeing similar symptoms on Ubuntu 8.04 (2.6.24-21-generic): with both vlc and totem, I can start playing back a video, but when I change it to fullscreen (or resize beyond a certain size), both players exit with:

  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()

I have plenty of system memory:

$ free
             total       used       free     shared    buffers     cached
Mem:       2075468     871988    1203480          0      98696     409680
-/+ buffers/cache:     363612    1711856
Swap:      2939884          0    2939884

My video card is a 64MB GeForce FX Go5200, driven by NVIDIA UNIX x86 Kernel Module  173.14.12.

gstreamer-properties doesn't crash for me, but if I maximize the "test video" window (the one with the bars and static), it exits with the same BadAlloc error.

And, if I select 'None' under Appearance->Visual Effects (thus disabling compiz?), then all these problems go away.

---

### Post by JohnnieRico on 2008-11-13
Hello? Should a bug be filed against this?

---

### Post by cbaltar2 on 2008-11-16
Guys, if only you'd know how much pain this gave me - I was getting this same error under VLC, so I ran it in terminal to see what errors it'd give me - first I thought it'd be a PULSEAUDIO error, but there was also this X11 stuff - anyway, turning compiz off fixes it. This problem is not Ubuntu-specific, since I'm getting the same behavior in OpenSuSE 11.

---

### Post by DarkDisaster on 2008-11-16
same error with me in 8.10... When compiz is off, everything rules!

---

### Post by maticer on 2009-02-25
I got the same issue on Interpid Ibex with all players and Nvidia 6600GT :(

Any soulutions/workaround avaliable for that?

---

### Post by paradox82 on 2009-04-28
new bump... Running intrepid fully updated with 6600GT. Exactly the same problem. With totem and vlc when I go fullscreen I get:

BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)

I would turn off my compiz but I love my Gnome do Docky (which needs compiz). Have anybody been able to isolate what i need to turn off in compiz settings to make fullscreen work.

PS. Boxee is aslo extremely slow when run with compiz on, probably the same bug.

---

### Post by SDXeus on 2009-04-28
I am also experiencing a similar error with my new installation of Jaunty 9.04. I used a fresh install and everything else has worked perfect. Not so with playing movies. I wanted to test the dvd playing capabilities of the new install. I downloaded and installed VLC and slapped in a dvd. The movie played fine until I wanted to enter full screen mode.  My computer crashed, giving some random output, then bleaked.

So I hope someone is able to help.

.::. system spec .::.

hp dv5z-1000 cto hp pavilion entertainment pc
dual-boot with windows vista, hp support partition also on hdd

Ubuntu Jauny 9.04 amd64
AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-80
3GB memory, 28.1GB hard drive alotment
ATI Mobility Radeon HD 3400, using proprietary drivers

VLC 0.9.9a
movie: Traitor

---

### Post by amast on 2009-04-29
Yea, I just updated to Jaunty from Intrepid (update, not new install) and all my video apps crash immediately with some error (most of which are the same or related).  These crashes are when I attempt to play a DVD. 


XINE: 

This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2506
  Current serial number in output stream:  2507

----------------------------------------------------------------------

TOTEM:

** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, codec_data=(buffer)1210, rate=(int)44100, channels=(int)2
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 310 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

----------------------------------------------------------------------

ACIDRIP: 

No error on preview but I cannot see anything, only audio

----------------------------------------------------------------------

VLC:

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

---

### Post by gotak on 2009-05-02
How come there isn't any real fix for this instead of just "don't use XV"?

Really annoying since the other driver the No XV version is just a bit crappier then when XV was working.

---

### Post by SvEnX on 2009-05-02
Same problem here, full screen crashes whole PC. W/O Compiz I can enter full screen, but it isn't a solution, because everybody love's Compiz.

---

### Post by drooze on 2009-06-01
Same problem here.

both totem and VLC crash when I want them to go fullscreen.

with VLC, however, it works about 1 out of 8 times, and it doesn't crash.

also, the first time I open a video, it doesn't crash. second video (or the same video out of fulscreen, and then fullscreen again) does crash. untill I reboot again.

has anyone filed a bugreport for this yet? I searched, but to no avail.

---

### Post by bgiannes on 2009-06-01
I think I have the same problem?

However I have just done a clean install of 9.04, and video players mplayer, vlc, elisa, xbmc will crash after a time, sometimes +30minutes!? something sooner.  Most times gnome crashes out altogether and I end up back at the logon screen, other times it just hanges w/ the sound looping, (hate that!!) and a hard reset is required.  Or other times the player just crashs.  

I have a both 9.04 i386 and 9.04 amd64 install on this HTPC, (and both have this problem) but the 64bit install is unusable, as a HTPC :( 

w/ compiz off it still happens...

my system is:
E8400
2GB
9500GT
Asus Turbo P45

---

### Post by jaj23 on 2009-07-31
I have the same problem with 9.04. Crash to back screen requiring re-start when playing Totem and VLC full screen. Zoom effect works, though has annoying lines top and bottom of video. Havnt tried turning compiz off, but i want a different solution as i want compiz on. This all started when i did a fresh install a few weeks ago and updated all the video and audio codecs. Never had a problem before that.

Been a while since last post, so maybe someone has found a solution?

jaj23

---

### Post by Dominym on 2009-09-05
I'm having this same problem. I can watch online videos fullscreen, but when I use VLC or Mplayer, the entire PC crashes when I try to switch to fullscreen.
Anyone figured this out yet?

---

### Post by vkovtun on 2009-09-13
Why do people experience the same problem for almost 1 year?! Couldn't it be solved by now yet? Why doesn't anyone from Ubuntu professionals at least say something about it?
:(

---

### Post by deuz on 2009-09-29
I've the same problem

---

### Post by knarfomat on 2009-10-08
me too...

---

### Post by HighTech on 2009-10-10
Fix for VLC:

Open vlc and go to preferences (ctrl+p) -> video -> and change video output to "x11 video output"

Does anybody who knows more about this kind of stuff know how to do the above for other media players?

---

### Post by Diskdoc on 2009-11-02
Hmm..maybe my problem is related:

[http://ubuntuforums.org/showthread.php?t=1311263]("http://ubuntuforums.org/showthread.php?t=1311263")

---

### Post by hcaicedo on 2009-11-12
Same problem here. I am using 9.10

---

### Post by Philip550c on 2009-11-20
> **Kprojekt said:**
> Just wanted to add, that this all goes away if extra effects (composting is turned off)

This is also a bump.

> **Diskdoc said:**
> Hmm..maybe my problem is related:

[http://ubuntuforums.org/showthread.php?t=1311263]("http://ubuntuforums.org/showthread.php?t=1311263")

This is the problem I'm having. When going fullscreen the extra effects makes it freeze. I'm only having this problem in VLC though. This is happening on all 5 of my computers all with different hardware. I'm using Intrepid and Jaunty.

---

### Post by baccilus on 2009-11-21
I have the same problem. It is with both SMPlayer and VLC. I am on Ubuntu 9.10 64Bit. I have ATI 4670HD with the latest driver (9.11) installed from their site. But once I disable the Desktop effect, everything runs beautifully.

---

### Post by rifter on 2010-03-02
For a lot of people, BadAlloc errors are fixed by switching from Video4Linux output to X11 Video Output.

For vlc you can do this either by calling it on the command line

vlc --vout x11

or better yet change the output in the preferences of vlc:

Tools -> Preferences -> Video -> Output -> X11 video output

hit save and try it out.

Now to fix it for Totem Movie Player you have to use the

gstreamer-properties

application to change the output.  You can launch that command from alt-f2 or the terminal, or you can instead go to 

System -> Preferences -> Multimedia Systems Selector

then go to the video tab and change the default output plugin to "X Window System"

One way you know you have this problem is, when you fullscreen the video player it crashes immediately.  The BadAlloc error will only show up if you start the video player from the command line, otherwise it is hidden from you.  BadAlloc can happen for a lot of reasons, but someone with a modern video card getting that for a video is completely bogus.  Turning Video4Linux off by changing output to X11(in the player, it's a per player setting unfortunately) does the trick for those people.  Worked for me.

---

### Post by alex_yen on 2010-04-23
That's right, going to X11 fixes the problem, but with X11 output I get another problem: the video "jumps" during the playback. It looks like it frezes and jumps over the frames a lot, not smooth video.

---

### Post by davidwillis on 2010-05-10
I have the same problem, using a nvidia geforce 7300 with 128mb of ram.  I found a post in another thread mentioning this:

> Re: Video players (Totem, VLC, etc.) fail with BadAlloc error
Thought I'd post my solution to this error. I'm using the i810 graphics driver, and my video card uses shared memory, which seems to be causing the error. My problem was that all movie players crashed when playing any video with a resolution higher than 640x480. After adding two lines to my xorg.conf file, I can finally play my 1024x768 screencasts.

I added these lines to Section "Device" in xorg.conf:
Code:

Option "VideoRam" "65536"
Option "CacheLines" "1980"

Related to bug #4229

I added that line, except I doubled the VidoeRam to 131072.  I am not sure if that is right, or if I should change my cachelines, but it did let me increase my screen more without crashing.  In fact I can run full screen if nothing else is running, but If I open up firefox, and a few other apps, I can not go full screen.

---

### Post by davidwillis on 2010-05-26
I just tried out a live cd with fedora and installed the experimental 3d (using the nouveau driver).  And it works.  I can run as many windows as I want, and can watch video at full screen.

Now if I can get it to work with ubuntu....

---

### Post by Vinre on 2010-09-28
I know the thread is a bit old, but...

I'm having a similar problem. with streaming video (youtube and hulu) if I try to go full screen, it crashes the window (go go chromium). I don't have problems with vlc or totem, and the REALLY odd thing is that I didn't have this problem until recently. It's very frustrating and embarrassing, when I try to watch videos with friends on my shiny new computer that I've had for less than 90 days and we cant full screen. they all use windows too so you can imagine what their comments are.

I've tried killing compiz with killall compiz, and I get no process found. I don't know anything! *sob sob sob* It's not the end of the world, but it's an inconvenience and it WAS working before...

---

