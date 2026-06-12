---
title: "realtime streaming of mic input over LAN?"
date: 2010-07-21
forum: Multimedia Software
---

### Post by prupert on 2010-07-21
Hi

I have investigated loads and loads of options and haven't really yet come across what I need.

I wish to stream the microphone input from a PC using Lucid to another PC also using Lucid on the same network. I don't care about the quality, however, latency is really important. I hope to use it to monitor the cries of my baby daughter, so the lower the latency the better.

I have tired various options:
- FFserver and FFmpeg - latency of over 30 seconds :(
- VLC - couldn't get it to work with my mic and maxes out the CPU
- ssh server 'cat /dev/dsp > /dev/dsp' - latency of around 5 seconds by audio keeps breaking up with huge delays
- icecast2 and darkice - latency of around 7 seconds but no audio breakups

I've been reading on maybe using PulseAudio to stream the input, but I am not sure if it will work or not...

Does anyone have any suggestions for how to get near real-time streaming audio? As I said, it is the realtime, not the quality that is important...

Cheers

---

### Post by aeiah on 2010-07-21
id go with pulseaudio. i actually looked into this yesterday as a quick and easy way to stream music (but my wireless is flakey, and it wasn't worth the effort in my case, i just used mt-daapd in the end).

this may help:
[http://www.unixmen.com/linux-tutorials/582-stream-music-wirelessely-using-pulseaudio-server-device-chooser](http://www.unixmen.com/linux-tutorials/582-stream-music-wirelessely-using-pulseaudio-server-device-chooser)

if you have the microphone producing sound out of the speakers locally, you can just do exactly as they do and treat it as music. from my tests it had pretty much zero lag. should be even better if you have a wired network.

---

### Post by prupert on 2010-07-21
Bugger, Pulseaudio works - but it seems to recquire a powerful processor and a fast network to stream audio (as I guess it is streaming uncompressed audio). It worked, for a little bit and then stopped.

Poop...

Thanks for the suggestion though...

---

