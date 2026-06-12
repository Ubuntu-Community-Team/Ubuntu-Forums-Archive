---
title: "Philips Webcam Recording Problems"
date: 2010-07-01
forum: Multimedia Software
---

### Post by DedMoroz on 2010-07-01
Ive got a cheap webcam purchased from ebay for $5. It works fine in Ubuntu 10.04 as its V4L (video 4 linux) compatible and I use it to record in cheese, no problem.

The quality of that webcam is not very good, so I decided to pick up a nicer higher quality cam. I purchased a Philips SPC1330NC webcam.

Cheese no longer can record video using this new webcam. It does see the webcam and show the live feed, but recording will either crash Cheese completely, or divide the video image in half and turn everything green.

Browsing around on Ubuntu wiki and help pages I came across some code to record from terminal directly to an AVI file. It WORKS! Here is the code...

```
mencoder tv:// -tv driver=v4l2:width=1600:height=1200:device=/dev/video0 -ovc lavc -o webcam.avi

```

Now for my question & thanks for reading through... Obviously the camera works fine in Ubuntu, so how do I get this going with Cheese so I can record?

Many thanks in advance!

---

### Post by no2498 on 2010-07-01
try this program wxcam

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

read and install all the page tells you to

it comes in a deb file also



as far as the green thing i cant help with 

i have the same thing on 910

804 im fine
enjoy the new program

---

