---
title: "Monitor line-in with jack and pulseaudio"
date: 2014-12-28
forum: Multimedia Software
---

### Post by Diomas on 2014-12-28
Hello, 

I'm trying to listen my line-in signal from guitar together with other sounds from rhythmbox, totem etc.

I tried this loopback solution:
```
pactl load-module module-loopback latency_msec=1
```

But it doesn't work for me cause I can hear a huge lag about 1/3 of a second (not sure why latency_msec parameter was ignored)


So I installed Jack with pulseaudio-module-jack and added these lines to [FONT=monospace]/etc/pulse/default.pa:[/FONT]
```
load-module module-jack-sink
load-module module-jack-source
```
Now I still can hear application sounds and I still can see input volume "levels" jumping in Sound Settings > Input > Jack source (PulseAudio JACK Source). But I still can't hear anything from line-in.

This is what I see in jack connections by default:

[IMG]http://i.imgur.com/6HQtKRh.png[/IMG]

I tried to connect some items randomly, but I can't hear line-in anyhow and I don't really understand what is what here.

So my questions are:
Where are my line-in and mic here in the picture?
Why do I have 8 playbacks (what does it mean)?
What do I do to hear my line-in signal in my speakers?

 I have a simple built-in soundcard, ubuntu 14.04 (if this info is relevant for my questions)

---

