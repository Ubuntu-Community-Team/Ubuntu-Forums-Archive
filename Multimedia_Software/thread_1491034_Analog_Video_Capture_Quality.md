---
title: "Analog Video Capture Quality"
date: 2010-05-23
forum: Multimedia Software
---

### Post by kb909 on 2010-05-23
Hi - I need some expert advice on how to improve my captured video quality. I have an analog SAA1734 based capture card and I use the composite port to capture video using the following command:
```
mencoder -ffourcc XVID tv:// -tv driver=v4l2:input=1:norm=pal-i:width=320:height=240:device=/dev/video0:forceaudio:audiorate=32000 buffersize=512 -ovc lavc -lavcopts vcodec=mpeg4:mv0:trell:v4mv:vbitrate=3000:ildct:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -o output.avi
```

Let me first say, the quality is not bad, so all I want to know is am I on the right track and can I improve the quality? The Standard is PAL-I and playback is on a 42" Plasma. Any one struggling with analog capture can go to a blog page I made for hopefully some helpful information. [http://www.tle-kobus.blogs.com/](http://www.tle-kobus.blogs.com/).

Thanks in advance

---

### Post by xzero1 on 2010-05-23
I'm no expert but xvid might not be the best codec, x.264 is probably better. Also 320x240 seems low. If you really want to push it, use a lossless codec to capture at the highest resolution your capture card provides, filter, deinterlace,reduce and re-encode to your target video.

---

### Post by kb909 on 2010-05-25
Hi Xzero1 - Thanks for the pointers. I will try your suggestions and report back. I seem to have some issues with X264 with the video looking very pixelated, almost like square pixels. I did not have any success with lossless using crf=0 parameter either. The 320x240 also could be a limitation on the card, since everything above that is degraded. The manufacturer suggests HD resolution capable though. All the above said, could you possibly translate your advice into a command - Thanks

---

### Post by xzero1 on 2010-05-25
I'm not familiar with pal since I live in the U.S. so I cannot test a specific command line. What might be helpful though is if you install ivtv-utils and then post the output from this command:

v4l2-ctl --all

This will list your capture cards info. Also post the command lines you are using. Another thing that will make a big difference the the input connection type. If possible, you should be using in this order s-video,composite,rf.

---

