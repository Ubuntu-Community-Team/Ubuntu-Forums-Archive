---
title: "capturing video with cheese does not work"
date: 2010-09-02
forum: Multimedia Software
---

### Post by toffifeemann on 2010-09-02
hey,
so i've been trying for a while now to capture videos with my webcam of my samsung n110 netbook, im running ubuntu 10.4 and cheese 2.30.1
i can take pictures fine, with effects and everything but when i press "start recording" the webcam seems to turn off or all i see is a black image, then when i press stop recording the camerapicture comes back on and then the program freezes
i've tried turning down the resolution, ive tried all the possibilities in gstreamer-properties but nothing helped so far
running from terminal didn't give me a clue on what the problem might be either
hope someone can help me
i would like cheese to work to have photo and video in one program but if someone has a good program to capture video im willing to try it out 
thanks in advance!

---

### Post by no2498 on 2010-09-03
try this 1 wxcam
read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by toffifeemann on 2010-09-03
i tried it and im not a big fan...
the video i record is playing way too fast, the sound is very bad if existent at all and there's a green line at the bottom of the video and also a part of the video that is supposed to be on top is on the bottom below the green line
so no fixes for cheese?

---

### Post by no2498 on 2010-09-03
try changing the size of the video 
cheese has a nice help file look in its faq's

---

### Post by toffifeemann on 2010-09-04
hey,
by size you mean resolution? because then i tried all the possibilities without any luck, also read the helpfile and it didnt help me...
thanks for the response though!

---

### Post by no2498 on 2010-09-05
retry the same thing with cheese

---

### Post by toffifeemann on 2010-09-06
doesn't help for the respecitve problem in either of the programmes...

---

### Post by no2498 on 2010-09-06
did you do this from the cheese help faq's

My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.

---

### Post by toffifeemann on 2010-09-29
hey,
so i tried it (after a while now, sorry) and it gave me these errors and warnings, the first ones about screenshots showed up immediatly as soon as the program started
the ones after that dont look like they are the errors that are causing my problem, do they?
anyway, i tried all the possibilities in gstreamer-properties without any luck
i can also enter this in the bugreport, but it doesnt look like it is describing the bug that causes the problem to me somehow
here we go:


** (totem-video-thumbnailer:7570): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:7570): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:7570): WARNING **: Could not take screenshot: no video info

** (totem-video-thumbnailer:7570): WARNING **: Could not take screenshot: no video info


** (totem-video-thumbnailer:7570): WARNING **: Could not take screenshot: no video info
totem-video-thumbnailer couldn't get a picture from 'file:///home/paul/Videos/Webcam/2010-09-10-102658.ogv'

** (cheese:7568): WARNING **: could not generate thumbnail for /home/paul/Videos/Webcam/2010-09-10-102658.ogv (video/ogg)

totem-video-thumbnailer couldn't process file: 'file:///home/paul/Videos/Webcam/2010-08-27-131427.ogv'
Reason: Took too much time to process.

** (cheese:7568): WARNING **: could not generate thumbnail for /home/paul/Videos/Webcam/2010-08-27-131427.ogv (video/ogg)

---

