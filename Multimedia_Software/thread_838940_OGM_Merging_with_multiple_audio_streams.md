---
title: "OGM Merging with multiple audio streams"
date: 2008-06-24
forum: Multimedia Software
---

### Post by pdoconnell on 2008-06-24
So I have some rips of the Lord of the Rings movies that I was only able to get ripped in ogm with multiple audio streams (4 total including 3 commentary tracks). I haven't been able to find any software that I can use to merge the multiple ogm files though, especially one that would allow me to keep all the audio tracks. Does anyone have any suggestions, or even a converter to say mp4 that would retain all of the audio tracks?

---

### Post by eye208 on 2008-06-24
Muxing from OGM to MP4 eventually requires transcoding the streams to MPEG formats, so it is not recommended. You can put the video and all the audio tracks into a single OGM (using ogmmerge from the ogmtools package) or Matroska file (using mkvtoolnix/mkvtoolnix-gui).

---

