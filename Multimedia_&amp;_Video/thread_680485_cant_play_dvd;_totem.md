---
title: "cant play dvd; totem"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by danran on 2008-01-28
I'm using Feisty Fawn with Gnome.  I get this error when I try to play DVD with Totem.  It starts and then quits right away.

daniel@Zuniga:~$ totem
process 18966: arguments to dbus_message_new_method_call() were incorrect, assertion "path != NULL" failed in file dbus-message.c line 1070.
This is normally a bug in some application using the D-Bus library.
libhal.c 1359 : Couldn't allocate D-BUS message
closing
closing
closing
libdvdnav: Using dvdnav version 1.1.4 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/daniel/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000146
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000025d
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 108 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by doorknob60 on 2008-01-28
Try VLC media player or Mplayer.

---

### Post by RomeReactor on 2008-01-28
Hi. Do you have an Intel video card? If so, it's a [known bug in Xorg]("https://bugs.launchpad.net/xorg-server/+bug/38939"). Please open  a terminal (Applications->Accessories->Terminal) and edit your xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down to **Section "Device"** and add the following line to it:
```
Option "LinearAlloc" "16000"
```
Save the file, close the text editor, and press CTRL+ALT+BACkSPACE to restart your display.

---

### Post by danran on 2008-01-28
I've tried both Mplayer and VLC but I get similiar errors and the players also quit right after start-up.  My video card is a Matrox G400.

---

### Post by philc on 2008-01-28
Not sure how much use this is to you, but I came across this How-to today:

[http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback](http://www.tech-recipes.com/rx/2765/ubuntu_enable_dvd_playback)

Shows how to enable DVD playback in Totem, with Xine backend. Maybe try this, rather than the default GStreamer backend for Totem.

---

### Post by danran on 2008-01-29
Nope.  That didn't work either.  Heres the output from when I try playing a DVD with mplayer.  The errors are similiar to what I receive when I try Totem.

daniel@Zuniga:~$ mplayer dvd://
MPlayer 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1.60GHz (Family: 15, Model: 1, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 4 titles on this DVD.
There are 26 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
number of subtitles on disk: 2
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  7500.0 kbps (937.5 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 3 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 4 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 4 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 5 0 

demux_mpg: 24000/1001fps progressive NTSC content detected, switching framerate.
X11 error: BadAlloc (insufficient resources for operation)?,?% 5 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 5 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 5 0 
X11 error: BadAlloc (insufficient resources for operation)?,?% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.2% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.2% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.1% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)1.0% 5 0 
X11 error: BadAlloc (insufficient resources for operation)0.9% 5 0 
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)
X11 error: BadAlloc (insufficient resources for operation)0.9% 5 0 


MPlayer interrupted by signal 2 in module: sleep_timer
X11 error: BadAlloc (insufficient resources for operation)
gnome_screensaver_control()daniel@Zuniga:~$

---

### Post by danran on 2008-01-29
Okay, I swapped the G4 with my other NVidia FX 5200.  DVDs play fine now.  I guess it was the video card.

---

