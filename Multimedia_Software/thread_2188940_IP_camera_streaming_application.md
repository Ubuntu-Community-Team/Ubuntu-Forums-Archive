---
title: "IP camera streaming application"
date: 2013-11-19
forum: Multimedia Software
---

### Post by prkhr4u on 2013-11-19
I want to make a desktop application in C/C++ wherein i want to display the stream of various IPcameras that support MPEG-4 format(H.264 compression) over RTSP protocol.
It is just like some surveillance software wherein I display each camera stream in a separate tile.
Any ideas how to start this??

I am thinking of it using ffmpeg,although not clear how to do it.

P.S: using ubuntu 12.04

---

### Post by papibe on 2013-11-19
Hi prkhr4u.

I'd start by taking a look at what is out there: [motion]("http://www.lavrsen.dk/foswiki/bin/view/Motion/WebHome") and [ZoneMinder]("http://www.zoneminder.com/").

Both available via apt-get or the Software Center, btw.

Just a thought.
Regards.

---

### Post by prkhr4u on 2013-11-20
Thank you for the reply.Both motion and zoneMinder look good,but i am working on an application and i want to integrate the stream of 2-3 cameras in my GUI output(QT).
So I want some small solution,as i only want to stream the camera output and display them continuously.That's it.

Any other solution will be highly appreciated.

---

