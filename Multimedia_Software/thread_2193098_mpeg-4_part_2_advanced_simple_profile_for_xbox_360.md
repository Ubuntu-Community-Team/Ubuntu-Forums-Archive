---
title: "mpeg-4 part 2 advanced simple profile for xbox 360"
date: 2013-12-11
forum: Multimedia Software
---

### Post by aarons6 on 2013-12-11
i have a bunch of avi files, the ones that work are all mpeg-4 part 2 (advanced simple profile) with mp3 audio.

what im trying to do is re-encode the ones that dont.
i figured out i can convert to h.264 with a mp4 container and the xbox should play them
but i want them to be mpeg-4 part 2 in a avi container.

but i cant figure out how to make avconv do mpeg-4 part 2 in a avi container.

i can make it use libx264 in avi container.. but im not sure if the quality is the same as if i did mpeg-4 part 2..




i dont want to make the files h.264 in a mp4 container as the quality sucks and the files are larger.


what is really weird is i have some avi files that already are mpeg-4 part 2 and they dont play either.. they should tho.. 
this whole thing is kind of confusing and when i look online i get 100 answers all different.


edit, so i just found this.
i installed libavcodec-extra-53 

This package is an enhancement to the regular libavcodec library package.
This package contains the following additional codecs.


 * OpenCORE Adaptive Multi-Rate (AMR) Narrow-Band (Encoder/Decoder)
 * OpenCORE Adaptive Multi-Rate (AMR) Wide-Band (Decoder)
 * Android VisualOn AAC (Encoder)
 * Android VisualOn Adaptive Multi-Rate (AMR) Wide-Band (Encoder)
 * OpenCV filtering
 * Dirac decoding support via libdirac
 * MP3 encoding with liblame
 * H.264 encoding via libx264
 * MPEG4 Part 2 encoding via libxvidcore


ok, so i tried avconv -vcodec libxvidcore and

  Metadata:
    artist          : TSV Productions
    IAS1            : English
  Duration: 00:37:14.56, start: 0.000000, bitrate: 1676 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 576x432 [PAR 1:1 DAR 4:3], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 131 kb/s
    Stream #0.2: Audio: mp3, 48000 Hz, stereo, s16, 132 kb/s
Unknown encoder 'libxvidcore'
Press Enter to Continue


it should work? but it doesnt..

---

