---
title: "V4L2 Webcam Utilities?"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by JNowka on 2007-03-18
I have been looking for some Video 4 Linux 2 webcam utilities.  I just can't seem to find any so far.  The only time I have been able to use my web cam was when i downloaded ekiga, a voip program.  I would like a program that can make videos and take snapshots.  If anyone knows of any V4L2 webcam utilities that I may have overlooked, I would appreciate being told what they are.

Thank you in advance.

---

### Post by badiruz on 2007-03-19
hi :)

which web cam do you use for ubuntu linux ... I want to have one that works on ubuntu ... I will appreciate very much if  you can give some suggestions ... 

thanks

bahadir:)

---

### Post by buildid on 2007-03-19
creative webcam nx ultra , out of box working

---

### Post by JNowka on 2007-03-21
Hello,
My webcam cam built in to my laptop.  It uses the linux-uvc webcam driver that requires video 4 linux 2 to use the webcam.  Seeing that most if not all webcam utilities use video 4 linux 1, I find myself unable to use my webcam with anything but ekiga.  I wish to  be able to take pictures and make little movies to send to my family and friends on the other side of the states, so that they can see me again after 3 years.  If anyone know of any webcam **utilities** that I can use with v4l2, it would be very appreciated if you could direct me in the right direction.  I have been looking for weeks off and on, and can't seem to find any.
 Thank you in advance.
 JNowka

---

### Post by drpaul on 2007-03-21
Amen to that. Where are they?

Paul

---

### Post by JNowka on 2007-03-27
*bump*

---

### Post by nodcero on 2007-06-25
Exhausted from my fight with webcams and drivers, but apparently winning, I think that post is well worth bumping, maybe something _is_ out there... ;)

---

### Post by Cymru Boyo on 2007-06-28
> **nodcero said:**
> Exhausted from my fight with webcams and drivers, but apparently winning, I think that post is well worth bumping, maybe something _is_ out there... ;)

I know how you feel!

After 3 day I've finally got my Logitech QuckCam for Notebooks (ID 046d:09c1) to work using the V4L2 drivers, following advice from several threads and a bit of luck from the Ubuntu gods.  

After that effort it would be nice to be able to do something with it other than use Ekiga, like taking still photos or record videos.

There must be something out there.  Any ideas?  :-k

---

### Post by hostcord on 2007-07-01
I've been trying to get this to work but so far no luck. Maybe someone can.

[http://ronald.bitfreak.net/cupid.php]("http://ronald.bitfreak.net/cupid.php")

---

### Post by drpaul on 2007-07-01
Can't seem to find a path to the "stable" version on the gstreamer site. Not adventurous enough to check out the CVS. ???

Paul

---

### Post by howlingmadhowie on 2007-07-03
you can try gqcam

that allows me to take single pictures (using a video4lin2 device). i'm still working on the video...

---edit---

xawtv works for me, but only with the -nodga option (it may be something about the nvidia driver)

---

### Post by Icarosaurus on 2007-07-08
Try VideoView.
You can find it here (32 and 64 bit versions)
[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")
Works with my camera but should it work with a generic one.

---

### Post by acorey on 2007-07-15
Is it me, or is it really strange fo a person to post a link here that asks you to;
1. Pay for software. 
and
2.Pay to some paypal account before getting the software in an email??!!!!!

WTF!!!!

---

### Post by YannickDefais on 2007-07-23
Hi,

To take pictures, you can try camorama and camstream as well.

Regards,
Yannick

---

### Post by drpaul on 2007-07-23
My bad news is that some "recent" update has broken the camera in Ekiga. Now nothing works with the built-in cam.

Paul

---

### Post by YannickDefais on 2007-07-23
Hi,
@drpaul,

Can you report this here please:
[https://bugs.launchpad.net/ekiga/+bugs?&field.scope=project&field.scope.target=ekiga](https://bugs.launchpad.net/ekiga/+bugs?&field.scope=project&field.scope.target=ekiga)

PLease provide your unbuntu version, ekiga version, webcam name and what's reported by the command line "lsusb" and your kernel version by the command line "uname -a". Thank you.

My guess is you installed the webcam driver by yourself. If the kernel upgrade, you often must reinstall the webcam driver to get your webcam work again.

Regards,
Yannick

---

### Post by drpaul on 2007-07-23
I've looked all over my computer, and I don't find any evidence of having installed v4l or v4l2 manually. Yet I know that Ekiga didn't run until v4l2 was loaded.

????????

Thanks for the help. I'll file the bug.

Paul

---

### Post by YannickDefais on 2007-07-23
Hi,

V4l and V4L2 are kernel API, i.e. a standard way to talk to your driver webcam inside the kernel. Your driver webcam is something like gspca, linux-uvc, etc. They are kernel modules.

Regards,
Yannick

---

### Post by sglow on 2007-07-25
I found links to a couple handy utilities that work with the linux-uvc driver at least.  I don't know if they will work with other V4L2 drivers.

luvcview ([http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz](http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz))  is a simple utility that allows you to display the view from the camera on screen.  It is also documented as producing a video file, but I can't get that to work at the moment.

uvc_stream ([http://naaa.de/programme/uvc_streamer/uvc_streamer_2007_07_11_20.55.20.tgz](http://naaa.de/programme/uvc_streamer/uvc_streamer_2007_07_11_20.55.20.tgz)) is based on the luvcview sources and acts like a web server for the camera.  It is reported to work with the motion program ([http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)), but I haven't tried that yet.

Seems like there is a fair amount of work yet to be done with V4L2 devices, but these simple utilities are a start at least.

Good luck,
Steve

---

### Post by drpaul on 2007-07-25
Yannick

I'm running on a laptop, so I reboot daily. Today I went to look at /dev and surprise! video0 was there and Ekiga now works.

I don't know what is going on. 
Do you have any suggestions that might milk some useful info from my machine? What should I do with that bug I filed on Ekiga?

Clueless but not in Seattle

Paul

---

### Post by xealous on 2007-08-28
i had the same problem. i hava an a4 tech webcam. it works with live cd but when i install feisty it just stops working. i can only use it with ekiga and camorama gives the usual error. after few reinstallations i realized that it's because updates. before update feisty it works just fine, after update it stops working again and a can only use my cam with ekiga. before someone finds a solution to this i won't update and thats my solution.. :D

---

### Post by kpturvey on 2007-10-18
> **howlingmadhowie said:**
> you can try gqcam

that allows me to take single pictures (using a video4lin2 device). i'm still working on the video...

---edit---

xawtv works for me, but only with the -nodga option (it may be something about the nvidia driver)

It crashes when I try to use it (gqcam).  Segmentation fault.  

The latest development snapshot of monitor works with my webcam.  (V4L2 only).

---

### Post by Depressed Man on 2007-10-18
Try Cheese Photo App (it's like Photobooth for Macs)

---

### Post by julianramon on 2007-11-06
This last one was my solution! Thanks. I used Synaptic Package Manager with Universe and Restricted activated and it was there in the list of packages available. Just look for "cheese" and that's it\\:D/

---

### Post by googleaseerch on 2007-11-11
Nothing else had worked for me, but cheese did the trick (video too!).  Many thanks. :D

---

### Post by Left hand of Gaia on 2007-11-17
> **Cymru Boyo said:**
> I know how you feel!

After 3 day I've finally got my Logitech QuckCam for Notebooks (ID 046d:09c1) to work using the V4L2 drivers, following advice from several threads and a bit of luck from the Ubuntu gods.  

After that effort it would be nice to be able to do something with it other than use Ekiga, like taking still photos or record videos.

There must be something out there.  Any ideas?  :-k

Cymro Boyo, I have the same camera, what did you have to do to get it working?  Any good links?

LHoG

---

### Post by imon9 on 2008-03-30
as many linux user notice, flash perviously only supported v4l webcam, while most of the new distro is using v4l2 as standard driver and v4l2 is also the standard driver embedded in the kernel.

So, most of us who has new webcam (especially those build-in) are using v4l2 driver and dont have the opportunity to use webcam based flash sites like:
[www.mebeam.com](www.mebeam.com)
[www.flixn.com](www.flixn.com)


NOW YOU CAN!!!

a developer wrote a loopdriver for webcam, you can get it from his website:
[http://www.swift-tools.net/Flashcam/](http://www.swift-tools.net/Flashcam/)

---

### Post by FrankVdb on 2008-03-30
I was going to recommend Cheese but someone ran off with it before I had the chance. :)

---

