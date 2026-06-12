---
title: "Idiot needs help, please?"
date: 2010-04-22
forum: Multimedia Software
---

### Post by ky5u on 2010-04-22
I have tried every idea I have read to try to get a camera server up with a picture.  WebcamStudio nobody seems to know how to get broadcaster to work.  I downloaded webcam-server and apache and installed them.  I started the server and when I send an invalid file request in my browser to ["http://localhost/bogusfile"]("http://%22http://localhost/bogusfile%22") I get an Apache message saying "not found", so I know the server is up and running.  When I run "http://localhost/webcam.html" in the browser I get "Done" on Firefox, but no picture.  When I try "http://localhost:8888" I get a Firefox box same as you get when you try to browse a site that does not exist.

I tried "camstream" and find no option to send video to localhost.  Cheese, WebcamStudio and camstream all find my webcam, and show it with no issues.

THIS IS WHAT I WANT TO DO:

I want a program to put 1 or 2 video snapshots from my webcam every second into a file "cam_1.jpg" on [http://localhost:8080]("http://localhost:8888"), so when I enter "http://localhost:8080/cam_1.jpg" in my browser I get a snapshot.  As fast as I hit refresh, I would get an updated picture.  I admit to not being smart enough at this point to write my own program.

Any suggestions besides things biologically impossible?  Thanks!!

Charlie

P.S.- I belong to a webcam net group on Ham Radio.  They use this format to update their server with pictures.  WebcamXP in Winders does it.  I worked with Evological on "evocam" to have this functionality for MACs.  I'd like people with Ubuntu Linux to be able to join us as well, which is why this is important.  Thanks again.

---

### Post by ky5u on 2010-04-23
I figured it out.  Syntax error in a script that prevented webcam-server from reading the webcam.  Looks like nobody has webcam issues besides me...  

:guitar:

---

