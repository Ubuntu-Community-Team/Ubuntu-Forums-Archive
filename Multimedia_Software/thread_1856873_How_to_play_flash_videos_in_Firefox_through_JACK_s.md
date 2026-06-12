---
title: "How to play flash videos in Firefox through JACK sound server"
date: 2011-10-09
forum: Multimedia Software
---

### Post by Jarks on 2011-10-09
Kubuntu 11.04 on HP ProBook 4525s:

Hi,
I needed to connect my keyboards to my notebook. First I couldn't hear anything. So I tried to load the loopback module to the Pulse. (pactl load-module module-loopback). But it had awful latency even with the latency_msec=1 parameter.

Then I installed QJackCt and JACK sound server. Made connection between system/capture and system/playback and it works fine. I can hear what I play but can't hear anything else. In Clementine there is an output module Audio Sink (Jack). When I choose it, Clementine plays through JACK.

The thing is that there is no sound from any other programs. For instance Firefox/Flash videos from Youtube and so on. Here are my questions:

1. Is there a way how to play *everything* through JACK, or do I need a special module for each program?
    (I have pulseaudio-module-jack installed but don't know what to do with it.)

2. If I need to do something special: How to play flash videos from Firefox through JACK?
    (I found some notes about libflashsupport package but I can't see it in repositories.)

Thanks.

---

