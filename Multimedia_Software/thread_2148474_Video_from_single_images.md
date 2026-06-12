---
title: "Video from single images"
date: 2013-05-25
forum: Multimedia Software
---

### Post by xxlray on 2013-05-25
I took a set of photos which I want to combine to a timelapse video. So far I have tried three approaches.

ffmpeg:
```
ffmpeg -i DSC_%04d.JPG -vcodec mpeg4 timelapse.mp4
```
The command only returns "DSC_%04d.JPG: No such file or directory" where all files in the directory look like DSC_6467.JPG .
I use ffmpeg 0.10.6-6:0.10.6 from the [Jon Severinsson PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg") on Ubuntu 12.04

mencoder:
```
mencoder -nosound -ovc x264 -x264encopts preset=slow:tune=film:crf=20  mf://*.JPG type=jpeg:fps=25:w=2896:h=1944 -o timelapse.avi
```
The result misses the last multiple tens of images.

avidemux:
I can attach files manually and create a working video but this is just too much work for some thousand images still waiting.

I would be thankful if you could solve any of the issues or even propose a new way which will just do the job. Note that I need a non-standard resolutions like 2896x1944.

---

### Post by evilsoup on 2013-05-25
The FFmpeg Image2 demuxer looks for files starting at number 0001, so if the lowest image number is something other than 1 you should try something like (to start from the 55th image):

```

ffmpeg -start_number 55 -i DSC_%04d.JPG -vcodec mpeg4 timelapse.mp4
##  or
ffmpeg -f image2 -start_number 55 -i DSC_%04d.JPG -vcodec mpeg4 timelapse.mp4

```

If there are gaps in the numbering, this may not work, so you should try:

```

ffmpeg -f image2 -pattern_type glob -i 'DSC_*.JPG' -vcodec mpeg4 timelapse.mp4

```

---

### Post by xxlray on 2013-05-25
The first option unfortunately gives me "Unrecognized option 'start_number'" and the last one "Unrecognized option 'pattern_type'".

---

### Post by sudodus on 2013-05-25
It is also possible to use the ***Openshot*** video editor.

---

### Post by FakeOutdoorsman on 2013-05-25
> **xxlray said:**
> The first option unfortunately gives me "Unrecognized option 'start_number'" and the last one "Unrecognized option 'pattern_type'".

Your version of ffmpeg is too old. Try a recent [static build](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453) (just download, extract, and run) or you can compile it fairly easily with these non-intrusive instructions: [Compile FFmpeg on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

---

### Post by xxlray on 2013-05-25
> **sudodus said:**
> It is also possible to use the ***Openshot*** video editor.
I use it a lot and I think you are talking about the "import as image sequence" feature but whenever I try to preview the imported sequence it only shows "INVALID". I think I read that only lower resolutions are so far supported.

> **FakeOutdoorsman said:**
> Your version of ffmpeg is too old. Try a recent [static build]("http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453") (just download, extract, and run) or you can compile it fairly easily with these non-intrusive instructions: [Compile FFmpeg on Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").
I will have to give this a try. Hopefully this will not blow up my system.

---

### Post by xxlray on 2013-05-25
The new installation of ffmpeg worked like charm. For anybody interested this is what I did:
```
mkdir ~/ffmpeg.static
cd ~/ffmpeg.static
wget http://ffmpeg.gusari.org/static/64bit/ffmpeg.static.64bit.2013-05-25.tar.gz
tar -xvzf ffmpeg.static.64bit.2013-05-25.tar.gz
rm ffmpeg.static.64bit.2013-05-25.tar.gz
cd /path/to/my/photos
~/ffmpeg.static/ffmpeg -f image2 -pattern_type glob -i 'DSC_*.JPG' -vcodec mpeg4 timelapse.mp4
```

---

