---
title: "Audio in tvtime with pulseaudio"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by flying_surprise on 2008-03-13
I have a Pinnacle Hybrid Pro Stick Analog/Digital tv tuner for USB. Before I installe pulseaudio (which has solved all other of my audio problems in ubuntu), i did like this to get tv audio in tvtime:

```
sox -r 48000 -w -c 2 -t ossdsp /dev/dsp -t ossdsp /dev/dsp
```

And I had TV audio! But after I installed pulseaudio this doesn't work anymore. Not even if I stop pulseaudio (/etc/init.d/pulseaudio stop).

I had an another idea using gst-launch for forwarding sound instead:

```
gst-launch -v pulsesrc ! audioresample ! audio/x-raw-int,width=16,depth=16,rate=48000,channels=2 ! pulsesink
```

This gives sound, but the quality is horrible. It's some kind of "vibrato" effect which is very annoying. Is there any way to get clear crisp sound from my tv tuner with gst-launch?

Thanks!

---

### Post by davidlm on 2008-05-03
Do you try with padsp? in this page [http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup") i find: 
> 
To run applications that support the OSS API for audio playback (/dev/dsp) on top of PulseAudio you can use the tool padsp that is part of the PulseAudio distribution.

```
padsp sox foo.wav -t ossdsp /dev/dsp
```

In your case:

> padsp sox -r 48000 -w -c 2 -t ossdsp /dev/dsp -t ossdsp /dev/dsp

---

