---
title: "Droid VNC"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by iamgeniusrnti on 2010-03-14
OK... I have a root'd moto Droid.  Best phone ever made!  Got a problem.  I pushed a VNC server into the Droid.  I fired it up and it works.  It listens on port 5901.  See screen shot.

Then I hop on my ubuntu and run vncviewer in the terminal and here is the output:

 Ultimate Edition 2.5
[http://ultimateedition.info/](http://ultimateedition.info/)
genius@k-laptop:~$ vncviewer 192.168.1.115::5901
Connected to RFB server, using protocol version 3.8
No authentication needed
Authentication successful
Desktop name "Android"
VNC server default format:
  16 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 31 green 31 blue 31, shift red 0 green 5 blue 10
Using default colormap which is TrueColor.  Pixel format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Using shared memory PutImage


Seems to work right?  Problem is all I see is a black screen with white blocks every now and then.  Did anyone here ever figure out how to VNC INTO the Droid?

For what it's worth, I got it to VNC out of the Droid and control my laptop.  Pretty cool actually, I set up a ssh pipe with port forwarding from the phone; badda bing, badda boom, I can control my laptop at home from work!

---

### Post by Excedio on 2010-10-28
Late reply...but here you go. :-)

[How To | Droid VNC Server]("http://goo.gl/JE1Q")

---

### Post by iamgeniusrnti on 2010-11-05
> **Excedio said:**
> Late reply...but here you go. :-)
 
[How To | Droid VNC Server]("http://goo.gl/JE1Q")
 
Holy crap!  That worked!  Hmm... now I just need to do a dyndns solution so I can remote control my phone while it's sitting in the car:D

---

### Post by Excedio on 2010-11-05
> **iamgeniusrnti said:**
> Holy crap!  That worked!  Hmm... now I just need to do a dyndns solution so I can remote control my phone while it's sitting in the car:D

I have a solution for that too. :D

[http://www.appbrain.com/app/dyndns/org.l6n.dyndns](http://www.appbrain.com/app/dyndns/org.l6n.dyndns)

---

