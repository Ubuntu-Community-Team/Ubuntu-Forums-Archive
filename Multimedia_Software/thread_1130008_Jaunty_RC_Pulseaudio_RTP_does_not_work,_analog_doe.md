---
title: "Jaunty RC: Pulseaudio RTP does not work, analog does"
date: 2009-04-19
forum: Multimedia Software
---

### Post by curvedinfinity on 2009-04-19
I have a XPS M1330 laptop, with sigmatel STAC9228 audio. I just upgraded to Jaunty RC, and all of my sound stopped working (including log-in sound). I've double checked in multiple applications that nothing is muted. After a little digging, I have found that OSS works 100%, but I'd prefer to keep Pulseaudio. Pulseaudio is showing strange symptoms:

In the Pulseaudio Manager, I can use the sample cache tab to play some sound. Using the Pulseaudio Volume Control to view sound levels, I have noticed that when RTP is selected as the output for the sample cache, I can see the sound playing, but nothing is reaching the speakers. When I select the analog output channel in the sample cache, sound actually plays. In both cases, only .wav files play sound -- .oggs create no sound and no level on the volume control.

Does anyone know what's happening? It seems as though if I switch to analog pulseaudio output, my problem will be "fixed", but I'd rather fix it properly.

---

### Post by curvedinfinity on 2009-04-19
I have temporarily defeated the problem by turning off RTP in Pulseaudio Preferences.

One problem I am still noticing is that applications that use sound take a long time to start up. The normal volume control takes a good 20-30 seconds to start up.

---

