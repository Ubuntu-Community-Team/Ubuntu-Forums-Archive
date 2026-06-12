---
title: "cannot play dvds on ubuntu 13.04"
date: 2013-05-13
forum: Multimedia Software
---

### Post by gusduenas on 2013-05-13
Hi I did a fresh install of ubuntu 13.04 on a dell latitude d520 averything went ok as espected but when I try to see a dvd it tells me at the menu wrong strem format, I tried to run this using the terminal and this is what I got.

~$ gst-launch-1.0 playbin uri=dvd:///dev/cdrom
Setting pipeline to PAUSED ...
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: NINEMONTHS_1
libdvdnav: DVD Serial Number: 2A3D5342
libdvdnav: DVD Title (Alternative): NINEMONTHS_1
libdvdnav: Unable to find map file '/home/jesusrivera/.dvdnav/NINEMONTHS_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000148
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000493
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000637
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000156e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00001712
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00028e61
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00029005
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0003a098
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0003a23c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00061065
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0006157f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0034549f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00345643
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
Pipeline is PREROLLING ...
Redistribute latency...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
ERROR: from element /GstPlayBin:playbin0/GstPlaySink:playsink/GstBin:abin/GstAutoAudioSink:audiosink/GstPulseSink:audiosink-actual-sink-pulse: The stream is in the wrong format.
Additional debug info:
gstaudiobasesink.c(1971): gst_audio_base_sink_render (): /GstPlayBin:playbin0/GstPlaySink:playsink/GstBin:abin/GstAutoAudioSink:audiosink/GstPulseSink:audiosink-actual-sink-pulse:
sink not negotiated.
Execution ended after 2838276 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
Setting pipeline to NULL ...
Freeing pipeline ...

what is this a bug? or is something that I can work around? please help me.

Thanks.

Gus.

---

### Post by bschedle on 2013-06-08
Hi,

 I have the same issue and see basically the same when I execute gst-launch-1.0 playbin uri=dvd:///dev/sr0. Except I have additional entries to the effect 
                  libdvdnav: Language 'en' not found, using 'ja' instead
                  libdvdnav: Menu Languages available: ja
 Also, I have no permissions to view the DVD; I cannot cd to the folder. 

 Please tell if you have been able to resolve.

 I also followed the steps in [Richard Worloma]("https://www.google.com/search?q=ubuntu+13.04+cannot+play+dvd&biw=1175&bih=890&tbs=ppl_ids:--117550624644028583374-,ppl_nps:Richard+Worloma,ppl_aut:1") post on Liberiangeek.net but no joy.

Thank you.

---

