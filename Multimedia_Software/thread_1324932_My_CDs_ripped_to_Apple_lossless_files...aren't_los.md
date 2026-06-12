---
title: "My CDs ripped to Apple lossless files...aren't lossless!"
date: 2009-11-13
forum: Multimedia Software
---

### Post by spasticteapot on 2009-11-13
I'm trying to rip my music collection to ALAC (.m4a) format using Rhythmbox, but the files produced don't sound right and are much to small - a file that was 18mb as a FLAC file was only 3mb when ripped in "apple lossless" format. What's going on?

---

### Post by mc4man on 2009-11-13
What are you expecting rhythmbox (gstreamer) to use to encode to alac?

ffmpeg can encode alac, but I wouldn't expect gstreamer to do so.

(myself use NeroAac/atomicparsley in rubyripper

---

### Post by VertexPusher on 2009-11-13
> **spasticteapot said:**
> I'm trying to rip my music collection to ALAC (.m4a) format using Rhythmbox, but the files produced don't sound right and are much to small - a file that was 18mb as a FLAC file was only 3mb when ripped in "apple lossless" format. What's going on?
.m4a does not mean ALAC. It means MP4 Audio.

MP4 files *can* contain ALAC streams, but they can also contain AAC (or even MP3). Rhythmbox probably encoded to AAC.

---

