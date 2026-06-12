---
title: "Does rhythmbox support ape format?"
date: 2012-06-16
forum: Multimedia Software
---

### Post by AleCes on 2012-06-16
Hi there,

I'm running Rhythmbox on Ubuntu 12.04, I'm experiencing a buggy reproduction of ape format. Even after having installed the Monkeys' Audio codec and relevant needed packages from the deb-multimedia.org repository, the reproduction is still buggy.

Thanks for your help,

---

### Post by Yellow Pasque on 2012-06-16
rbox uses gstreamer backend, which supports ape through ffmpeg plugin:

```
# gst-inspect-0.10 | grep -i ape
taglib:  apev2mux: TagLib-based APEv2 Muxer
apetag:  apedemux: APE tag demuxer
ffmpeg:  ffdemux_ape: FFmpeg Monkey's Audio demuxer
ffmpeg:  ffdec_ape: FFmpeg Monkey's Audio decoder
```

---

### Post by AleCes on 2012-06-17
> **Temüjin said:**
> rbox uses gstreamer backend, which supports ape through ffmpeg plugin:

```
# gst-inspect-0.10 | grep -i ape
taglib:  apev2mux: TagLib-based APEv2 Muxer
apetag:  apedemux: APE tag demuxer
ffmpeg:  ffdemux_ape: FFmpeg Monkey's Audio demuxer
ffmpeg:  ffdec_ape: FFmpeg Monkey's Audio decoder
```

Hi Temüjin,
My output is:
```
ffmpeg:  ffdec_escape124: FFmpeg Escape 124 decoder
ffmpeg:  ffdec_ape: FFmpeg Monkey's Audio decoder
ffmpeg:  ffdemux_ape: FFmpeg Monkey's Audio demuxer
typefindfunctions: application/x-ape: ape
typefindfunctions: application/x-apetag: mp3, ape, mpc, wv
shapewipe:  shapewipe: Shape Wipe transition filter
apetag:  apedemux: APE tag demuxer
taglib:  apev2mux: TagLib-based APEv2 Muxer
apexsink:  apexsink: Apple AirPort Express Audio Sink
```Seems all right to me.

---

