---
title: "FFMpeg output error"
date: 2015-11-16
forum: Multimedia Software
---

### Post by mavik1 on 2015-11-16
Hello,

Our program will capture the raw data and put it in file. 
This is the statement in program.

sprintf(commandLine,  "ffmpeg -metadata title=%s  -metadata artist=%s  -metadata genre=%s  -metadata comment=\"%s\"  -metadata album=\"%s\" -i %s-0000.mp4 -acodec  copy -vcodec copy  video.mp4 2>**NULL **\n", TITLE, ARTIST,GENRE, month_time, location_name, aviFileName);

NULL file contents are:

ffmpeg version 2.8.1 Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.9.2 (Ubuntu/Linaro 4.9.2-10ubuntu13)
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame  --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora  --enable-libvorbis --enable-libx264 --enable-libxvid --enable-nonfree  --enable-postproc --enable-version3 --enable-x11grab --enable-shared  --enable-pic
  libavutil      54. 31.100 / 54. 31.100
  libavcodec     56. 60.100 / 56. 60.100
  libavformat    56. 40.101 / 56. 40.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 40.101 /  5. 40.101
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  2.101 /  1.  2.101
  libpostproc    53.  3.100 / 53.  3.100
Option  metadata (add metadata) cannot be applied to input file test-0000.mp4  -- you are trying to apply an input option to an output file or vice  versa. Move this option before the file it belongs to.
Error parsing options for input file test-0000.mp4.
Error opening input files: Invalid argument

 Same program  worked before. 
Now, it's not. Unable to understand what is the problem.

Thank you,
Answers Appreciated.

---

### Post by FakeOutdoorsman on 2015-11-16
Move your medatada options from the input to the output as indicated by your console output. Option placement matters:

```
ffmpeg [global options] [input options] -i input [output options] output
```

---

