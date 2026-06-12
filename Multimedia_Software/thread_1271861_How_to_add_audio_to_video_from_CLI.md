---
title: "How to add audio to video from CLI?"
date: 2009-09-21
forum: Multimedia Software
---

### Post by jakev383 on 2009-09-21
I currently use ffmpeg to convert an mpeg4 avi file to a quicktime/mov file (h264 and aac).
I'm not all that familiar with ffmpeg, so I would like to know if there was a way to add an audio track to the avi as I convert it to quicktime? I record the audio in Audacity, so I can export any of the popular formats. I do not have any audio on the avi file, so I am not concerned with retaining any audio from the original movie or anything.
Any help is appreciated. Current, here is the command I use to convert the movie ($1 is the name of the file as supplied by the command line - this is a script I run):

```

ffmpeg -i ~/$1.avi -vcodec h264 -sameq -acodec aac ~/$1.mov

```

Thanks in advance!

---

### Post by FakeOutdoorsman on 2009-09-21
Yes, you can add audio as you convert with FFmpeg.  If your video source contains no audio, then you can simpily just add another input file that contains your audio.  Here's an example using your command:
```
ffmpeg -i ~/$1.avi -i audio.wav -vcodec h264 -acodec aac ~/$1.mov
```
Also, I could be wrong, but I don't think *sameq* is a valid option for the h264 encoder.  If your video input contains audio that you don't want, then you will need to use the map option to tell FFmpeg what to encode:
```
ffmpeg -i input.avi -i input.mp3 -map 0:0 -map 1:0 -vcodec libx264 -vpre hq -crf 22 -threads 0 -acodec libfaac -ab 128k -ac 2 output.mp4
```
The *-map 0:0* option tells FFmpeg to only encode the first input:first stream, and *-map 1:0* corresponds to second input:first stream.  A much better explaination can be found at [Using ffmpeg to manipulate audio and video files: Mapping Channels](http://howto-pages.org/ffmpeg/#map).

In my example above, you may see a bunch of other commands which bring out the full potential of encoding to h264.  However, you will need to compile FFmpeg and x264 to do this.  It's not too hard and definately worth it if you want to see a huge increase in video quality:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Make sure to also read the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for a good introduction to encoding to h264 video.

---

### Post by jakev383 on 2009-09-21
Thanks for the information. I'll definitely sit down after dinner and read through the links you gave me.
Be well!

---

