---
title: "Can't play Intel Video 5, even with pitfdll and 32bit Intrepid"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Lars Stokholm on 2009-02-05
The following is the output from Totem when I try to play [_this IV50 file_]("http://samples.mplayerhq.hu/V-codecs/IV50/wigout.avi").> ** Message: don't know how to handle video/x-indeo, indeoversion=(int)5, framerate=(fraction)20/1, width=(int)320, height=(int)240
** Message: Missing plugin: gstreamer|0.10|totem|Intel Indeo 5 decoder|decoder-video/x-indeo, indeoversion=(int)5 (Intel Indeo 5 decoder)I followed the instructions from the pitfdll readme and extracted [_this file_]("http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2") into /usr/lib/win32 (no, not /usr/lib/codecs where pitfdll won't find it), so I do have ir50_32.dll:> $ locate ir50_32.dll
/usr/lib/win32/ir50_32.dllHelp? :)

---

### Post by andrew.46 on 2009-02-05
Hi,

One solution is to use a full installation of the svn MPlayer. I attach a screenshot of the svn MPlayer and SMplayer successfully playing the file you mention.

Andrew

---

### Post by Lars Stokholm on 2009-02-05
Thank you. I often miss MPlayer, since switching from FreeBSD, but one of the main reasons for doing so, was the relatively sane default Ubuntu, not to say the easy setup. Principally, I sort of like to stay within reasonable boundaries of what Ubuntu has to offer, even at some cost, so although I don't like Totem too much (yet?) I'll prefer a solution fit for that.

Of course if no such solution exist, it will be difficult to achieve. :) But in that case, do you know if work is being done to get Intel Video 5 to play in Totem?

---

### Post by andrew.46 on 2009-02-05
Hi Lars,

> **Lars Stokholm said:**
> Thank you. I often miss MPlayer, since switching from FreeBSD, but one of the main reasons for doing so, was the relatively sane default Ubuntu, not to say the easy setup. Principally, I sort of like to stay within reasonable boundaries of what Ubuntu has to offer, even at some cost, so although I don't like Totem too much (yet?) I'll prefer a solution fit for that.

It is a choice of course :-).

> Of course if no such solution exist, it will be difficult to achieve. :) But in that case, do you know if work is being done to get Intel Video 5 to play in Totem?

I will admit that I am no fan of Totem (and secretly not a big fan of Gnome either!) so I cannot answer that one :-).

All the best,

Andrew

---

### Post by mc4man on 2009-02-05
While my main 8.10 install is setup in such a way to preclude the use of all the gstreamer plugins (and I don't use totem in any fashion), a quick ck. on a hardy box shows that "wigout.avi" is quite playable in totem (gstreamer).


> (no, not /usr/lib/codecs where pitfdll won't find it), so I do have ir50_32.dll:
I not sure why your doing that, the needed codec(s) will be found properly in /usr/lib/codecs, typically /usr/lib/win32 is a folder link to /usr/lib/codecs.

So in terms of doing this the 'gnome/gstreamer/ubuntu' way you would've simply installed ...

The multiverse versions of gstreamer bad, ugly, and the pitfdll plugin (the ffmpeg plugin is useful though not needed here I don't believe
w32codecs ( which would install to /usr/lib/codecs and create the ...win32 link

At this point you'd have support for  Intel Video 5 in gstreamer apps


(there is almost no difference between the mplayer codec pack and a current w32codec package from medibuntu or debian-multimedia (sid), the most notable is the .deb package creates the ...win32 link

---

### Post by Lars Stokholm on 2009-02-05
> **mc4man said:**
> I not sure why your doing that, the needed codec(s) will be found properly in /usr/lib/codecs, typically /usr/lib/win32 is a folder link to /usr/lib/codecs.Sweet, that was it! Thanks.

I named it /usr/lib/codecs at first, but when I played one of my videos, Totem complained that it couldn't find the codec in /usr/lib/win32. So I renamed it. But now it wants other codecs in /usr/lib/codecs? What makes it look for some codecs in one place and some in another?

So problem solved, I'll just use the symlink, I just wonder why I need it...

---

### Post by mc4man on 2009-02-05
> I just wonder why I need it
Not 100% sure but I believe some apps are coded to look to /usr/lib/win32 and if not found will stop there. Others may look to /usr/lib/codecs and some will follow a progresion and look for /usr/lib/codecs, /usr/local/lib/win32 and /usr/lib/win32.

The standard now seems to  be /usr/lib/codecs with links to there.

Here's what mplayer does (removed the codecs so it couldn't find (I believe it first looked to /usr/lib/codecs though not noted

> doug@doug-desktop:~$ mplayer 2.wma
MPlayer dev-SVN-r28349-4.3.2 (C) 2000-2009 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
name: The Song Remains the Same
author: Led Zeppelin
================================================== ========================
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll
IMediaObject ERROR: 0x894e14d could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wma9dmod.dll.
ADecoder preinit failed
ADecoder init failed
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
IMediaObject ERROR: 0x894e14d could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmadmod.dll.
ADecoder preinit failed
ADecoder init failed
Cannot find codec for audio format 0x163.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video
Exiting... (End of file) 

---

