---
title: "Amarok gstreamer engine and ogg for 5.1 sound system????"
date: 2007-09-17
forum: Multimedia Production
---

### Post by ApuX on 2007-09-17
Hi,

I used sound juicer to rip some songs, but I used it with the option channels=5. I don't know  if the quality is really improved for a 5.1 sound system. Any body knows?

Well, the ogg file is correctly played in totem-gstreamer, but not in amarok. It shows a message "Audio output unavailable; the device is busy."

I had to change the output plugin from "autodetect" to "alsa" and change "plug:surround51:0" to "default" in 6 channels. The ogg file can be played now, but the sound is really really bad.

So, I'm trying to change the xine-engine to gstreamer-engine for Amarok. I remember in older version It was possible, but in feisty I can't find the way to do it...

The questions are:

How the "channels" option works for sound juicer?.  Is it possible to convert a CD song into a 5.1 quality ogg file? and, how can I install gstreamer engine for amarok?

Can anybody help me?

Thanks.

---

### Post by stmiller on 2007-09-18
As of [Amarok 1.4.0]("http://packages.debian.org/changelogs/pool/main/a/amarok/current/changelog.html")  gstreamer support was dropped from Amarok. Only xine is available as the engine now.

---

