---
title: "Pulseaudio over network acting flaky"
date: 2014-11-23
forum: Multimedia Software
---

### Post by BatteryKing on 2014-11-23
I have been trying to use Pulseaudio over the network between two Ubuntu 14.04LTS systems with limited success.  While I have managed to get the audio to stop breaking up like it was in the beginning, there are other unresolved issues.  Specifically two things keep happening:
1. After a certain amount of time, anywhere from minutes to hours, the program playing audio over the network has its time index freeze.  For a pure audio player the time index of the current audio stream stops.  If say I have multiple songs queued up to play, it will never advance to the next track.  If I am playing a video, the video will freeze up while associated audio will keep playing.  This happens across multiple applications.
2. The list of available network audio devices in the client pulseaudio manager will randomly show or not show devices.  Sometimes I will see no devices, but most often I will some some devices on the server and not others.  It is just kind of wonky.
3. Using Rhythmbox with networked audio device will cause crash messages to appear for Rhythmbox, especially on startup.

One thing I did to resolve the audio breaking up issues when I initially tried this is to make the following changes to the /etc/pulse/daemon.conf:
default-fragments = 4
default-fragment-size-msec = 20

I tried various other settings for these and got various wonky results going either direction of these values.  One thing I picked up on is the total of (default-fragments) * (default-fragment-size-msec) seems to need to be under 100ms, which I suppose makes sense if you are trying to not have excessive latency.  What these settings actually do I only have a vague idea at the moment due to limited time to dig.  (I keep I should have time this weekend and then stuff happens.)

The networking environment I am primarily doing this over is a 1st gen Core-i7 desktop and a 2nd gen Core-i5 talking over a switched 1 Gb/s wired Ethernet network with all actively utilized hardware in the same room.

Anybody have ideas on how to make this work reliably or is this one of those "why don't you rewrite Pulseaudio yourself" kinds of things if I actually want it to work?

---

