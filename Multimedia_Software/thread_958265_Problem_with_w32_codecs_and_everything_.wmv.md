---
title: "Problem with w32 codecs and everything .wmv"
date: 2008-10-25
forum: Multimedia Software
---

### Post by darthshak on 2008-10-25
I run Ubuntu 8.04. I recently got hold of some .wmv files, which didnt play on vlc. 
The error i get is that it cannot find audio decoder wmas for the file.
I tried mplayer, but it complains about LIRC support and doesnt play a thing.

Now, I have tried *everything* that has been suggested on every forum and still no luck. Here's the list :


1) I installed w32codecs, ubuntu-restricted-extras, non-free codecs, mplayer. No luck
2) I compiled vlc from source, mplayer from source, tried running the video on both. No luck.
3) I checked out the videos to see to it they werent DRM-protected. 
4) I tried setting the preferred encoders list to point to /usr/lib/codecs explicitly, but no luck.

What was stranger, was when i tried SMplayer, it whined about no wmv9mod.dll, but the file is very much there, present in /usr/lib/codecs

The .wmv plays fine for other people on mplayer on linux, and it seems to run on Windows Media Player 11 on windows just fine. 

I'm at my wits' end on this. Please help.

---

### Post by xc3RnbFO8P on 2008-10-25
Did you try Medibuntu:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by darthshak on 2008-10-26
Yes, I got the w32codecs of the medibuntu repositories.

---

### Post by cor2y on 2008-10-26
OK lets take it from the top please post the error from the terminal when you try to play the file in mplayer.

---

### Post by darthshak on 2008-10-26
Here's the message with mplayer. The LIRC support thing seems to have gone to be replaced with this : 

```

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Lec-1.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV3]  640x480  24bpp  1000.000 fps  750.0 kbps (91.6 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 280.
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /usr/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmspdmod.dll, /usr/lib/win32/wmspdmod.dll, /usr/local/lib/win32/wmspdmod.dll
IMediaObject ERROR: 0x88acea9  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmspdmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dshow] Win32/DirectShow decoders
Win32 LoadLibrary failed to load: wmavds32.ax, /usr/lib/win32/wmavds32.ax, /usr/local/lib/win32/wmavds32.ax
Warning: DS_Filter() could not open DirectShow DLL.  (DLL=wmavds32.ax, r=0x0)
ERROR: Could not open required DirectShow codec wmavds32.ax.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0xA.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.

```

---

### Post by Sef on 2008-10-26
Do the files have a DRM?  If so, they won't play.

---

### Post by gandaran on 2008-10-26
do you have libdvdcss2 for drm protected/encrypted playback installed?

---

### Post by darthshak on 2008-10-26
Nope. The files do not have DRM protection. I doubly checked that.

---

### Post by cor2y on 2008-10-26
Well the answer is in your error message.
I could be wrong but mplayer is looking for the w32codecs in /usr/lib/win32 thats an old location for the w32codecs, i don't recall if they have used that directory in a long while the default these days is /usr/lib/codecs, so what you can do is change the directory mplayer is looking for the codecs in or create a symlink to the codecs in /usr/lib/win32, when compiling mplayer you should use the "--codecsdir=" so mplayer knows where the win32codecs are installed or are extracted to.
So if you used the win32codec pack from medibuntu when compiling mplayer "--codecsdir=/usr/lib/codecs" should be used with ./configure

**Edit**
To create the symlink first see where your w32codecs are installed so via the terminal or gname searcher look for "wmv9dmod.dll" without the quotes.
If the w32codec deb is installed from medibuntu it should be in /usr/lib/codecs so to symlink you will have to either create /usr/lib/win32 and symlink and if it already exists then symlink it.
```

sudo mkdir /usr/lib/win32
```
```
sudo ln -s /usr/lib/codecs /usr/lib/win32
```

---

### Post by darthshak on 2008-10-26
Well, that still didnt solve the problem. I had to do the ugly thing of moving the w32codecs to /usr/lib/win32

It worked after i did this.
I have one question though : Would it be possible to do something similar for vlc? I would prefer vlc as my speaker volume is very low(I have a Thinkpad T61).

---

### Post by darthshak on 2008-11-01
<bump> Is this problem equivalent to one of the millenium prize problems or something? :)

---

### Post by darthshak on 2008-11-02
I got version 0.9.3 off the web and it doesnt work either.
Come on, SOMEONE has to know what the problem is

The codecs are right there in /usr/lib/codecs and in /usr/lib/win32.
Why cant vlc find them?!

---

### Post by darthshak on 2008-11-03
<bump> Come on, somebody?

---

### Post by xc3RnbFO8P on 2008-11-03
Read this:
[http://lj4newbies.blogspot.com/2007/11/install-win32-codecs-for-mplayer-in.html]("http://lj4newbies.blogspot.com/2007/11/install-win32-codecs-for-mplayer-in.html")

---

### Post by darthshak on 2008-11-03
Well, it works on mplayer. But I need it on vlc because the volume is too low on my laptop. Headphones arent much help either.

---

### Post by Kangarooo on 2009-04-20
Yes i also want on VLC and maybe TOTEM?
ok only VLC

Ill now try mencoder couse it should now also should be able to convert them.

---

### Post by ranie on 2009-10-05
VLC is working on my karmic (by accident)
I got a Bad file descriptor error when install the pacage from mediabuntu pacage arcive, using GDebi installer.
I downloaded the w32codecs pacage from [http://packages.medibuntu.org/karmic/w32codecs.html](http://packages.medibuntu.org/karmic/w32codecs.html)
Then installed it using 
      
dpkg -i w32codecs_20071007-0medibuntu5_i386.deb

Then I Created the folder and link above. To me it looks as there is some issues installing w32codecs using GDebi and apt-get.

mplayer on the other hand is not working :( trying to play a dvd gives fatale error! Error opening/initializing the selected video_out (-vo) device

---

