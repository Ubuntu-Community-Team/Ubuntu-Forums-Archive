---
title: "totem ends early"
date: 2009-06-03
forum: Multimedia Software
---

### Post by ELD on 2009-06-03
Totem always seems to end videos at least a few seconds before they are supposed to end, anyone else see that, extremely annoying!

---

### Post by ELD on 2009-06-04
BUMP

Just had an 18min video end at 7minutes, whats up with it?!

---

### Post by franzbischoff on 2009-06-16
That happens with me too...

All movies that I play at Totem, it ends about 1-3 min before the real end...

Any idea?

---

### Post by ELD on 2009-06-17
What graphics card do you have? I have an ATI card and new drivers got released other day so i am going to install them and test.

---

### Post by franzbischoff on 2009-06-17
Mine is nVidia GF8600 (Asus z53sv laptop).

I tried VLC player, but I get low FPS there (dunno why, well its another topic), so I keep using Totem even with this little bug...

I tried as well to install other codec's from Totem webpage, but I still have the same problem...

---

### Post by ELD on 2009-06-17
Do the videos also seem to stop for a split second a lot in either VLC or Totem for you?

---

### Post by ~sHyLoCk~ on 2009-06-17
Looks like a codec problem. Install the appropriate gstreamer plugins for the video files. What type of file is it? Also did you try with Mplayer?

---

### Post by ELD on 2009-06-17
I have all the codecs installed and they are normal .avi files for the most part, apart from a few .rmvb

---

### Post by m4tic on 2009-06-17
Use VLC:popcorn:

---

### Post by franzbischoff on 2009-06-17
[edited: not solved... forget this post :)]

Hi there!

I guess I solved :) Today night I'll test again. If my videos doesn't "early ends" anymore I post here what I did :)

But seems to be a codec problem.

I use Ubuntustudio 9.04

---

### Post by ELD on 2009-06-17
> **m4tic said:**
> Use VLC:popcorn:
VLC is even worse, besides a problem doesn't go away by just using something else.

---

### Post by franzbischoff on 2009-06-17
> **m4tic said:**
> Use VLC:popcorn:

My VLC "feels like" to play at 15fps :(

I tried to change video output from XVideo to X11 and even OpenGL, but I always get more FPS at Totem...

Strange because I used to play at VLC years ago in Ubuntu 6.06 with no problems...

---

### Post by ELD on 2009-06-17
I'm not sure if my VLC issue is the same but my VLC seems to stop all the time for a split second it's highly annoying and it is noticeable.

---

### Post by franzbischoff on 2009-06-17
not solved :(

Still ending early...

I've downloaded Mplayer but it doesn't plays rmvb...

I'll try to watch a movie at VLC player and see if it also ends early...

---

### Post by andrew.46 on 2009-06-18
Hi franzbischoff,

> **franzbischoff said:**
> I've downloaded Mplayer but it doesn't plays rmvb...

Just for the MPlayer *should* play rmvb files if correctly set up. I attach a screenshot of this rmvb file playing:

```
wget http://samples.mplayerhq.hu/real/AC-cook/cook_5.1/hotel_california_ra5.1_640x480_30s.rmvb
```

using SMPlayer, a gui for MPLayer.

Andrew

---

### Post by franzbischoff on 2009-06-18
Well, now we have lots of info :)

1st SMPlayer complains of my MPlayer version (attachment 1).

2nd My rmvb files cannot be opened in Mplayer and it opens a message (attachment 2). Follow is the console output:

```
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  576x432  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 comment: 
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Error loading dll
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drv4.so.6.0: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drv4.so.6.0, /usr/lib/win32/drv4.so.6.0, /usr/local/lib/win32/drv4.so.6.0
Error loading dll
ERROR: Could not open required DirectShow codec drv4.so.6.0.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drv43260.dll, /usr/lib/win32/drv43260.dll, /usr/local/lib/win32/drv43260.dll
Error loading dll
ERROR: Could not open required DirectShow codec drv43260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Error loading dll
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.1 kbit/4.54% (ratio: 8010->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.7 (02.6) of 2921.0 (48:41.0)  1.3% 
```

3rd your rmvb sample gives me the "attachment 3" message [at totem it asks for Real Audio G2 (cook) codec, and fails to find it at repository] . Follow is the console output: 

```
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
[real] Video stream found, -vid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 1
Stream mimetype: logical-fileinfo
VIDEO:  [RV40]  640x480  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.so, /usr/lib/win32/drvc.so, /usr/local/lib/win32/drvc.so
Error loading dll
ERROR: Could not open required DirectShow codec drvc.so.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drvc.dll, /usr/lib/win32/drvc.dll, /usr/local/lib/win32/drvc.dll
Error loading dll
ERROR: Could not open required DirectShow codec drvc.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drv4.so.6.0: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drv4.so.6.0, /usr/lib/win32/drv4.so.6.0, /usr/local/lib/win32/drv4.so.6.0
Error loading dll
ERROR: Could not open required DirectShow codec drv4.so.6.0.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Win32 LoadLibrary failed to load: drv43260.dll, /usr/lib/win32/drv43260.dll, /usr/local/lib/win32/drv43260.dll
Error loading dll
ERROR: Could not open required DirectShow codec drv43260.dll.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Opening video decoder: [realvid] RealVideo decoder
Error: /usr/lib/codecs/drvc.bundle/Contents/MacOS/drvc: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: drvc.bundle/Contents/MacOS/drvc, /usr/lib/win32/drvc.bundle/Contents/MacOS/drvc, /usr/local/lib/win32/drvc.bundle/Contents/MacOS/drvc
Error loading dll
ERROR: Could not open required DirectShow codec drvc.bundle/Contents/MacOS/drvc.
Read the RealVideo section of the DOCS!
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30345652.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
[cook @ 0x8972330]MC_COOK not supported!
Could not open codec.
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/codecs/cook.so: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: cook.so, /usr/lib/win32/cook.so, /usr/local/lib/win32/cook.so
Error loading dll
ERROR: Could not open required DirectShow codec cook.so.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/codecs/cook.so.6.0: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: cook.so.6.0, /usr/lib/win32/cook.so.6.0, /usr/local/lib/win32/cook.so.6.0
Error loading dll
ERROR: Could not open required DirectShow codec cook.so.6.0.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Win32 LoadLibrary failed to load: cook.dll, /usr/lib/win32/cook.dll, /usr/local/lib/win32/cook.dll
Error loading dll
ERROR: Could not open required DirectShow codec cook.dll.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Win32 LoadLibrary failed to load: cook3260.dll, /usr/lib/win32/cook3260.dll, /usr/local/lib/win32/cook3260.dll
Error loading dll
ERROR: Could not open required DirectShow codec cook3260.dll.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [realaud] RealAudio decoder
Error: /usr/lib/codecs/cook.bundle/Contents/MacOS/cook: cannot open shared object file: No such file or directory
Win32 LoadLibrary failed to load: cook.bundle/Contents/MacOS/cook, /usr/lib/win32/cook.bundle/Contents/MacOS/cook, /usr/local/lib/win32/cook.bundle/Contents/MacOS/cook
Error loading dll
ERROR: Could not open required DirectShow codec cook.bundle/Contents/MacOS/cook.
Read the RealAudio section of the DOCS!
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x6B6F6F63.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video
```

I looked around, and seems Ubuntu (and other dists) lacks the rmvb codecs for Mplayer in their repository...

at Mplayer homepage, they say they play .rmvb, but the documentation webpage is offline (404 error).

Seems we have 3 problems:
1) Totem ends early
2) VLC plays with a "low FPS sensation" only with .rmvb files (tested several XVID 30fps files and they play good at VLC)
3) Mplayer doesnt play rmvb without proper and complicated configuration :)

How could we split this topic? Or rename it? :)

---

### Post by ELD on 2009-06-18
I renamed the topic to "media player problems" but crappy vbulletin doesn't rename it in the topic list, i think only a mod/admin can do that?

---

### Post by rvm4000 on 2009-06-18
> **franzbischoff said:**
> 1st SMPlayer complains of my MPlayer version (attachment 1).

You can find newer versions of mplayer here:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

> **franzbischoff said:**
> 
3) Mplayer doesnt play rmvb without proper and complicated configuration :)

:o

You only have to install the w32codecs or w64codecs package that you can find in medibuntu.

[http://packages.medibuntu.org/jaunty/w32codecs.html](http://packages.medibuntu.org/jaunty/w32codecs.html)
[http://packages.medibuntu.org/jaunty/w64codecs.html](http://packages.medibuntu.org/jaunty/w64codecs.html)

---

### Post by franzbischoff on 2009-06-18
thank you :) I'll test it later.

So we still with Totem and VLC issues :)

---

### Post by franzbischoff on 2009-06-19
I've tested last night at my wife Toshiba laptop (Intel graphic card):

1) started Totem to play a .rmvb file (20min)
2) Totem asked for codecs and installed from repository:
   - gstreamer0.10-ffmpeg 0.10.6.2-1ubuntu2
   - gstreamer0.10-plugins-bad 0.10.6.2-1ubuntu2
   - gstreamer0.10-plugins-ugly 0.10.6.2-1build1
3) Started to play the file
4) Ended about 2min before the real end

:(

Seems to be a real bug

---

### Post by ELD on 2009-06-19
Then one of us needs to report it!
Edit > [https://bugs.launchpad.net/ubuntu/+bug/389419](https://bugs.launchpad.net/ubuntu/+bug/389419)

---

