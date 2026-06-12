---
title: "audio mixer device"
date: 2008-06-07
forum: Multimedia Software
---

### Post by sovereign_soul on 2008-06-07
On windows, audio input can be done using either a microphone or a sound mixer device (options are available in volume control). but there's no similar thing on Linux. 

I'm using Ubuntu 8.04, alsa but no pulseaudio. So can any1 tell me how to access a mixer device ? I want to use ti to play music ..

Thanks

---

### Post by DJ_Peng on 2008-06-08
There is a Volume Control mixer that you get by double clicking the Volume icon on the right hand side of your upper panel. You cal also right click the icon and select en Volume Control.  You can also access it at Applications > Sound & Video > Volume Control.

---

### Post by mastermindg on 2008-06-08
I think that most people do not fully understand what PulseAudio is exactly:

It's not the replacement for ALSA or OSS or ESD. It is a sound SERVER that allows users to configure it alongside any sound daemon, be it Alsa or whatever.

The default setup for Ubuntu is to use ALSA with Pulse. You can set input sources (MIC, line-in, etc) with ALSA. You simply have to keep in mind that you will need a pulse control module for applications to interface with ALSA.

---

