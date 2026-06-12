---
title: "Webcam works.... sometimes"
date: 2010-07-20
forum: Multimedia Software
---

### Post by sdlyr8 on 2010-07-20
I'm trying to get my webcam working on ubuntu 9.4. Installed a few different programs to get it to work. streamer, cheese, webcam-server, motion and luvcview just to name a few.

My goal is I want to set it up on my old desktop (turned server) to monitor my apartment while I go out of town next week. The most luck I've had is with webcam-server, I can start the server and it takes a picture, but it's only ever that ONE picture. If I start cheese, I can see the video sometimes, but that doesn't start from command line.  Most of the other times, all I get is a grey image. 

I need something that just takes a single snapshot that will run from a bash script (or php, perl, etc). Any suggestions on getting rid of the grey picture? I've already spent a few hours trying different things but nothing is ever consistent...

---

### Post by no2498 on 2010-07-21
find the program called, motion

you will need to stop it yourself to turn it off

hope this helps you

---

### Post by sdlyr8 on 2010-07-21
I tried motion, but all I get is still that grey image :-( It sounds like that's what I want but the picture doesn't work and I haven't been able to access it outside of localhost..

---

### Post by soldier1st on 2010-07-22
what brand/name is the webcam? also did you try upgrading to the latest ubuntu release?

---

### Post by no2498 on 2010-07-22
try the cam in cheese webcam booth first


or if it dont come on try this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

