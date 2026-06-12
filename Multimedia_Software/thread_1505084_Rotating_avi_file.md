---
title: "Rotating avi file"
date: 2010-06-08
forum: Multimedia Software
---

### Post by Janeleaper on 2010-06-08
I have several small avi files that I shot with my digital camera. A few of them play sideways, that is rotated 45 degrees.  I want to rotate them upright again, just as a I would a digital picture, but I can't find any software that would enable me to do that.  Pitivi video editor doesn't do it.  Does anyone know of any software that would do it?

---

### Post by splicerr on 2010-06-09
If it were rotated a multiple of 90 degrees you could use avidemux. For 45 degrees, Blender can handle that. But it's not a simple application, so if you've never used Blender before you'll first have to learn the basics.

---

### Post by xc3RnbFO8P on 2010-06-09
I hope you mean 90 degrees.
In Avidemux Video, choose codec
in Filter> Transfom> Rotate (90 or 270)

---

### Post by Jinger on 2010-06-09
You can also use Cinelerra. There's an effect in order to do this. 
[IMG]http://img571.imageshack.us/img571/639/schermatafinestrasenzat.png[/IMG]

---

### Post by FakeOutdoorsman on 2010-06-09
Another option for those who prefer command-line.  This is easier than it looks:

1. Install FFmpeg and Imagemagick:
```
sudo apt-get install ffmpeg imagemagick
```

2. Install additional encoders in FFmpeg (required for step 5, unless you want a different output format).
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

3. Convert the movie to images:
```
mkdir imagedump
ffmpeg -i input.foo imagedump/%d.png
```

4. Rotate the images:
```
mogrify -rotate 90 imagedump/*.png
```

5. Convert the rotated images to a movie.  This example will create a H.264 video:
```
ffmpeg -i imagedump/%d.png -vcodec libx264 -vpre hq -crf 26 -threads 0 output.mp4
```
For more information on these options, see [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).  It's also possible to copy the audio from the original into the rotated video.  See the [add mp4a track to mp4 video](http://ubuntuforums.org/showpost.php?p=9431205&postcount=3) thread for example commands.

6. Delete imagedump directory:
```
rm -rf imagedump
```

---

### Post by Janeleaper on 2010-06-09
Thank-you.  I did mean 90 degrees.

---

