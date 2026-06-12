---
title: "Use a DV cam as a webcam -- help?"
date: 2011-03-23
forum: Multimedia Software
---

### Post by garfonzo on 2011-03-23
Hey Folks:

I am a recent convert to Ubuntu 10.10 from Vista. I work from home and do all of my work via remote login and video conferencing through Skype. In Vista, I could use my DV Camcorder as a webcam which, in turn, gave me video for Skype. In Vista, I used a program call "Tracker Cam" which I could run, and then it would act like a video driver for Skype and presto, I had perfect video in Skype.

Now that I am in Ubuntu, I am trying to achieve the same thing. I can hook up my DV Camcorder (A Sony Handycam HDR-HC5) and see the live video through Kino. However, this doesn't help me with Skype. I still can't enable video, or select a video device in Skype. I have Googled this up and down with no leads.

So, I am wondering if anyone has done this with Skype (or other programs) to get their DV Camcorders acting like webcams for video calls or is this just one of those things that won't work in Ubuntu?

Thanks!

---

### Post by garfonzo on 2011-03-23
Well, wouldn't you know it. An hour after this post, I found a solution. 

For those who are also on the hunt for a solution, here is how I got it to work:

**Objective**: Get Skype to use my DV Camcorder (Sony HDR-HC5) as a video source on Ubuntu 10.10 hooked up via firewire. 

**Solution**:
[LIST]
[*]Download "Webcamstudio" from this website: [Webcam Studio for GNU/Linux]("http://www.ws4gl.org/download/installing-on-ubuntu")
[*]Install "dv4l" from the Ubuntu Software Center (on the "Applications" menu on your desktop)
[*]Edit your user groups so that you can use the video device. Open System-> Admin-> Users and Groups, Click advanced settings for your account, click user privelages tab, ensure there is a checkmark by the "Use Video device" option and hit "OK". Then click "Manage Groups", scroll to "Video", click "Properties" and ensure your user name is part of that group. 
[*]Create an application launcher (right click desktop and select "Create Launcher". Type a name such as "Skype with DV/Cam" and for the command put: ```
dv4lstart skype /dev/video0
```
[*]Restart your computer and double click your launcher. Make sure you select the new "webcam" in the Skype options. 
[/LIST]

This is how I got it working. Hopefully it helps someone else looking for the solution.

---

