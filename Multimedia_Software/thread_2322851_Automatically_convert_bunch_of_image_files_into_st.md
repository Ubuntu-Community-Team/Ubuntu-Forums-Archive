---
title: "Automatically convert bunch of image files into still-image video files."
date: 2016-04-30
forum: Multimedia Software
---

### Post by AnCapGamer on 2016-04-30
I have about 130 .png files that I've generated using GIMP - they're basically introductory slides that I'm going to be putting in front of a bunch of music videos that state the title, artist, etc, for the benefit of my audience before the video plays - and I need to convert them from image files into 10-second video files.

Now, if all else fails I CAN use OpenShot to convert them by manually importing each image file, dragging it down into the video stream, manually selecting all my various export options, and exporting the image into a .mp4 file - and if need be I'm willing to do so.

HOWEVER, doing all of that by hand for 130 slides would probably take me 2 or 3 DAYS just from all the clicking, dragging, selecting, and waiting while each file transcodes.

So, I'm wondering: is there any way that I can automate this process? I doubt that there's some line in Terminal that I could just type in, but if there's a video editing program that supports pre-set configuratons and batch-loading of files or job queues, it'd REALLY help me a lot.

---

### Post by neu2buntu on 2016-05-01
I think this should be possible using ffmpeg / avconv .  It seems tho that you will need to have the image files named in a numbered sequence e.g 0001.png. .. 0002.png etc to have any order in the video sequence, otherwise it will work on alphabetical order. See this link for an example [http://hamelot.io/visualization/using-ffmpeg-to-convert-a-set-of-images-into-a-video/](http://hamelot.io/visualization/using-ffmpeg-to-convert-a-set-of-images-into-a-video/)

---

### Post by FakeOutdoorsman on 2016-05-01
FFmpeg development is very active, so unless you're using 15.10 or newer I recommend [downloading a recent ffmpeg binary](http://johnvansickle.com/ffmpeg/) or use [mc3man's PPA for 14.04 users](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).

Then you can use a bash for loop. Untested H.264 example:
```

mkdir output
for f in *.png; do ffmpeg -framerate 13 -i "$f" -c:v libx264 -pix_fmt yuv420p -movflags +faststart "output/${f%.png}.mp4"; done

```

If you're going to import this into OpenShot or another editor, then consider using a lossless intermediate format instead (ffv1, huffyuv, libx264 with -qp 0, etc). Also, you may want to match the frame rate of your music video, such as 25 in this example:
```

mkdir output
for f in *.png; do ffmpeg -framerate 13 -i "$f" -c:v ffv1 -g 1 -r 25 "output/${f%.png}.mkv"; done

```

If you want to get real fancy you can use the concat filter and do everything at once:
```

mkdir output
for f in *.png
  do ffmpeg -framerate 13 -i "$f" -i "$musicvideo" -filter_complex "aevalsrc=0|0:d=1[silent];[0:v][silent][1:v][1:a]concat=n=2:v=1:a=1[v][a]" -map "[v]" -map "[a]" "output/${f%.png}.mkv"
done

```
You'll need to use arrays or something for your input variables to get this example to work.

---

### Post by FakeOutdoorsman on 2016-05-01
FFmpeg development is very active, so unless you're using 15.10 or newer I recommend [downloading a recent ffmpeg binary](http://johnvansickle.com/ffmpeg/) or use [mc3man's PPA for 14.04 users](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media).

Then you can use a bash for loop. Untested H.264 example:
```

mkdir output
for f in *.png; do ffmpeg -framerate 25 -loop 1 -t 10 -i "$f" -c:v libx264 -pix_fmt yuv420p -movflags +faststart "output/${f%.png}.mp4"; done

```
Adjust -framerate to your desired frame rate. Consider using the same frame rate as the music videos.

If you're going to import this into OpenShot or another editor, then use a lossless intermediate format instead (ffv1, huffyuv, libx264 with -qp 0, etc):
```

mkdir output
for f in *.png; do ffmpeg -framerate 25 -loop 1 -t 10 -i "$f" -c:v ffv1 -g 1 "output/${f%.png}.mkv"; done

```

If you want to get real fancy you can use the [concat filter](http://ffmpeg.org/ffmpeg-filters.html#concat) and do everything at once:
```

mkdir output
for f in *.png
  do ffmpeg -framerate 25 -loop 1 -t 10 -i "$f" -i "$musicvideo" -filter_complex "aevalsrc=0|0:d=1[silent];[0:v][silent][1:v][1:a]concat=n=2:v=1:a=1[vpre][a];[vpre]format=yuv420p[v]" -map "[v]" -map "[a]" -c:v libx264 -c:a aac -movflags +faststart "output/${f%.png}.mp4"
done

```
Input frame rate, width, and height should all be the same. You'll need to use arrays or something for your input variables to get this example to work.

---

