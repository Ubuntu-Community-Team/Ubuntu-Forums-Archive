---
title: "All of a sudden sluggish video and no audio in Cheese"
date: 2010-11-28
forum: Multimedia Software
---

### Post by giddyup306 on 2010-11-28
I've been fighting this problem for probably a week.  The first video was the very first test take I took since I got my Logitech Orbital web cam.  It was the best one they had, and it supports 30 FPS.  I thought maybe I might have better luck if I tried some other software.  Someone suggested Webcamstudio, but I can't get the audio to work on there. Period.  I looked for some tutorials on youtube, and the version that I found on there is quite different than what I have.  Here's the original video that I made about a week ago.  The next is something I just recorded.  I read the faqs on Cheese.  It said something about the resolution.  Both of these recording are 320X240.  It also said something about the processor being overworked, rather than working the video card.  I have an i7 processor, and it doesn't even break a sweat with things like this.  I tried changing the settings as per the FAQs, but the settings weren't the same (or I didn't understand them).  

I was going to let that go for the moment and make some Linux tutorials.  I wanted to use GTK record my desktop, but the mic in my Orbital didn't work.  So I can't even make a few quick tutorials.  

Here's the videos.

[http://www.youtube.com/watch?v=MoxLxR1ktmg](http://www.youtube.com/watch?v=MoxLxR1ktmg)

[http://www.youtube.com/watch?v=PUqneh7qEVw](http://www.youtube.com/watch?v=PUqneh7qEVw)


Another thing is that the res was reduced a lot when I converted it from .ogv to .flv.

Thoughts?

---

### Post by giddyup306 on 2010-11-28
I forgot to mention that sometimes it won't record at all.

---

### Post by no2498 on 2010-11-28
this is a 32 bit program it may help you wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by giddyup306 on 2010-11-29
> **no2498 said:**
> this is a 32 bit program it may help you wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)


Tried that one as well. Couldn't get the audio or video to record with that one.

Does no one know why Cheese is messing up???

---

### Post by no2498 on 2010-11-29
this is in the cheese help faq's


My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.

---

### Post by giddyup306 on 2010-11-29
After two days of searching I finally found this.

[http://forums.logitech.com/t5/Webcams/How-to-get-30-Frames-Per-Second-with-your-Logitech-Webcam/m-p/202898](http://forums.logitech.com/t5/Webcams/How-to-get-30-Frames-Per-Second-with-your-Logitech-Webcam/m-p/202898)

It's all Windows related tho. The software that comes with this POS doesn't even support 30 FPS.  The reason why I bought it is because the camera itself does support 30 FPS.  You need to go through a third party source to get 30 FPS.  

It's going to take forever to figure this out. *sigh*

BTW the software that came with it is junk!  It wouldn't install right in XP or 7.

---

