---
title: "How to get a high res snapshot of an mpeg video?"
date: 2013-06-22
forum: Multimedia Software
---

### Post by MikeB23930 on 2013-06-22
In a nutshell, I want a "good" snapshot of an mpeg2 video that I can use as the startup image of a dvd I am authoring.

More info that might be useful:  I edited a PBS broadcast and exported it to a dvd ready mpeg using openshot in the DreamStudio 12.04 derivative of Ubuntu.  I'm using Bombono to author the dvd.  I've taken snapshots using VLC and Mplayer.  The snapshot looks great in imageviewer even at full screen but when I author the dvd the snapshot is so blurry that I would be better off just using a solid color background.  Deinterlacing in vlc doesn't imporove things at all.  I'm assuming the problem is with the resolution of the screen shot.

Any help you could offer would be greatly appreciated.

Thanks,

Mike

---

### Post by ktat on 2013-06-22
Hi Mike, can I suggest you take a look at these links:

[http://linuxers.org/tutorial/how-extract-images-video-using-ffmpeg](http://linuxers.org/tutorial/how-extract-images-video-using-ffmpeg)

[http://ubuntuforums.org/showthread.php?t=1141293](http://ubuntuforums.org/showthread.php?t=1141293)

---

### Post by MikeB23930 on 2013-06-22
[QUOTE=ktat;12702411]Hi Mike, can I suggest you take a look at these links:

[http://linuxers.org/tutorial/how-extract-images-video-using-ffmpeg](http://linuxers.org/tutorial/how-extract-images-video-using-ffmpeg)

[http://ubuntuforums.org/showthread.php?t=1141293](http://ubuntuforums.org/showthread.php?t=1141293)[/QUOT

Ktat, I think that with a little trial and error I can use the first link to get what I want.  Your help is very much appreciated.

Mike

---

### Post by FakeOutdoorsman on 2013-06-23
jpg:
```
ffmpeg -ss 12 -i input.mpg -vframes 1 -qscale:v 2 output.jpg
```
png:
```
ffmpeg -ss 00:22:14 -i input.mpg -vframes 1 output.png
```
To deinterlace with the [yadif](http://ffmpeg.org/ffmpeg-filters.html#yadif-1) filter:
```
ffmpeg -ss 12 -i input.mpg -vf yadif -vframes 1 -qscale:v 2 output.jpg
```

[list]
[*]"-qscale:v" controls the output quality for jpg, and a value of 2 will give a good quality output. You may have to use "-qscale" instead of "-qscale:v" if it is not recognized.
[*]The "-ss" option can use seconds or sexagesimal format HH:MM:SS.MICROSECONDS for time values as shown in both examples.
[/list]

---

### Post by SeijiSensei on 2013-06-23
Another easy solution is to install **SMPlayer** from the respositories and use it to take screenshots.

You can have it take a single shot or a sequence with a keystroke combination while the video is playing.  You'll get files with names like shot0001.png.  The image will have the same resolution as the video, e.g., 1280x720 pixels for 720p content.

---

### Post by MikeB23930 on 2013-06-23
> **SeijiSensei said:**
> Another easy solution is to install **SMPlayer** from the respositories and use it to take screenshots.

You can have it take a single shot or a sequence with a keystroke combination while the video is playing.  You'll get files with names like shot0001.png.  The image will have the same resolution as the video, e.g., 1280x720 pixels for 720p content.

FakeOutdorsman and SeijiSensei, thanks for your help.  By the by, SeijiSensei, you might want to take a look at the third post in this thread.

Mike

---

### Post by andrew.46 on 2013-06-23
The commandline MPlayer allows you to manipulate the *quality* of the generated png (so I guess SMPlayer does as well). For the gory details have a look at Tip 5:

[http://andrews-corner.org/topten.html](http://andrews-corner.org/topten.html)

Several other formats available although I suspect that png would be the best choice...

---

### Post by SeijiSensei on 2013-06-24
I've taken many screenshots from 720p anime videos and stored them as PNG.  Here are a few examples:

[http://www.takinganimeseriously.com/images/kurenai-wall.png](http://www.takinganimeseriously.com/images/kurenai-wall.png)
[http://www.takinganimeseriously.com/images/worried-red-sox-mom.jpg](http://www.takinganimeseriously.com/images/worried-red-sox-mom.jpg)
[http://www.takinganimeseriously.com/images/mononoke-wallscreen-1280.png](http://www.takinganimeseriously.com/images/mononoke-wallscreen-1280.png)
[http://www.takinganimeseriously.com/images/moloch+azazel.png](http://www.takinganimeseriously.com/images/moloch+azazel.png)

I've saved images as JPEGs as well; whatever differences there are between the formats are not discernible by my aging eyes.

---

