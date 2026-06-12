---
title: "lifecam vx-3000 doesn't work"
date: 2010-01-29
forum: Multimedia Software
---

### Post by bgrohe on 2010-01-29
I have a microsoft lifecam vx-3000 and when I open cheese up, I get a black shot as seen in the screenshot then the a green shot as pictured below. Is there a way to get in to work in karmic?

---

### Post by bgrohe on 2010-03-01
I just tried alpha three of ubuntu, and the webcam sort of works, but it is very pixalized and discoloured. is there a way to correct this error? I will attempt to get a screenshot if someone requests it.

---

### Post by no2498 on 2010-03-02
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

open cheese click preference make the pic size smaller

---

### Post by bgrohe on 2010-03-07
That didn't change the quality at all.:confused:  Is it possible that the pixelization  is happening because of the live cd. Any suggestions are welcome.

---

### Post by executorvs on 2010-03-08
I'm in the same boat. I got it to run at one point in jaunty with much effort. what I get in the alpha right now isn't great but I'm going to try changing the video4linux modul's settings. I'll let you know if I have any luck.

---

### Post by bgrohe on 2010-03-08
thats good to know that someone is in the same situation as me, hopefully you can fix the problem. :)

---

### Post by no2498 on 2010-03-09
i do not think this will work with the live cd

open a terminal type (  gstreamer-properties  ) click enter
click video try v4l1 and v4l2 click the bottom test button for each 1

if you need to install gstreamer go to add/remove install it


try your cam in ekiga softphone its loaded already

---

### Post by bgrohe on 2010-03-09
The recent update to karmic gives me a similar result as the alpha, but the settings only give to different drivers and one doesn't work and the other is the same result. Any other suggestions?

UPDATE: I can get the colour right in ekiga, but it still seems out of focus.

---

### Post by executorvs on 2010-03-13
did you adjust the physical focus on the camera? it took me a while to think of it.. I felt smrt, I mean smart...

I did adjust the v4l2 default color settings a bit and it gives slightly better results from the drivers auto adjusting right after you turn it on. changing the lighting in my room got it a little better also. so while I can get a decent picture (kind of) it takes work as the auto adjusting properties of the driver don't work very well yet.

---

### Post by executorvs on 2010-03-13
oh, and did anyone get the mic working? it's giving me a headache.

---

### Post by bgrohe on 2010-03-13
The manual focus works (I didn't even notice it had one :)), I have not tested the mic yet though.

---

### Post by executorvs on 2010-03-13
to adjust the v4l2 settings you can use 'v4l2ucp' in the repos. I find that adjusting the lighting where you're using the camera has a greater affect though. after each adjustment you need to restart cheese or mplayer or which ever program you are previewing your tweaking with so you can see how the auto adjust is affected.

---

### Post by executorvs on 2010-06-10
For the VX-3000,
I've got the mic working in lucid. I have tested it in sound recorder and used it in skype. I'm sure of two steps used in getting it to run, but there may be remnants from weeks of tinkering I'm not sure of.

1.)I am using kernel 2.6.35-1.1 from the kernel testing ppa
2.)in order to get sound in skype you must install padevchooser and run it before opening skype.

if someone could try these steps and let me know how things go it would be appreciated. I'm going to try isolating what exactly is enabling the mic and will post more later.

the above is also posted at [http://ubuntuforums.org/showthread.php?t=1333343&page=2](http://ubuntuforums.org/showthread.php?t=1333343&page=2) and may be discussed there as well.

---

