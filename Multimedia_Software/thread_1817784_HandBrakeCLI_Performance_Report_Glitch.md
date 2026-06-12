---
title: "HandBrakeCLI Performance Report Glitch?"
date: 2011-08-03
forum: Multimedia Software
---

### Post by Drak3 on 2011-08-03
Hello,

So, I recently built myself a simple multi-purpose server, with one of those uses being handbrake dvd backup.  Everything works as i would have expected it, with one exception:  the reported cpu usage while encoding.  (everything was while using the default settings)

While encoding, the CPU usage as reported by "top" and the system monitor is <1/3 of being fully used.  Also, the temperature load was about what i would expect for near full utilization)

The thing is, its running *faster* than i would have expected.  (I'm comparing it to my dual core 2.8GHz intel laptop.  the server has an AMD 1100t (6x3.3GHz) )  While it should have been ~3.5x faster, it was closer to 5x faster.  not wholly unexpected, but still notable.

Ive attached some screenshots to show the encode times of both, and the performance use of the server (the laptop was full on using both cores)

SO, my question is this:  has anyone run into this before?  if so, do you know a way to have the OS properly report the usage, if that is what isn't being reported properly.

System Monitor
[IMG]http://db.tt/gXwJTZb[/IMG]

top
[http://db.tt/fdQte7h](http://db.tt/fdQte7h)

temps
[http://db.tt/S2Ia5Z1](http://db.tt/S2Ia5Z1)

Ubuntu ETA
[http://db.tt/k0VLl20](http://db.tt/k0VLl20)

OS X ETA
[http://db.tt/dj3gfxs](http://db.tt/dj3gfxs)


{edit}  it appears the forum only embeds the first image.  the links should work though.

---

