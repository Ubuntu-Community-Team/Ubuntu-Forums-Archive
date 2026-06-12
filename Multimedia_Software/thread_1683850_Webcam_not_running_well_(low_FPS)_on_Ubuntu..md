---
title: "Webcam not running well (low FPS) on Ubuntu."
date: 2011-02-08
forum: Multimedia Software
---

### Post by Milorandom123 on 2011-02-08
[I]Hi, I'm relatively new to Ubuntu, and am currently just setting it up so that it can preform just as well as my Windows install (I'm dual booting Vista & Ubuntu), currently trying to get my webcam to work and trying to get it to record well.
[/I][B]
OS: Ubuntu 10.10

Webcam: Logitech Quickcam s5500

Software used: Cheese Webcam Booth[/B] (Standard webcam software for Ubuntu?)


So as soon as I plugged in my webcam and ran cheese it found the webcam and got the picture, no problems so far; 

**1.** However, when trying to record on acceptable quality settings the FPS dropped massively to less than 1 FPS. When I run it in the lowest possible quality 160x120 the video recording works fine. The effects are all turned off. On my windows I can get a lot higher quality than is even possible with this software, and it runs perfectly.

**2.** There is no sound whatsoever. This Logitech Webcam does have a build in microphone, which is fully operational when running it on Windows. 


-Of course on windows I am running the software that is specifically designed for this very webcam. 
-The webcam has, I believe it's called, a shutter, you can move this over the lens to block the image, and the webcam does actually (on Windows) read the location of the shutter and it'll run some code when the shutter is on to create a new 'image' (like a background), obviously the shutter is not on, but it could possibly be that the software isn't operating right and is blocking some of the functionality.(?)

---

### Post by Milorandom123 on 2011-02-14
Bumped.

---

### Post by fugalaya on 2011-04-02
I would like an answer to this as well.  The webcam on my Dell Vostro V13 is nearly unusable.  Other than that Ubuntu 10.10 runs great on it.

Thanks.

---

### Post by no2498 on 2011-04-03
this comes from the cheese help FAQ'S

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by keshetIsrael on 2011-05-13
Where can I get better plugins for the multimedia systems selector, video tab?  I only have one plugin and it's not doing the trick! My FPS is still set at 1 .. and I can't figure out how to simply change it.

Running ubuntu 11.04 Natty..

---

### Post by no2498 on 2011-05-14
keshetIsrael
you need to make your own ?
as i have just started seeing they are doing away with some of gstreamer
so someone has bigger better plans for the cams

---

### Post by Anthem on 2011-05-16
I can confirm the low framerate isn't a Cheese problem... it's also there in Google Video Chat, Skype, and the input test program for gstreamer.

> **no2498 said:**
> this comes from the cheese help FAQ'S

The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

Tried it, but it didn't change anything.

The bug is documented in #613979, but unfortunately the submitter didn't give enough detail.  The maintainer said "I can see myself in Cheese just fine" without knowing it's the framerate that's the problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/613979](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/613979)

For what it's worth, this laptop is sold by Dell with Ubuntu pre-installed, but the spec sheets don't say there's a webcam.  I'm guessing it's a bad driver.

---

### Post by keshetIsrael on 2011-06-07
> **no2498 said:**
> keshetIsrael
you need to make your own ?
as i have just started seeing they are doing away with some of gstreamer
so someone has bigger better plans for the cams

What do you mean make my own?

---

### Post by no2498 on 2011-06-08
try this program wxcam
it should be in your repos

---

