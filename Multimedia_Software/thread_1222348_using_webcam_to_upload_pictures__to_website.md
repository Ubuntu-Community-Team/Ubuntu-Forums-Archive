---
title: "using webcam to upload pictures  to website"
date: 2009-07-24
forum: Multimedia Software
---

### Post by bundy75 on 2009-07-24
Hi I am trying to configure 'motion' to take a picture(jpeg) every 15 minutes and upload it to my web site. I have got the uploading part figured but I can't seem to turn off the motion detector and get it to just take a single picture every 15 mins. I am using juanty. Does anyone know if this is possible with motion or can someone recommend a package???

Thank

---

### Post by Gina on 2009-08-23
I haven't tried Motion but I have a webcam working with Ubuntu 9.04.  I'm using a command line application called **webcam** which captures an image and uploads it to a web site with FTP.  You can set the time interval between capturing images, the resolution and other things using a text config file.

I'm using it to provide a "weathercam" for my weather website, capturing an image (with time-stamp) every 5 minutes.

I've also been looking at **webcamd** which uses perl script and relatively easy for a programmer to modify.  I'm hoping to use this to do much the same but also provide a history of images on my web site.  So far I get an error trying to capture and it doesn't work.  I'm investigating.

---

### Post by jcnewbie on 2009-10-01
Hey Gina,

Thanks for the tip.  I installed "webcam" (as well as ftp daemon) and got this error with the config file below that. I don't have v4l running but I'm not sure I need it.  Any idea what I'm doing wrong?

I have a Dell Mini 9 with a built-in webcam.

Help!

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


Here is the .webcamrc file:
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

