---
title: "(insufficient resources for operation) when running VLC"
date: 2008-11-21
forum: Multimedia Software
---

### Post by warsong on 2008-11-21
I followed the guide in this thread:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but I didn't use steps 3-5 cause I'm not interested in video or sound editing at the moment.

I did however install vlc using

sudo apt-get install vlc.

I downloaded a video and when I try to play it, vlc opens and closes.
I ran vlc through the terminal with -vvv and it says the following:

```
[00000404] qt4 interface debug: Video is resizing to: 624 352
[00000455] qt4 video output debug: Qt FS: Attaching Vout
[00000455] qt4 video output debug: Qt: Changing Fullscreen Mode
[00000458] main window debug: using vout window module "qt4"
[00000458] main window debug: TIMER module_Need() : 347.460 ms - Total 347.460 ms / 1 intvls (Avg 347.460 ms)
[00000404] qt4 interface debug: Updating the geometry
[00000454] main audio output warning: output date isn't PTS date, requesting resampling (69863)
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000454] main audio output warning: buffer is 69863 late, triggering upsampling
QPainter::begin: Paint device returned engine == 0, type: 1
[00000455] xvideo video output debug: XShm video extension v1.1 (with pixmaps, opcode: 145)
[00000455] xvideo video output debug: Window manager supports NetWM
[00000455] message video output warning: message queue overflowed
[00000455] xvideo video output debug: Window manager supports _NET_WM_STATE_FULLSCREEN
[00000455] xvideo video output debug: Window manager supports _NET_WM_STATE_ABOVE
[00000455] xvideo video output debug: Window manager supports _NET_WM_STATE_BELOW
[00000455] main video output debug: using video output module "xvideo"
[00000455] main video output debug: TIMER module_Need() : 590.448 ms - Total 590.448 ms / 1 intvls (Avg 590.448 ms)
[00000455] main video output debug: waiting for thread initialization
[00000455] main video output debug: thread started
[00000455] main video output debug: got 8 direct buffer(s)
[00000455] main video output debug: picture in 624x352 (0,0,624x352), chroma I420, ar 382909:216000, sar 1:1
[00000455] main video output debug: picture user 624x352 (0,0,624x352), chroma I420, ar 382909:216000, sar 1:1
[00000455] main video output debug: picture out 624x352 (0,0,624x352), chroma I420, ar 382909:216000, sar 1:1
[00000455] main video output debug: direct render, mapping render pictures 0-6 to system pictures 1-7
[00000455] main video output debug: thread 2907163536 (video output) created at priority 15 (video_output/video_output.c:504)
[00000404] qt4 interface debug: New Event: type 1109
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83

```

The one thing that I see is the "insufficient resources for operation".
The first thing that comes into my head is that I didn't activate the proprietary drivers for my ATI card (x1400 XT 256meg). I was reading about the FGLRX drivers and I wasn't sure I should install them.
What do you guys think?
I could be completely wrong though haha.....

My system specs:
Ubuntu 8.10
2 gigs of ram.
160 gig hard drive (40 allocated to ubuntu and 2 of that for swap)

Let me know if you need anything else.
Thanks!

---

### Post by warsong on 2008-11-21
Any ideas?

---

### Post by rednick on 2008-12-03
Are you getting the "Aperture beyond 4GB - Ignoring" message at bootup?

I am and my VLC does that.  My ubuntu-using buddy isn't and his VLC works.
I therefore wonder if the two are linked.

---

### Post by cursednomore on 2009-03-15
> **rednick said:**
> Are you getting the "Aperture beyond 4GB - Ignoring" message at bootup?

I am and my VLC does that.  My ubuntu-using buddy isn't and his VLC works.
I therefore wonder if the two are linked.

This does seem to be the case. I had the same problem and upgraded to an alpha release of Jaunty as [suggested in this bug resolution]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070") and DVDs now play properly.

---

