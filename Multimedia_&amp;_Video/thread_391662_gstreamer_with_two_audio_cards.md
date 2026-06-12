---
title: "gstreamer with two audio cards"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by otc242 on 2007-03-23
I am trying to use gstreamer with saa7134 tv card (gigabyte, has no audio jack, so it's dma sound only). Video is working fine, but there is no sound.

Here is what i tried (sound example): 

```
gst-launch-0.10 alsasrc device="hw:1" ! "audio/x-raw-int,width=16,depth=16,rate=32000,channels=2" ! alsasink -v

```

and the output:

```
Setting pipeline to PAUSED ...
/pipeline0/alsasrc0.src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)32000, channels=(int)2
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: audioclock0
/pipeline0/capsfilter0.src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)32000, channels=(int)2
/pipeline0/capsfilter0.sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)32000, channels=(int)2
/pipeline0/alsasink0.sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)32000, channels=(int)2

```

hints, anyone?

---

### Post by otc242 on 2007-03-28
... i found the solution:

```
gst-launch-0.10 alsasrc device="hw:1" ! "audio/x-raw-int,width=16,depth=16,rate=32000,channels=2" ! osssink sync=false

```

trick is in the sync=false; it works also with alsasink instead of osssink, but the audio delay is noticable (grows in time).

the complete script to having sound with saa7134 (s/w sound) and tvtime that use now is:

```
gst-launch-0.10 alsasrc device="hw:1" ! "audio/x-raw-int,width=16,depth=16,rate=32000,channels=2" ! osssink sync=false &
tvtime
killall gst-launch-0.10
```

hope this helps someone :)

---

