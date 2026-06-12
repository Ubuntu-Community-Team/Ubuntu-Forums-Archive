---
title: "Problem with selecting video source..."
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by giorgosc61 on 2008-03-27
Hi, 
 
I want to use my Lifeview pcmcia card to get video-in for surveilance reasons on my Ubuntu installation. 
My card is correctly recognised in /dev/video1. 
When i use wxcam an select /dev/video1 it does not get signal from composite2 video source where my camera is connected. 
To get picture from wxcam I have to do the following: 
1)exit wxcam 
2)xawtv -c /dev/video1 
3)select from the xawtv menus composite2 as video source 
4)exit xawtv 
5)start wxcam and now I can get the correct picture from the video source 
 
I wonder if there is a possibility of selecting the video source and setting it in a config file, so as every time I start the wxcam application it displays the correct video source. 
 
Thank you in advance

---

### Post by opscure on 2008-03-27
The config file you are looking for is in:
/etc/X11/xawtvrc  or
$HOME/.xawtv

and the man page for it can be found here:
[http://linux.die.net/man/5/xawtvrc](http://linux.die.net/man/5/xawtvrc)

good luck.

---

### Post by giorgosc61 on 2008-03-27
Thank you thank you thank you......
Open console

nano .xawtv

[defaults]
capture = grabdisplay
input = Composite2


And now everytime i enter xawtv -c /dev/video0 it shows the correct image.:)

---

### Post by opscure on 2008-03-27
no problem

---

