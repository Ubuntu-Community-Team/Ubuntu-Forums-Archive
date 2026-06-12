---
title: "High fps with guvcview but low fps with v4l"
date: 2012-05-14
forum: Multimedia Software
---

### Post by nevixa on 2012-05-14
Hello,

I am having problems with my  webcam, Microsoft LifeCam Cinema. In guvcview the camera is working  perfectly (1280x720 30fps), but when using other (I guess v4l, but not  sure) applications, I only get 10fps on 1280x720. For example when using  v4l Control Panel and start a preview in MPlayer, it only gets 10fps. 

I'm on Ubuntu 10.10. Anyone any idea why this is, and more importantly how to fix this? 

Thanks in advanced!

---

### Post by mörgæs on 2012-05-16
My first recommendation is a fresh install of one of the 12.04 Buntus. 

10.10 is unsupported and contains, as you have experienced, obsolete packages.

---

### Post by nevixa on 2012-05-18
I figured out it is a problem with my gstreamer. Somehow it only can handle 10fps yuv, except when you force it to do 30fps like this:

gst-launch v4l2src device=/dev/video0 ! 'video/x-raw-yuv, width=1280, height=720,framerate=30/1' ! xvimagesink

Problem is that I have no idea how to get this working in my c++/OpenCV program. Any ideas?

---

### Post by mörgæs on 2012-05-19
I have already posted my main idea, but you didn't respond to it.

---

### Post by nevixa on 2012-05-19
> **mörgæs said:**
> I have already posted my main idea, but you didn't respond to it.

Sorry. I will try this today. Thank you for your reply

---

### Post by nevixa on 2012-05-24
[[COLOR=#DD4814]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075") thanks again for your reply. I did a fresh install of Ubuntu 12.04, that did not directly did the trick, but did do something. The problem was that I was setting the camera to 1280x800 in my own program and to 1280x720 in other programs. In the 1280x800 mode, the camera can only output 10fps. Setting it to 1280x720 with the freshly installed Ubuntu 12.04 gave me 30 fps throughput! 

Thanks again

---

