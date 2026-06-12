---
title: "Merge/Join Mpeg-4 files?"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by montgoss on 2007-03-11
Anyone know how to merge/join two (or more) MPEG-4 files?

I tried just cat'ing them together, but that doesn't work.  Well, it produces a new file that is the right size for merging them together.  But playback of the file just ends where the first of the two files ends.  Maybe there is some command I could run against this cat'ed file that would fix the headers or whatever so that the video players realize it is now longer?

I tried with cat and ffmpeg:
```
cat Carnivale-S2E01-Los_Moscos_part1.m4v Carnivale-S2E01-Los_Moscos_part2.m4v > Carnivale-S2E01-Los_Moscos.m4v
```
```
ffmpeg -i Carnivale-S2E01-Los_Moscos.m4v -f m4v -vcodec copy -acodec copy Carnivale-S2E01-Los_Moscos_merged.m4v
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Mar  8 2007 06:14:12, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Carnivale-S2E01-Los_Moscos.m4v':
  Duration: 00:25:28.4, start: 0.000000, bitrate: 1312 kb/s
  Stream #0.0(und): Video: mpeg4, yuv420p, 480x270, 29.97 fps(r)
  Stream #0.1(und): Audio: aac, 48000 Hz, stereo
Output #0, m4v, to 'Carnivale-S2E01-Los_Moscos_merged.m4v':
  Stream #0.0: Video: mpeg4, yuv420p, 480x270, q=2-31, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=45808 q=0.0 Lsize=  128169kB time=1528.2 bitrate= 687.1kbits/s    
video:97312kB audio:30857kB global headers:0kB muxing overhead 0.000000%
```
As you can see, ffmpeg thinks the cat'ed input file is only 00:25:28.4 long instead of the ~51 minutes it should be.  And playback of the merged file ends at 00:25:28.

I tried similar methods with mencoder with worse results.   Anyone know how to do this?

---

### Post by chewearn on 2007-03-12
Not sure if this will work on mpeg-4 files, but I have used Avidemux to join two avi (xvid+mp3) files.

---

### Post by montgoss on 2007-03-12
I tried Avidemux to join regular mpeg-2 files.  It screwed up the sound sync horribly.  I guess I didn't try it with mpeg-4 though.

One note of clarification: the MPEG-4 I'm referring to isn't Divx or Xvid.  I believe those are MPEG-4 part 2.  I guess just MPEG-4 would be part 1.  Basically, it's video that would play on an iPod.  So, MPEG-4 video with AAC audio.

---

