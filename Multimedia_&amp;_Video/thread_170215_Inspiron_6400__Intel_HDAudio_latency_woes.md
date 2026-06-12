---
title: "Inspiron 6400 / Intel HDAudio latency woes"
date: 2006-05-04
forum: Multimedia &amp; Video
---

### Post by mimp on 2006-05-04
Ok, just got a shiny new laptop and have been trying to get it running at acceptable latencies.
Everything works with the latest dapper 686 kernel but at a pretty horrific latency (35ms is the lowest I can go without copious xruns and even that isn't very reliable)
Enabling realtime operation for jack results in xruns regardless of latency settings, so something seems wrong there too.

Anyway, thought I’d have a go at compiling a vanilla kernel with the realtime pre-emption patch -If I follow the ubuntu studio dapper howto exactly (ie same kernel/patch versions) it works, but if I use a more recent kernel and patch I wind up unable to boot.

The problem is, the old kernel doesn't like my soundcard much - it works wonderfully with jack’s real-time option at very low latencies (sub 5ms) but the headphone jack doesn't function, and my built-in laptop speakers aren't really up to monitoring.
Building and installing the latest alsa drivers fixes the problem but also messes up the low latency operation - real-time suddenly means xruns again and the lowest latency I can get reliably without it is about 20ms

Just wondering if I’ve missed some option when compiling the new alsa which means its not optimised or cooperating with the patched kernel or something (I just did a standard ./configure make make install), or if support for Intel HD audio is just a bit buggy right now or what.. have spent ages on this and don't know weather I should just give up and try again in a month or so..
Any insight anyone has would be greatly appreciated.

---

