---
title: "amarok crash when playin wma or save playlist"
date: 2011-01-22
forum: Multimedia Software
---

### Post by AbuHammzah on 2011-01-22
Hello everyone
Amarok crashes every time I try to play a .wma file or save the playlist!  and gives the message "segmentation fault"
And I noticed a process called "python" that consumes the CPU after the crash..

Sometimes it crashes and "python" doesn't appear!
Sometimes it suddenly works for a track or two and then crashes!
Rythmbox works just fine..

Aamarok 2.3.2 build date Oct 2 2010
KDE 4.5.1
Ubuntu 10.10, kernel 2.6.35-24-generic
I would have posted info. about the backend if I knew it..

any ideas?

---

### Post by AbuHammzah on 2011-02-11
The problem turned out to be with the backend rather than Amarok itself, and that is libxine1-ffmpeg

The solution is to switch the backend for Phonon from Xine to GStreamer:
Configure Amarok > Playback > Configure Phonon > Backend
and make GStreamer preferred

Notice that you might have to install phonon-backend-gstreamer first..

Hopefully useful!

But as to saving playlist.. it is still unsolved.. :(

---

