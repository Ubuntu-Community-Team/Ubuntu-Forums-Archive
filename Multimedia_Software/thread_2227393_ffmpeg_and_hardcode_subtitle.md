---
title: "ffmpeg and hardcode subtitle"
date: 2014-06-01
forum: Multimedia Software
---

### Post by horhokokki on 2014-06-01
I have little problems with ffmpeg burning subtitles to 1080p video stream. The position of subtitles are middle of screen, but I managed to put them to right place with xy-coordinates, but subtitles are too small text, how can I add the text size?

this is my command:
ffmpeg -hide_banner -y -i "Pullman.mpeg" \
-filter_complex "[0:v][0:3]overlay=x=50:y=500[v]" -map [v] \
-map 0:1 -ab 256k  -r 25 "Pullmanwithsubs.mpeg"

What should I add there? textsize=32 or something like that I would like to have there, but .. how do I do that?

ffmpeg version N-63116-gbb9e511
built on May 31 2014 18:59:46 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
configuration:  --enable-gpl --enable-static --enable-shared --enable-libmp3lame  --enable-nonfree --enable-libx264 --enable-x11grab --enable-libvorbis  --enable-libv4l2 --enable-opengl --enable-libfaac --enable-avisynth  --enable-fontconfig --enable-version3 --enable-avresample  --enable-libtwolame --enable-avfilter --enable-libass
libavutil      52. 83.100 / 52. 83.100
libavcodec     55. 61.100 / 55. 61.100
libavformat    55. 37.102 / 55. 37.102
libavdevice    55. 13.101 / 55. 13.101
libavfilter     4.  5.100 /  4.  5.100
libavresample   1.  2.  0 /  1.  2.  0
libswscale      2.  6.100 /  2.  6.100
libswresample   0. 18.100 /  0. 18.100
libpostproc    52.  3.100 / 52.  3.100

---

### Post by FakeOutdoorsman on 2014-06-01
Please include the complete ffmpeg console output that results from your command. You can add the -t option, such as "-t 60", to encode a segment instead of the whole thing.

---

