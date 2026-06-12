---
title: "Cluster encoding DVD::RIP TV cap"
date: 2011-08-05
forum: Multimedia Software
---

### Post by lible on 2011-08-05
hi

I'm looking to setup a cluster encoding system as described here. 
[http://www.exit1.org/dvdrip/doc/cluster.cipp](http://www.exit1.org/dvdrip/doc/cluster.cipp)

The issue ive come across is that the format which i'm attempting to transcode is not natively supported by dvd:rip (which is *.ts transport stream/mt2s/mp4). Ive read that the program transcode is capable of such a thing but unfortunately i'm not as knowledgeable in batch/cli as i would like to be. Would anyone know of a means of accomplishing the cluster mode that dvd::rip gui offers which supports .ts files and you don't have to be an engineer to figure out.
 
transcode example
[http://www.transcoding.org/transcode?Examples/Cluster_Batch_Encoding](http://www.transcoding.org/transcode?Examples/Cluster_Batch_Encoding)


Thanks

---

### Post by BicyclerBoy on 2011-08-05
mpeg4 ts is a container.
You may not need to transcode but just re-mux your existing streams into a new container.

But mpeg4 ts is normally only supported with mpeg2 & mpeg4/10 (H264) video formats, the audio is normally AAC.

The best app for this is ffmpeg or possibly tsmuxer.
There is a GUI for ffmpeg (WinFF) but it does not seem to have a preset for .ts output container..

AFAIK dvd:rip & transcode are not actively maintained.

---

### Post by lible on 2011-08-05
Thanks for you reply BicyclerBoy.

I'm quite new to all of this but in a nutshell I'm looking to crop, resize, and convert videos to XviD in the minimal amount of time, hence my interest in the cluster.currently ive been using staxrip in windows but the amount of time it's taking to encode is really long for my purposes.hope this clarifies my question a little more.

---

### Post by BicyclerBoy on 2011-08-05
You do need to transcode to resize etc...

AFAIK XviD is the ms mpeg4-asp profile..not very good compared to H264.
I don't think XviD is preferred codec inside ts container..
I would not use XviD unless you you have no other choice.

XviD is commonly supported in newer DVD players etc ...seems like a stop-gap measure.

All new TVs should play H264 in .ts stream as the world is using H264 with dvb-t/t2/s/s2 broadcast.

All mpeg4 video encoding require a lot of CPU power..

A core2 duo will only manage almost real-time encoding h264 (HD resolutions).

ffmpeg & x264 are arguably the best options but cli only.

A fast intel CPU with lots of RAM could encode H264 (HD) maybe 6x to 10x real time..

---

### Post by lible on 2011-08-05
Guess ill just have to look into getting a better PC. thanks for the info

---

