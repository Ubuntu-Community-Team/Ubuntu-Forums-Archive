---
title: "Roadblock streaming webcam"
date: 2010-11-03
forum: Multimedia Software
---

### Post by TechSupportx86 on 2010-11-03
lets just get down to business. I have an apache server here that i would like to add a webcam to, to stream video to a webpage hosted on said server. Now i hit some trouble using 10.10 with v4l2 not being able to make use of my webcam. 

So this is where i stand right now:
I have ubuntu 9.10 Server installed
Apache2 (good install, shows default page on networked computers)
Static IP of 192.168.1.4
openssh (works fine)
Samba sharing /var/www to my windows machine
Logitech C120m connected via USB 2.0

I have tryed 2 guides using both webcam-server and VLC, Neither worked however one would show a single frame when i connected to the webpage when i tryed on other ubuntu desktop, but wouldn't refresh unless i rebooted. I tryed the webcam on my other 9.10 computer and it worked fine with cheese (Video0 is there on the server)

The server has pretty much a clean install with nothing on it (yet). I have 3 empty 40GB hard drives, so installing and testing another release of ubuntu is **_not a problem_** if you think it might solve my problem. Any and all opinions welcome, this is starting to annoy the crap out of me ;)

---

### Post by P4man on 2010-11-03
Im not sure I understand where the problem lies. Are you having trouble capturing images from the webcam, or is it just a matter that the images are not refreshed in the browser (but they are on the drive) because they are being cached by the browser?

(also: why are you sharing /var/www ? Are you uploading the images via a windows machine which is connected to the webcam?)

---

### Post by TechSupportx86 on 2010-11-03
The problem is when i use webcam-server, the webpage shows up with the javaapplet (black window with play, pause, ect), but no video will play. If i try [http://localhost:8888](http://localhost:8888), it'll show a single frame taken from when i connected to the stream, and won't refresh. 

so the problem is it seems to be setup correctly, but i am still not getting any video. 

Here are the guides (maybe someone can see the problem?)
[http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server)
[http://forum.videolan.org/viewtopic.php?f=13&t=39050](http://forum.videolan.org/viewtopic.php?f=13&t=39050)

Also the sharing of /var/www is for uploading and modding the webcam.html page, as well as the others.

---

