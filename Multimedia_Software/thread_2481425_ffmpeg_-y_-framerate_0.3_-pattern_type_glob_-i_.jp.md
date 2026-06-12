---
title: "ffmpeg -y -framerate 0.3 -pattern_type glob -i *.jpg"
date: 2022-11-29
forum: Multimedia Software
---

### Post by jari169 on 2022-11-29
how repair script
ffmpeg -y -framerate 0.3 -pattern_type glob -i *.jpg -c:v libx264 -r 30 -pix_fmt yuv420p road_87.mp4



[image2 @ 0x55eefe95e7c0] Could not open file : *.jpg
[image2 @ 0x55eefe95e7c0] Could not find codec parameters for stream 0 (Video: mjpeg, none(bt470bg/unknown/unknown)): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, image2, from '*.jpg':

---

### Post by DVoid on 2022-11-29
> **jari169 said:**
> how repair script
ffmpeg -y -framerate 0.3 -pattern_type glob -i *.jpg -c:v libx264 -r 30 -pix_fmt yuv420p road_87.mp4



[image2 @ 0x55eefe95e7c0] Could not open file : *.jpg
[image2 @ 0x55eefe95e7c0] Could not find codec parameters for stream 0 (Video: mjpeg, none(bt470bg/unknown/unknown)): unspecified size
Consider increasing the value for the 'analyzeduration' and 'probesize' options
Input #0, image2, from '*.jpg':

Hi Jari. If I recall correctly, when using glob you might need to put *.jpg in single quotes. so try.:

ffmpeg -y -framerate 0.3 -pattern_type glob -i '*.jpg' -c:v libx264 -r 30 -pix_fmt yuv420p road_87.mp4

---

### Post by jari169 on 2022-11-29
just keeps giving the same error code..

I installed the package ffmpeg and imagemagick, works on another server

---

### Post by DVoid on 2022-12-01
> **jari169 said:**
> just keeps giving the same error code..

I installed the package ffmpeg and imagemagick, works on another server

That's very strange then. Is it possible there's a jpg file on that server that is corrupted? Maybe compare file sizes to the other server, checking for 0 byte files or other signs of file truncation?

---

