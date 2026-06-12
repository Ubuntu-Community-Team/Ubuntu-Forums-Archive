---
title: "Webcam capture and FTP"
date: 2009-10-01
forum: Multimedia Software
---

### Post by jcnewbie on 2009-10-01
I'm a linux newbie running unbuntu 8.04 and have been trying to setup a webcam stream to show off my week old twin girls (gotta have something to do in between diaper changes).

I read post after post and decided to go for the simplest approach: have my webcam capture and FTP a jpg to a www server every second, displayed on a html page that's refreshed using a header refresh every second or so.  You can see the simple webpage here:
[http://www.spotretrieve.com/lexitalicam.html](http://www.spotretrieve.com/lexitalicam.html)
(it's a static image right now)

I found a post suggesting the command line program called webcam to capture and upload the jpg using a built-in webcam on my Dell Mini 9.  However, I can't seem to get the webcam program to work and don't have a clue what I'm doing wrong. I'm not sure how to turn the webcam on in command line and not sure where it's output goes. 

Can anyone with experience with the program webcam or built-in webcams on the dell help me out?  My questions are
1) what am I doing wrong with webcam?  I installed a ftp daemon + the command line app "webcam", and created a configuration file for the app.  I do NOT have video4linux installed.  I ran webcam and what I got is below.  
2) Is there an easier webcam capture and upload program that I can use?
3) Is there an easier way in general to do this?

Many thanks,
deperate new daddy

What I got when I tried running webcam:
zoe@zoe: ~$ webcam
reading config file: /home/zoe/.webcamrc
/home/zoe/.webcamrc:1: error: no section
/home/zoe/.webcamrc:2: error: no section
/home/zoe/.webcamrc:3: error: no section
.
.
/home/zoe/.webcamrc:30: error: no section
/home/zoe/.webcamrc:31: error: no section
v4l2: open /dev/video0: No such device
v4l2: open /dev/video0: No such device
v4l: open /dev/video0: No such device
no grabber device available


Here is the .webcamrc config file:
       device = /dev/video0
       text = "webcam %Y-%m-%d %H:%M:%S"
       fg_red = 255
       fg_green = 255
       fg_blue = 255
       width = 640
       height = 480
       delay = 3
       wait = 0
       input = composite1
       norm = pal
       rotate = 0
       top = 0
       left = 0
       bottom = -1
       right = -1
       quality = 75
       trigger = 0
       once = 0

       host = [xxxxxxxx.com]("http://xxxxxxxx.com/")
       user = [EMAIL="webcam@xxxxxxxx.com"]webcam@xxxxxxxx.com[/EMAIL]
       pass = xxxxxxxx
       dir  = public_html/webcam
       file = webcam.jpeg
       tmp  = uploading.jpeg
       passive = 1
       debug = 0
       auto = 0
       local = 0
       ssh = 0

---

