---
title: "046D:09a1 Logitech Quickcam Communicate MP camera Driver"
date: 2008-07-06
forum: Multimedia Software
---

### Post by xx.canes.rites on 2008-07-06
Hi how are you,

My name is Robert. I have recently switched from Windows XP over to Linux Ubuntu/Hardy Heron, yet I find myself in somewhat of a predicament. I have a Logitech G5 mouse on my Ubuntu setup which works fine on my computer, but my camera just refuses to even turn on mainly because of the lack of driver components it needs to operate as intended.My VID/PID is under "Thread Subject".Also I don't want to forget to mention that not only did I just recently switch over to Linux system, but it is my first time ever even being on a linux, but don't be scared to help me because I'm an absolutely quick learner. I follow directions very well, and if I could just be pointed in the right direction as to where I should start I would be so grateful. If there is no known working drivers for my camera I would love to be informed as to where I should start as to getting a known working driver code, and maybe just changing it myself to get my camera working and how I go about doing that.Thank you very much for even reading my post and investing your time into helping me :)

p.s. Is everyone that uses Ubuntu or any other Linux system a certified developer or something LOL! I need a Linux for Dummies book or maybe just a good website to show me the ropes, so if you could just shoot me a URL or something I would appreciate it.I switched from windows over to Linux kernel just to show my support even though I really had no idea what to do once I got into a linux distro.I'm a computer gamer so being a Linux dummie is really killing me right now haha, I just installed wine to get my games working and im still struggling with that, but if I don't get this camera working my roommate gonna kill me, cause I lied to her and told her windows crashed and I had to install new OS LOL so help me out guys haha!!

---

### Post by Resnick on 2008-07-07
Hey there. I too have the same camera;

```
$ lsusb
Bus 003 Device 003: ID 046d:09a1 Logitech, Inc. 
```

Take a look at the Linux UVC project over @ [http://developer.berlios.de/projects/linux-uvc/]("http://developer.berlios.de/projects/linux-uvc/"). I believe it supports our camera model. I just switch to Ubuntu a couple of days ago, and found it to already contain the uvcvideo module. 

(P.S. You may want to keep an eye on [this thread]("http://ubuntuforums.org/showthread.php?p=5340684#post5340684") as both myself and achortleaday are having issues with our Logitech Quickcams.)

---

### Post by Resnick on 2008-07-07
Forgot to add, I am new to Ubuntu as well and found a couple of things helpful.
[https://help.ubuntu.com/]("https://help.ubuntu.com/") and the help application that appears in the top panel answered some of my initial questions. I have used linux for a while, but I am sadly by no mean proficient at it :D

---

### Post by xx.canes.rites on 2008-07-10
Yo I've already added the USB UVC linux drive and it doesnt work on amsn or any other program I use. Linux always gives me issues with all the drivers I try to install, I hate windows, but at least its simple to install required drivers...zzzzz.. I wish linux would just be more user friendly

---

### Post by markbuntu on 2008-07-11
I got my Logitech Quickcam Communicate STX to work by getting V4l with Synaptic and using it instead of V4l2 which seems to be the default installed item. 

I used Ekiga to figure this out. With V4l2 selected as the video plugin in Edit/Preferences/Video Devices it could not find my camera when I checked Detect Devices but after I installed V4l and told Ekiga to use that, it found the camera by name and then cheese, etc, also worked.

I did not do anything else, no drivers, nothing and it works on both my 64bit and 36bit Hardy installs.

---

### Post by baosheng on 2008-07-15
does anyone know what is the version of uvcvideo in Ubnuntu 8.04? I just wanna make sure whether Ubuntu could support the Quickcam Communicate MP out of the box, or I need to download the driver and install it.

---

### Post by jlg317 on 2009-12-23
Bus 001 Device 004: ID 046d:08c3 Logitech, Inc.

I just started using Ubuntu, and so far everything works just fine, but the above mentioned camera, does anyone know of any package or driver I can get to make it work? feel free to break it down in your simplest terms, since I am a rookie using Ubuntu or any type of Linux OS.

---

