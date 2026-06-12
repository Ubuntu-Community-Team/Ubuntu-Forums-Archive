---
title: "Creative Live! Cam Optia not working with stopmotion."
date: 2009-04-22
forum: Multimedia Software
---

### Post by Mr._Pickles on 2009-04-22
I'm a new Ubuntu user, slowly getting to grips with all the new ways of working (I mostly use XP), but still in need of some poiting in the right directon.

I'm trying to get my Creative Live! cam Optia to work with Stopmotion, but it's not working. It just comes up with a flat green image.

If I use VLC Player to open capture device I get a perfect image from the camera, better than running it under Windows.

I am running 32 bit Ubuntu Studio 8.10, and the camera is V4L2.

I know you people love code, so here is as much relevant code as I can find :)

lsusb returns

```
Bus 004 Device 003: ID 041e:4057 Creative Technology, Ltd Live! Cam Optia
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 2101:020f ActionStar 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```This:

```
vgrabbj -s /dev/video1
```Outputs this:

```
vgrabbj, Version 0.9.6
Videodevice name: /dev/video1 (Live! Cam Optia)
Capabilities
Type     : 1    Values can be looked up at videodev.h
Channels : 1
Audio    : 0
MaxWidth : 640
MaxHeight: 480
MinWidth : 48
MinHeigth: 32

Current Settings:
Brightness: 19661
Hue       : 32768
Color     : 24576
Contrast  : 21845
Whiteness : 28086
Depth     : 16
Palette   : YUYV (8)
Width     : 640
Height    : 480
Chromakey : 0
```If I try

```
vgrabbj -f test.jpg -d /dev/video1 -b -D 0 -i cif
```I get a plain green image, the same as in stopmotion.

I also tried

```
vgrabbj -f test.jpg -d /dev/video1 -b -D 0 -g
```with no change.

In looking for a V4L2 frame grabber I found Motion - [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome). I haven't tried it yet as I'm not really sure how to install it, what version I need, what dependant packages I need, how to get those and so on.

Hopefully that's enough info for someone to point me in the right direction.

Cheers

---

### Post by Junkieman on 2009-04-23
Hello Mr Pickles!

Same here, I'm using a Logitech Quickcam 3500. It works out of the box, but I just get a green image when I take a shot with Stopmotion.

Try [Cheese]("http://projects.gnome.org/cheese/") (install through Syntaptic), it is the only app that gets a picture out of the webcam, so I know the hardware is working.

Also have a read [through this topic]("http://ubuntuforums.org/showthread.php?t=931208&highlight=stopmotion") if you haven't already, I will post back if I find anything :)

---

### Post by Mr._Pickles on 2009-04-26
Cheers for the reply Junkieman, I was beginning to think that no-one had seen my thread...

I know that the hardware is working - I can get a great picture in VLC by doing open capture device.

I have read through the topic that you found as well, to no avail.

---

### Post by bmullan on 2012-08-25
I also had the Optia AF and although at one time it did work with linux (couple years ago) something in Video4Linux (V4L) changed and it is no longer possible to get it working.   After a couple months of on again off again research I concluded that the Optia AF is NOT UVC compliant.

So doing a little more research I found that its much less aggrevation to just go out and buy a new webcam.

All of the following are UVC compliant webcams.

I found that the Logitech HD Pro C910 ($79-$99) works very well with Ubuntu and it is 1080p capable but you should have a good CPU, enough memory etc to process it at that rate or just drop back to 720p.   The C910 has a 15 megapixel camera

So does the Logitech C310 ($45) which is also HD but 720p and has a 5 megapixel camera.

I settled on the C650 ($65) which is also 1080p or 720p HD and has a 8 megapixel camera.

I came home, plugged Logitech C650 and immediately it was recognized by Ubuntu 12.04 and worked.

So far I have used the following programs with it flawlessly:
camorama (sudo apt-get install camorama)
guvcview (sudo apt-get install guvcview)
skype (sudo apt-get install skype)

I am so glad I stopped screwing around trying to get that older Optia AF webcam to work as it was just a waste of time.

This Logitech C650's picture is just awesome.

---

### Post by overdrank on 2012-08-25
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

