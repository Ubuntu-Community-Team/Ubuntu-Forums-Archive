---
title: "How can I reset my webcam (Phillips SPC 900 NC) without loading windows xp"
date: 2010-07-14
forum: Multimedia Software
---

### Post by crjackson on 2010-07-14
Okay here's my problem.  My webcam works AWESOME when it works.  However, occasionally it produces no video for Ubuntu based applications.  Cheese, aMSN, Skype or anything else for Ubuntu Lucid.

I have tried power off & cold booting.  Moving from one USB port to another, warm booting etc...

The only way to make it work instantly is to boot into Windows XP and access the Webcam.  Then upon rebooting to Ubuntu the cam works perfectly again.

It's not a matter of Ubuntu finding and recognizing the cam.  It always does and TRYS to activate the cam (the led comes on when loading any cam application) but it produces no video.

**Is there a command I can use to force a _RESET_ of the video device so I can stop loading Windows?**  I freaking hate the necessity of using windows to fix this problem. 

Thanks for your help.

---

### Post by no2498 on 2010-07-14
you can try an see if this helps it does for me

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

this is a nice cam program wxcam

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it also comes in a deb file

hope this helps you

---

### Post by crjackson on 2010-07-14
Okay, thanks.  It'll be a week or so before it decides to act up again.  When it does I'll try working with gstreamer-properties and see what happens.

thanks

---

