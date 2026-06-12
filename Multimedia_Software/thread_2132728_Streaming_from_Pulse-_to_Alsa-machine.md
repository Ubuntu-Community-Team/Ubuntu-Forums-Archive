---
title: "Streaming from Pulse- to Alsa-machine"
date: 2013-04-05
forum: Multimedia Software
---

### Post by hampsterstory on 2013-04-05
Hello,

I'm running Ubuntu 12.04 and I want to stream Audio from the Pulse-server of that machine over my Wifi to another machine. The remote machine is not able to run the Pulseserver (lack of processing power), only Alsa is present.

I think the problem can be divided into 3 parts:

[LIST=1]
[*]Setting up a virtual device for streaming at the Pulseaudio-side (Server) 
[*]Stream Audio to the Alsa-device 
[*]Output Audio at the Alsa-side (Remote) 
[/LIST]

I'm aware that this is a rather strange request, but I hope somebody has a good Idea how this can be done.

---

### Post by CatKiller on 2013-04-06
If you don't want to run Pulse on the client (although it doesn't necessarily use much by way of resources), have you considered running a DLNA server instead? Personally, I use Mediatomb for streaming to the PS3 but there are others available. Obviously only a solution if you're wanting to stream media rather than generic audio.

---

