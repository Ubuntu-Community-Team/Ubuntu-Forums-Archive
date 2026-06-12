---
title: "Logitech Quickcam, I think i know why they won't work."
date: 2008-11-08
forum: Multimedia Software
---

### Post by bishounen on 2008-11-08
For those of you who, like me, found that your Logitech camera  (mine is a Quickcam for Notebooks Pro) suddenly quit working with Intrepid, I think I may have found out why.

The older Logitech cameras use Phillips USB camera hardware.  This uses the pwc camera driver.  Unfortunately, there have recently ben some kernel changes which resulted in the removal of the pwc drivers from the kernel.  This means that for those of us with slightly older cameras, there is NO driver built into the kernel for it.

What this means is that you have to RECOMPILE YOUR KERNEL to include the pwc driver AND the binary add-on so you can get high-rez video out of it.  (without the binary, the cameras will work, but like crap.)

Now, I would LOVE to post the directions on how to do this, but I've got no freaking clue how to go about that, nor am I inclined to try.  Needless to say, this is going to need a new kernel patch from canonical to fix it for most users.

Info on the missing driver here:  [http://www.smcc.demon.nl/webcam/](http://www.smcc.demon.nl/webcam/)

---

### Post by curly752 on 2008-11-08
> **bishounen said:**
> For those of you who, like me, found that your Logitech camera  (mine is a Quickcam for Notebooks Pro) suddenly quit working with Intrepid, I think I may have found out why.

The older Logitech cameras use Phillips USB camera hardware.  This uses the pwc camera driver.  Unfortunately, there have recently ben some kernel changes which resulted in the removal of the pwc drivers from the kernel.  This means that for those of us with slightly older cameras, there is NO driver built into the kernel for it.

What this means is that you have to RECOMPILE YOUR KERNEL to include the pwc driver AND the binary add-on so you can get high-rez video out of it.  (without the binary, the cameras will work, but like crap.)

Now, I would LOVE to post the directions on how to do this, but I've got no freaking clue how to go about that, nor am I inclined to try.  Needless to say, this is going to need a new kernel patch from canonical to fix it for most users.

Info on the missing driver here:  [http://www.smcc.demon.nl/webcam/](http://www.smcc.demon.nl/webcam/)

bishounen - that page is very old... it refers to problems of over a year ago.

---

### Post by bishounen on 2008-11-08
> **curly752 said:**
> bishounen - that page is very old... it refers to problems of over a year ago.

Dang.  And here I was thinking I was onto something.  :(

Oh well.  Can't say I didn't try.

Now if I could only figure out WHY my camera won't work!!!

---

### Post by cariboo on 2008-11-08
The difference is that your web cam is now a v4l device. Cheese and Camorama don't know what to do with a v4l device. The only app I've found that automagically detects my Logitech QUickcam Messanger is Ekiga, mind you I haven't looked to hard yet for any other applications.

Jim

---

### Post by jasreca on 2008-11-11
> **cariboo907 said:**
> The difference is that your web cam is now a v4l device. Cheese and Camorama don't know what to do with a v4l device. The only app I've found that automagically detects my Logitech QUickcam Messanger is Ekiga, mind you I haven't looked to hard yet for any other applications.

Jim
No it is not a v4l device. Ekiga sees nothing, skype sees nothing, /dev/video0 does not exist. I've been tampering with some retarded gspca module whole afternoon now, but it won't compile.
I'm starting to get sick and tired of the thing.

---

### Post by Yellow Pasque on 2008-11-11
> I've been tampering with some retarded gspca module whole afternoon now, but it won't compile.
gspca modules come with the Ubuntu kernel modules. Check /lib/modules/`uname -r`/kernel/drivers/media/video/gspca
You can see if the gspca kernel modules are loaded with:
```
lsmod | grep gspca
```

---

### Post by jasreca on 2009-04-24
nope, not loaded, and the gspca directory does not exist...

in the meantime I gave away my QuickCam, and am looking for a cam that will work with linux...

---

### Post by Saibot Sivad on 2009-05-06
> **cariboo907 said:**
> The difference is that your web cam is now a v4l device. Cheese and Camorama don't know what to do with a v4l device. The only app I've found that automagically detects my Logitech QUickcam Messanger is Ekiga, mind you I haven't looked to hard yet for any other applications.

Jim

If this is the case, that the Quickcam is v4l, then I don't think one should say that the Quickcam is supported "out of the box" in Ubuntu.

What advantage does v4l2 present, if support for a mainstream webcam is broken? This, quite bluntly, sucks hard-core.

---

### Post by cariboo on 2009-05-06
My Quickcam messenger is automagically detected in Juanty and uses the gspca_zc3xx module.

---

### Post by hansdown on 2009-05-06
A fairly good idea of webcams that work in ubuntu can be found below.

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

