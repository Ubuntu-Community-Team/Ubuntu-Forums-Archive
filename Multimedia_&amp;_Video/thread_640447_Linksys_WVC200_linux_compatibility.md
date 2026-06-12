---
title: "Linksys WVC200 linux compatibility"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by jbcola on 2007-12-14
I just wanna share my experience with the Linksys WVC200 Wifi IP Camera

On linux, you can capture the stream with this URL:
[http://IP_OF_CAMERA/img/video.asf](http://IP_OF_CAMERA/img/video.asf)
or
[http://IP_OF_CAMERA/img/mjpeg.cgi](http://IP_OF_CAMERA/img/mjpeg.cgi)
(The connection needs basic authentification, so for mplayer use [http://user : password at IP_OF_CAMERA/](http://user : password at IP_OF_CAMERA/)...)

The only drawbackis the exclusive compatibility of the web interface with IE, firefox is not supported for live streaming.

Best regards,

---

### Post by Pakkanen on 2008-01-19
Beforementioned authentication method applies also when using VLC.

---

### Post by jbcola on 2008-01-21
Maybe someone knows how to use "motion" with a webstream?
This should then work with the WVC-200....

---

### Post by freechelmi on 2008-07-22
Hi Jbcola , after Few months lokking for a decent 100 $ IPCAM, I'm willing to buy this one , But the worst Part is the need for activeX to make the PanTilt Works. 

Did you try to run their software on Wine ? 

the good point is the OpenSource Firmware , I really like it.

---

### Post by freechelmi on 2008-07-23
Good news !! 

I find out that , as opposite to the "cheap" Ip Cam , this linksys Cam is really nice to use with any OS : 

Here is a stream of a Cam in Max Video Res : 

[http://cam3.hdvideo.ca:1026/img/video.asf](http://cam3.hdvideo.ca:1026/img/video.asf)

you get a nice MP4 +G726 ( all FFmpeg readable ) and so you can record the stream by yourself. SO that's for the video part. 

But there is even better news 

the Web interface 
[http://cam3.hdvideo.ca:1026](http://cam3.hdvideo.ca:1026)

apart from the activeX if you are on IE, Give a Nice CGI based interface to control the Cam with almost all the function you can find in the ActiveX, so it's even possible to Ditchthe Win software and make your own....

So Even if it's a bit expensive, the linux friendlyness and opens ource firmware will make this mine :-)

---

