---
title: "Does anybody know what it takes to play this video?"
date: 2008-11-29
forum: Multimedia Software
---

### Post by ar-jar on 2008-11-29
Hi, I've got pretty much everything to play on this 8.10 ubuntu laptop but not videos from the Swedish TV channel 4. For instance: [http://www.tv4.se/1.283438?videoId=1.737504](http://www.tv4.se/1.283438?videoId=1.737504). How can I find out the format for this stream and can anybody out their play it and with what codec in that case? (I kindly decline any comments on my taste for TV shows :-)). Thanks! -Arto
PS. If anybody has info about any time plans for an AVCHD codec for Linux I'd be very interested too. Thanks again!

---

### Post by binbash on 2008-11-29
That video link is working fine here with firefox 3.1b + adobe flash 10 + vlc plugin

---

### Post by JeppeV on 2008-11-29
Plays fine here as well! I have the same setup as the previous poster:)

---

### Post by Sealbhach on 2008-11-29
Doesn't work for me, I've just installed the VLC plugin, I've got Flash 10 and Firefox 3.1b  :confused:


.

---

### Post by binbash on 2008-11-29
click once to blank player, it will load fine

---

### Post by ar-jar on 2008-11-30
Thanks for the answers guys! I checked on one of my Windows machines and the video stream format seems to be WMV V8. I have been able to play V9 fine with a codec from Fluendo butit obviously doesn't decode V8. Now, having installed the mozilla vlc plugin, neither V8 nor V9 works anymore. So it goes...  What codec would you recommend for WMV V8? Thanks!

Another question: is there an application for Linux corresponding to graphedit in Windows, i.e. a GUI-based tool for experimenting with filter graphs, e.g. for video.

Arto

---

### Post by gandaran on 2008-11-30
mplayer plugin plays the video fine, to get mplayer to work (after installing mplayer plugin) in firefox, you have to either remove the totem plugin or disable the totem plugin and enable mplayer plugin in firefox for these type of streams, (wmv if this is realy a wmv stream)

---

### Post by ar-jar on 2008-11-30
Thanks! I tried it. No luck though. No video.

When pasting the video link into mplayer proper it says that it can't find the audio codec. I downloaded the binary codec pack from mplayer and put the dll's into /usr/lib/win32 as per instructions. Obviously that didn't work. And neither does the WMV9 video file from my gallery2 site play any more after I disabled the totem plugin.
Thanks!
Arto

---

### Post by gandaran on 2008-11-30
> **ar-jar said:**
> Thanks! I tried it. No luck though. No video.

When pasting the video link into mplayer proper it says that it can't find the audio codec. I downloaded the binary codec pack from mplayer and put the dll's into /usr/lib/win32 as per instructions. Obviously that didn't work. And neither does the WMV9 video file from my gallery2 site play any more after I disabled the totem plugin.
Thanks!
Arto
you don't need to download the codecs, just install the w32codecs from the medibuntu repo (how to add medibuntu [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) also install the ubuntu-restricted-extras package and type codecs or windows codecs in synaptic package manager search box, you'll find there are still some you can install (lib's), after this you'll have just about every free codec available for linux installed, it must work for you then with mplayer just at it does for me.

---

### Post by ar-jar on 2008-11-30
Well, sometimes things "must" work but still they don't :-) I went through (again) all the instructions here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and installed the gecko media player instead of the basic mplayer. I can play the apple media trailers, I can play my own WMV9 files streamed through gallery2 BUT I can't play the ... clips at [www.tv4.se](www.tv4.se). Time for some serious troubleshooting... -Arto

---

### Post by ar-jar on 2008-11-30
When trying to play the clip directly in MPlayer it says "cannot find codec or audio forat 0x56444152". The other players (VLC, Movie Player, Gnome MPlayer) don't say anything but don't show any video. -Arto

---

### Post by doas777 on 2008-11-30
yep. unfortunately, evil Imaginary Property laws say that this can't "just work", unless you pay a lot. 

fight the power

---

### Post by ar-jar on 2008-11-30
I went through exactly the same installation procedure (again) on my 8.04 stationary machine (both 32 bit btw) and get exactly the same kind of behaviour. I give up "fighting the power". At least for now... -A

---

### Post by ar-jar on 2008-12-02
I didn't quite give up... This is the output from mplayer when trying to play one of the clips. Does this ring a bell somebody? Thanks again!

-Arto

--

arto@Heron:~$ mplayer [http://www.tv4.se/1.283438?videoId=1.745560](http://www.tv4.se/1.283438?videoId=1.745560)
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option msglevel: Unknown suboption 5
Warning unknown option msglevel at line 7
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing [http://www.tv4.se/1.283438?videoId=1.745560](http://www.tv4.se/1.283438?videoId=1.745560).
Resolving [www.tv4.se](www.tv4.se) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.tv4.se](www.tv4.se)
Resolving [www.tv4.se](www.tv4.se) for AF_INET...
Connecting to server [www.tv4.se](www.tv4.se)[80.76.149.158]: 80...
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
V:   0.0   2/  2 ??% ??% ??,?% 0 0 0% 
GNOME screensaver enabled

Exiting... (End of file)

---

### Post by gandaran on 2008-12-02
ar-jar
are you trying the link in stand alone mplayer? it won't work, the correct url stream is [http://anytime.tv4.se/webtv/metafile.asx?p=687625&bw=600](http://anytime.tv4.se/webtv/metafile.asx?p=687625&bw=600) but this too doesn't work in stand alone mplayer! only the mozilla-mplayer-plugin works with the url on my ubuntu 8.10!

---

### Post by ar-jar on 2008-12-02
Thanks, I thought it was the same player pretty much and there was the -playlist option that I tried too.

In the Firefox browser the mplayerplug-in says:
Getting playlist...
Connecting to anytime...
Stopped
That's it. No video.

I'm running Ubuntu 8.10, Firefox 3.0.4 and mplayerplug-in 3.55. I can play my own wmv9 files through gallery2 and as I said and I can play the apple trailers too. It's just this particular site that doesn't work. Do you have any idea as to how i can analyze this behaviour? Log files etc.? Thanks again! -Arto

---

### Post by gandaran on 2008-12-02
look try installing opera, I actually find it connects the video stream better in opera than firefox

---

### Post by ar-jar on 2008-12-02
The Norwegians rule! The video played fine in Opera as you suggested. I conclude that the problem is with Firefox 3.0.4 or the integration. It looked like those who said this worked were using the 3.1 beta. I'm thus looking forward to the next release of Firefox. It does have some very useful addons which give me reason to stick with it. -Arto

---

