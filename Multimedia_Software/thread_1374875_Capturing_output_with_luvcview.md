---
title: "Capturing output with luvcview"
date: 2010-01-07
forum: Multimedia Software
---

### Post by garryknight on 2010-01-07
According to 'man luvcview', if I do this:
```

luvcview -o testvid.avi

```then luvcview should capture the video to the .avi file. However, when I try it, no output file is created. Grabbing a raw stream or raw frames works fine, but not the creation of AVI files. Am I missing something?

---

### Post by FlyingBuzz on 2010-01-09
I'm experiencing the same problem on Asus EeePC t91. Everything works fine except video capturing. No errors, no warnings, everything seems to be fine, but.. no video.

---

### Post by naruka on 2011-06-09
Hi,

Has anyone found a solution this problem ?

I am facing the same problem. luvcview does not save avi file though its able to capture jpgs, ram frames.
sudo luvcview -d /dev/video0 -f yuv -s 176x144 -i 3 -o ./vid.avi

It shows like avi file recording started/stopped but there is no file generated.

Thank you,
naruka

---

### Post by no2498 on 2011-06-09
look in your home folder for it
or in the computer

---

### Post by naruka on 2011-06-09
I think I see the problem in luvcview code, avi file is not initialized  for V4L2_PIX_FMT_YUYV, its is initialized only for MJPG fmt.

./v4l2uvc.c:650:            vd->avifile = AVI_open_output_file(vd->avifilename);

Now all I want to know is, does luvcview doesnt support recording of avi file from YUV frames ? 
Any suggestions, what I can do for that support ?

Any help will be gr8!! 

Thanks,
Naruka

---

### Post by rahulagarwal622 on 2011-06-22
Hi,
How can I get frames in jpeg format. Luvcview only saves frames in .raw format. 
Or how can I view raw frames.

---

### Post by kayosiii on 2011-06-22
guvcview supports the same hardware and has a much friendlier interface. Unless you have a specific reason not to I would reccomend trying that in place of luvcview.

---

### Post by michelepolo on 2013-03-29
> **kayosiii said:**
> guvcview supports the same hardware and has a much friendlier interface. Unless you have a specific reason not to I would reccomend trying that in place of luvcview.

i do agree with you, Luvcview has an horrible and unfriendly interface, when Guvcview is much better

---

