---
title: "How do I find movement in a video file"
date: 2013-08-06
forum: Multimedia Software
---

### Post by ssam on 2013-08-06
I am experimenting with a DIY CCTV system using an old helmet cam. I can leave it running, and then later collect it and download the file to a computer. However hours of footage of the back yard are not exciting viewing, so I'd like something to scan through the files, and let me know where anything eventful happened.

I have found lots of information about [Motion]("http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome"), which looks great, but seems to only work with a live video stream. Does anyone know of an equivalent that works with a folder of existing video files?

---

### Post by GwL3eNC on 2013-08-07
unfortunately i don't know a application. But, if you have java programming experience you can try to do
it on your own. I would give ImageJ a try, import my avi file and convert it to a thing called ImageStack. I would
make two from the same video an try building differences and using correlation etc. There are also some 
plugings for biological use, all code is open an should bring you further if you try. 
For example [http://www.uhnresearch.ca/facilities/wcif/](http://www.uhnresearch.ca/facilities/wcif/).

---

### Post by Cheesemill on 2013-08-07
This looks promising...
[http://cwee.ucdavis.edu/projects/CBVision](http://cwee.ucdavis.edu/projects/CBVision)

Unfortunately they don't provide pre-built binaries but there are instructions for compiling it yourself in the downloadable pdf manual.

---

### Post by ssam on 2013-08-08
thanks for comments. I found out a bit of info with more searching
to use motion with existing files you can make a fake webcam device using video4linux loopback [http://www.lavrsen.dk/foswiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/foswiki/bin/view/Motion/VideoFourLinuxLoopbackDevice)

I also found that you can split the video into frames with ffmpeg
```

ffmpeg -i inputvideo.h264 -r 1 -f image2 -s 240x135  frames_%6d.png

```
(grabs 1 frame per second)
then use matplotlib to read each image, subtract the last one, and sum the pixel differences.

---

### Post by SlugSlug on 2013-08-08
am sure you have a reson but whats wrong with using motion as the cctv?

---

### Post by notnuke on 2013-08-09
If you can tweak the code, I'm pretty sure motion detection and file I/O are samples that come with [http://opencv.org/](http://opencv.org/)

---

### Post by cdragon on 2014-02-06
It can be done by installing VirtualDub and AVISynth 2.5 with the following AVISynth plugins: RT_Stats v1.20, FrameSel v1.03, GScript, and Grunt.  Note that "FrameSel" is NOT the same as the "FrameSelect" plugin.

Edit SecurityCamExtractMotion.AVS that comes with RT_Stats and edit the video file it refers to as well as any parameters you want to tweak.  I used it with TH set to 12.5, commented "ShowMetrics(..." and uncommented "AutoGetFrames(...".  Open SecurityCamExtractMotion.AVS in VirtualDub and after a long delay (about 30 minutes for 5 hours of video), you'll see a video containing only frames where motion was detected.

I've only gotten it to work with AVI files and I was running it under Windows but supposedly it works in Ubuntu as well.  I tried to use it with an MTS/M2TS file and it acted like it worked but did not show the correct frames.  So I had to use another video processor to render the MTS file as AVI.

---

