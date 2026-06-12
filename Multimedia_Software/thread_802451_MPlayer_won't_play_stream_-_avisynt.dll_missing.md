---
title: "MPlayer won't play stream - avisynt.dll missing?"
date: 2008-05-21
forum: Multimedia Software
---

### Post by lodp on 2008-05-21
Hi,

I'm trying to get mplayer to play this mp4 stream from archive.org, but it won't cooperate. VLC and kaffeine won't play it either. I've got w32codecs installed, and I don't have any problems playing other files (divx, xvid, wmv, rm...)

Maybe you guys can try if it plays for you: [SIZE="3"][http://www.archive.org/stream/dn2008-0521_vid/dn2008-0521_256kb.mp4](http://www.archive.org/stream/dn2008-0521_vid/dn2008-0521_256kb.mp4)[/SIZE]


Here's what I get if I open it with mplayer in command line:

> $ mplayer [http://www.archive.org/stream/dn2008-0521_vid/dn2008-0521_256kb.mp4](http://www.archive.org/stream/dn2008-0521_vid/dn2008-0521_256kb.mp4)
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.70GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Warning unknown option -ao at line 3

Playing [http://www.archive.org/stream/dn2008-0521_vid/dn2008-0521_256kb.mp4](http://www.archive.org/stream/dn2008-0521_vid/dn2008-0521_256kb.mp4).
Resolving [www.archive.org](www.archive.org) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.archive.org](www.archive.org)
Resolving [www.archive.org](www.archive.org) for AF_INET...
Connecting to server [www.archive.org](www.archive.org)[207.241.229.39]: 80...
Cache size set to 320 KBytes
Cache fill:  0.12% (379 bytes)
**Win32 LoadLibrary failed to load: avisynth.dll**, /usr/lib/codecs/avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll

I've searched the web quite a bit. I tried placing avisynth.dll from sourceforge ([http://sourceforge.net/projects/avisynth2/](http://sourceforge.net/projects/avisynth2/)) in /usr/lib/codecs/

That got rid of the error, but the file still wouldn't play, mplayer just exits.

I've read in other threads that starting mplayer with the -playlist option worked for some when they got the avisynth.dll error, but it didn't for me.

---

### Post by croto on 2008-05-21
Hi,

The main problem is that the link you are using is not the url to the stream but an http web page that loads the stream (try to open the link in firefox to see what I'm trying to say). That web page has a flash application that opens the stream. Analyzing the network traffic with wireshark I found the right stream url is 

rtsp://ia360919.us.archive.org:554/3/items/dn2008-0521_vid/dn2008-0521_256kb.mp4

However, it seems that my version of mplayer has problems playing it. I could play it with VLC though.

---

