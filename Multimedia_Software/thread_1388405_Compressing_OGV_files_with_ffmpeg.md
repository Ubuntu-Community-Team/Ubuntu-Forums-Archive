---
title: "Compressing OGV files with ffmpeg"
date: 2010-01-23
forum: Multimedia Software
---

### Post by rocketssss on 2010-01-23
Hello! I am converting some AVI videos into OGV Theora files for internet distribution. Because the source files are variable bitrate, I had some problems getting the audio/video sync working, but I fixed that by encoding the audio and video separately, then combining them:

```
ffmpeg -i $FileIn -an -vcodec libtheora $TempVideo
ffmpeg -i $FileIn -vn -acodec libvorbis $TempAudio
ffmpeg -i $TempAudio -i $TempVideo $Final
```

This produces a lossless OGV file, but I want to compress the result further. However, I'm having trouble making ffmpeg's various quality settings play nice. The bitrate feature clearly isn't working, as these commands:
```
ffmpeg -i temp.ogg -i temp.ogv out.ogv
ffmpeg -i temp.ogg -i temp.ogv -b 50k out2.ogv
ffmpeg -i temp.ogg -i temp.ogv -b 100k out3.ogv

```
All result in similarly-sized files (about 45 MB for a 4-min, 1280*768 video). I figured that since it was Variable Bit Rate media I should try the -qscale option:
```
ffmpeg -i temp.ogg -i temp.ogv -qscale 5 out4.ogv
ffmpeg -i temp.ogg -i temp.ogv -qscale 1 out5.ogv
ffmpeg -i temp.ogg -i temp.ogv -qscale 10 out6.ogv
```

This sort of worked but the results were even BIGGER than the original! I know that it is possible to get much smaller files using ffmpeg2theora, for this command shrinks a 50MB OGV file to roughly 12MB with very little loss in quality:
```
ffmpeg2theora $MiddleOut -v 5 -a 2 --optimize -o $FileOut
```

However, the ffmpeg2theora messes up my audio/video sync even when the source OGV was good. Am I just using the wrong options for ffmpeg?

Any help would be GREATLY appreciated!
Thanks.

---

