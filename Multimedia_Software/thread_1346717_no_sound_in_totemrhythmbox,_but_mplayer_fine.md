---
title: "no sound in totem/rhythmbox, but mplayer fine"
date: 2009-12-05
forum: Multimedia Software
---

### Post by ___ToniC on 2009-12-05
Hi,

I have a weird problem with audio playback and I have no idea what could be wrong: there is no audio at all in Rhythmbox or Totem. However, mplayer is working perfectly fine.

This morning some security updates were installed with a following reboot. Rhythmbox was running (fine) at this time. Maybe some file got locked or something during shutdown. Booting the old kernel does not help. Oh, and this is 9.10.

All the following sound as expected:
gst-launch-0.10 filesrc location=~/a.mp3 ! mad ! alsasink
gst-launch-0.10 filesrc location=~/a.mp3 ! mad ! pulsesink
gst-launch-0.10 playbin uri=file:///home/xxx/a.mp3
speaker-test -c2

Any help, or possibly important config files, welcome...

Thanks!
Toni

---

### Post by ___ToniC on 2009-12-05
OK, I somehow solved it, still not sure what the reason was.

Anyway, what helped was to purge and reinstall gstreamer. Dont forget to check settings afterwards.

Cheers
Toni

---

