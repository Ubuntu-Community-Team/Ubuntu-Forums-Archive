---
title: "High latency on Pulseaudio network stream"
date: 2014-03-18
forum: Multimedia Software
---

### Post by Ranko Kohime on 2014-03-18
Ok, here's my situation.  I'm using Linco and Netcat on a Windows 7 box to stream audio out to my laptop, and the laptop is receiving the audio with Netcat and pacat.

Now while I realize that there will of course be latency with such a setup, I wasn't quite anticipating the full 2 second delay that I'm getting.  Starting pacat with -vv shows my latency bouncing between 1.9-2.1m usecs, or 1.9-2.1 seconds.  Watching a video on the Win7 box shows the latency to be about that on the eye counter.

Is there a way to figure out where in the pipeline all this latency is, and perhaps reducing it to something a little more manageable?  (I'm thinking something more like 400-500 msecs, but less is better, of course)

---

### Post by Ranko Kohime on 2014-03-18
Well, I figured it out.  :D

Apparently pacat starts with a high latency by default, and you have to cut it down with the --latency(-msec) switch.

---

