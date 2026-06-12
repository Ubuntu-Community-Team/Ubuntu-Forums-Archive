---
title: "logitech quickcam pro 9000, will it work ?"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by Bert_2 on 2007-09-10
Well, as the title says, will a logitech quickcam pro 9000 work on my desktop and if so, which drivers should I download and install ?

(I'm searching a nice webcam that works with ubuntu and that has a very good quality and well, the pro 9000 really gives top quality, HD all the way :D )

I haven't bought it yet so I can't post terminal outputs, but I can't find information about it on the forum (only older pro webcams and other logitechs) and v4l isn't very clear about it.

---

### Post by linuxwizard on 2007-09-10
According to this it is supported.
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by Bert_2 on 2007-09-11
Sorry man but I can't load the first link and the second says that some other quickcam pros are supported but nothing about the 9000, but perhaps I didn't have a good look at it.

But it was already very helpfull and if the pros all use the same chipset I don't need to check anymore (but that's one of the things I don't know)

---

### Post by linuxwizard on 2007-09-11
That website must be having problems. I use that site often never had issues with it before. Try it later it does show your webcam you are looking at.

---

### Post by Bert_2 on 2007-09-11
Okey, the link works now and now I know it's supported, thank you veyr very very much :D :D :D

---

### Post by kosson on 2007-11-23
Some positive experience ?

For me ?!? only Ekiga works and that's it !

Hmmm this cam has the best quality I ever seen but to what use as we cannot use it tot the max in Linux ?

---

### Post by Bert_2 on 2007-11-24
Well, I have chosen a logitech quickcam pro for notebooks and I seems to work, only kopete doesn't want to work with it but I think it's a port related problem.

---

### Post by tuque on 2007-11-24
Uvc is installed but it doesn't work in Skype, 
Also fails to work in Canorama with the error message, "could not connect to video device (/dev/video0) "

lsmod | grep videodev
videodev 29312 1 uvcvideo
v4l1_compat 15364 2 uvcvideo,videodev
v4l2_common 18432 2 uvcvideo,videodev

The camera works in Cheese (although the image is poor, blurred) so I guess V4l2 is running ok.
Rather puzzling as reports suggest this camera works without issues. It's bound to be something simple that I have or haven't done but for now it's got me beat.

---

### Post by rsambuca on 2007-11-24
Have you compiled the latest uvcvideo drivers?

---

### Post by tuque on 2007-11-24
Yes, as far as I can tell. I used;

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

---

### Post by lingnoi on 2007-12-25
This camera works for me in Skype but I have to plug in a different web cam and then this one, so that the Logitech Pro 9000 is in /dev/video1

After you do that it'll work in Skype.

Anyone know how to get this web cam working without having to have another web cam plugged in?

---

### Post by asnd16 on 2008-01-08
yeah the day people get this thing working let me know !!! I have tried many things. . ..

---

### Post by Nevell on 2008-01-10
> **tuque said:**
> Uvc is installed but it doesn't work in Skype, 
Also fails to work in Canorama with the error message, "could not connect to video device (/dev/video0) "

lsmod | grep videodev
videodev 29312 1 uvcvideo
v4l1_compat 15364 2 uvcvideo,videodev
v4l2_common 18432 2 uvcvideo,videodev

The camera works in Cheese (although the image is poor, blurred) so I guess V4l2 is running ok.
Rather puzzling as reports suggest this camera works without issues. It's bound to be something simple that I have or haven't done but for now it's got me beat.
I have the same problem!

---

### Post by wjston on 2008-01-10
> **Nevell said:**
> I have the same problem!

have you tried typing luvcview into a terminal to see whether your camera works with Luvcview? If so, and the camera turns on and you see yourself, post the results of luvcview -L. You should see a number of different frame rates and video screen sizes that your camera can support. The part you should look for and post (everything from this line down)t is - pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }.

Go to your home folder>press Ctrl_H and this should show all hidden folders in your home folder. Navigate to the .Skype folder and then the folder with the config.xml file in it. Right click on the file and choose>open with> then choose either a text editor or Bluefish editor or some other editor that will allow you to add information. Add the part that I highlighted in red or a Height and Width that works for you. This hopefully will help. OK, here is the information I added to my config.xml file from my .Skype folder (located in /my_home_folder/.Skype/my_username/config.xml):
<Video>
<AutoSend>1</AutoSend>
[COLOR="Red"]<CaptureHeight>600</CaptureHeight>
<CaptureWidth>800</CaptureWidth>
<Device>/dev/video0</Device>
<Fps>25</Fps>[/COLOR]
</Video>

---

### Post by Nevell on 2008-01-15
> $ luvcview -L
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
/dev/video0 does not support read i/o
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/15, 1/10, 1/5, 
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 160, height = 120 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 176, height = 144 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 320, height = 240 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 352, height = 288 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 640, height = 480 }
        Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 800, height = 600 }
        Time interval between frame: 1/25, 1/20, 1/15, 1/10, 1/5, 
{ discrete: width = 960, height = 720 }
        Time interval between frame: 1/10, 1/5, 
{ discrete: width = 1600, height = 1200 }
        Time interval between frame: 1/5, 


I'm add into the /my_home_folder/.Skype/my_username/config.xml):
<Video>
<AutoSend>1</AutoSend>
<CaptureHeight>720</CaptureHeight>
<CaptureWidth>960</CaptureWidth>
<Device>/dev/video0</Device>
<Fps>15</Fps>
</Video>
also i tried 320@240@30fps

Next, i'm start the Skype, press the TEST button, then  i see black image and after 15-20 sec. Skype is crashed (close). 
P.S. Kopete, Cheese work with my cam... But after my experiments with the other drivers i see in the luvcview not more 5 fps...

---

### Post by wjston on 2008-01-17
> **Nevell said:**
> I'm add into the /my_home_folder/.Skype/my_username/config.xml):
<Video>
<AutoSend>1</AutoSend>
<CaptureHeight>720</CaptureHeight>
<CaptureWidth>960</CaptureWidth>
<Device>/dev/video0</Device>
<Fps>15</Fps>
</Video>
also i tried 320@240@30fps

Next, i'm start the Skype, press the TEST button, then  i see black image and after 15-20 sec. Skype is crashed (close). 
P.S. Kopete, Cheese work with my cam... But after my experiments with the other drivers i see in the luvcview not more 5 fps...

Have you tried reinstalling the latest uvcvideo driver? You will need to install subversion first. It is in the repository.
svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/)
cd linux-uvc/linux-uvc/trunk
make
sudo make install

---

### Post by Nevell on 2008-01-21
I have lastest version...

---

### Post by wjston on 2008-01-21
> **Nevell said:**
> I have lastest version...

Does the orange light around the lens of the camera come on when you run the test or have tried other calls?

---

### Post by Nevell on 2008-01-25
No, orange light dont ON... If I run luvcview everythink all right...

---

