---
title: "Skype Video Freeze"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by chownrus on 2008-02-10
Hi all

I've been having problems with Skype Beta (2.0.0.43) and video conferencing.

I have a Logitech Communicate STX camera. (gspca driver)


Skype detects the camera and starts video just fine, but the video looks jerky and pixellated on the receiving end. 

After 30 seconds, the video freezes (but audio continues). If I restart the video, it will do the same thing -- transmit for 30 seconds and freeze.

Also, CPU usage is close to 100%.

Any help would be greatly appreciated, thanks

---

### Post by linuxwizard on 2008-02-10
According to this a known issue the cam will crash but it also said it was fixed.
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

---

### Post by chownrus on 2008-02-15
According to your link, the fix came with version 2.0.0.27. 
Is it possible that 2.0.0.43 broke it again? If so, is there anywhere I can get version 2.0.0.27 to test it?

Thanks

---

### Post by tribunal on 2008-02-23
same problem here, 2.0.0.43, freezes in 30 secs

---

### Post by chensamurai on 2008-03-28
BTW, I have solved this problem.

To me, you were right when you said that the problem was probably from Compiz.

To stop the video freezes and lags, I simply unselected as many uneeded Compiz effects and chose the "None" mode for "Visual Effects"

In this mode, Ubuntu has no fancy graphics but music and video plays smoothly and perfectly
:popcorn:

---

### Post by simplejordon on 2008-03-30
I used skype but just for IMs ...I have Logitech QuickCam Communicate STX Webcam integrated with my [http://www.rhubcom.com](http://www.rhubcom.com) turbomeeting for over an year now and frankly its the best one I got...there haven't been any issues whatsoever..You shall try a different browser if helps..

---

### Post by turezky on 2008-05-01
Uncheckin' compiz effects solves the trouble, but what if I'm that greedy that I want both :)

---

### Post by chinese_ys on 2008-05-09
Disabling the compiz is the only solution for this so far?

what about skype version 2.0.0.68?

thax

---

### Post by GourmetGen on 2008-05-16
I have this problem and am not running Compiz or have nvidia driver installed.  

I get video for less than 10 sec and then my whole machine freezes, only a hard reset works (though mouse is still active, no response from keyboard). I have tried this with a video feed from my computer only and it works ok. When the second video feed is detected, complete freeze. 

The complete freeze has also happened to me when I've opened two different media applications at the same time. 

I'm runny under Hardy with Skype 2.0.0.68. 
Thanks,

---

### Post by erichgamba on 2008-05-27
You could try the skype-static package from the medibuntu repository.

---

### Post by jkmuller on 2008-07-11
> **GourmetGen said:**
> I have this problem and am not running Compiz or have nvidia driver installed.  

I get video for less than 10 sec and then my whole machine freezes, only a hard reset works (though mouse is still active, no response from keyboard). I have tried this with a video feed from my computer only and it works ok. When the second video feed is detected, complete freeze. 

The complete freeze has also happened to me when I've opened two different media applications at the same time. 

I'm runny under Hardy with Skype 2.0.0.68. 
Thanks,

This is my exact problem, anyone found a solution yet?

---

