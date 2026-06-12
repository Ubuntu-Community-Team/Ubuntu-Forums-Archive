---
title: "Convert to 3GP with FFmpeg?"
date: 2009-02-20
forum: Multimedia Software
---

### Post by fraser_m on 2009-02-20
My iPod died recently, so I've been looking for ways to watch my downloaded videos on my phone. I found a converter which works in Wine, but it was only a trial, so I was wondering how to convert a video in FFmpeg which'll be playable on my phone.

The codec details box in VLC says that one of the files has:

Stream 0:
Type: Video
Codec: mp4v
Resolution: 320x240
Framerate: 14.985000

Stream 1:
Type: Audio
Codec: mp4a
Channels: 2
Sample Rate: 44100 Hz
Bits per sample: 16
Bitrate: 705 kbps
AAC Extension: SBR

Help?

---

### Post by howefield on 2009-02-20
I know you specifically asked about ffmpeg, but have you looked at Handbrake, you might find it easier with some of the presets to convert to what you need,

---

### Post by fraser_m on 2009-02-20
I've tried handbrake, and can't find the scaling options...

---

### Post by andrew.46 on 2009-02-20
Hi,

Phones these days have all sorts of capabilities so you probably need to have a good look at the actual specs of your device. The base level of encoding is h263 video + amr_nb sound in a 3gp container but newer phones will do h264 + aac in an mp4 container. A big difference in quality possible...

Do you have a copy of FFmpeg available to you?

Andrew

---

