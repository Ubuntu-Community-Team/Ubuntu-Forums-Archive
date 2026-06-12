---
title: "Pulseaudio, did i grasp the idea?"
date: 2009-08-29
forum: Multimedia Software
---

### Post by BramWillemsen on 2009-08-29
Hello,

This question comes forth out of my confusion with the different sound systems used in Linux. I've read through some documentation and i'd like to find out if my conclusions are right. If right, this could be a useful summary for other newcomers (like me) that are confused about the sound system.

So basically, ALSA is the base of the sound system in modern linux installations. It replaces the old OSS drivers. ALSA has a kernel layer that takes care of the communication with the hardware and a layer that provides the API for the software to communicate with.

The goal of pulseaudio is to let all the sound streams go through it. Some programs directly contact ALSA. In order to also send these sound streams through pulseaudio you can make a virtual device in ALSA. (see [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) under 'Third Party Applications', make pulse the default output device). All the sound streams that directly reach ALSA are rerouted to pulse this way. 

All the sound streams will go through pulse this way, either directly or from the redirect in ALSA. Pulse can manage all the soundstreams this way. The result is sent to ALSA again, which contacts the hardware for the real sound output.

Is this a good summary of the basic pulse functionality ?

kind regards, Bram

edit: i don't know if any of the ALSA sound settings still apply when the sound is rerouted to pulseaudio. Say you change the volume in ALSA, would the resulting sound be affected?

---

