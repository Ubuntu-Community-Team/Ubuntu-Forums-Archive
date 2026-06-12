---
title: "gstreamer-properties won't start"
date: 2011-07-02
forum: Multimedia Software
---

### Post by someitalian123 on 2011-07-02
When I type gstreamer-properties in to the terminal I get

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'

and nothing happens. I was just trying to get my webcam working, since it isn't detected with skype.. It should work out of the box since it's supported by the uvc driver. I have gstreamer good , bad , ugly , and .010 installed

---

### Post by no2498 on 2011-07-03
see if this helps you half way down the page


[http://ubuntuforums.org/showthread.php?t=1777612&highlight=cheese](http://ubuntuforums.org/showthread.php?t=1777612&highlight=cheese)

---

### Post by someitalian123 on 2011-07-03
That did absolutely nothing, gstreamer-properties still won't start after installing gstreamer0.10-gconf.

Edit:
 I just installed xawtv to see if my tv tuner works and my webcam works in xawtv I also tried vlc and that worked too, but it still isn't detected in skype or cheese, how do I fix that. I've tried LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype and LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype. My webcam still isn't detected.

---

### Post by no2498 on 2011-07-04
try starting gstreamer-properties with sudo

sudo gstreamer-properties

i see a line i do not get as i start gstreamer-properties

gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'


you have this 1

gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'



is odd yours dont work in cheese after you see it in xawtv

thats how i get mine to work in cheese
as xawtv loads a cam grabber

---

### Post by someitalian123 on 2011-07-05
sudo made no difference. When ever I try cheese I'm unable to close it, I can force quit but I still find it running under the processes tab of the system monitor. Should I try installing the missing plug in? Where can I find it? I don't think it's in the repositories.

---

### Post by Yellow Pasque on 2011-07-05
You can use gconf-editor to change the values that gstreamer-properties does.

---

### Post by someitalian123 on 2011-07-05
Yeah I suppose but I can't help but think that some how my webcam not working with skype or cheese is related to gstreamer-properties not starting. I don't care if gstreamer-properties works, I just want my webcam to work. Is there any settings I could try to change in gconf-editor to fix the problem? Video was suppose to be able to work right out of the box according to this list .

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by no2498 on 2011-07-06
try these for cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so cheese

---

### Post by someitalian123 on 2011-07-06
I've already tried those with skype and cheese and neither of them did anything.

---

