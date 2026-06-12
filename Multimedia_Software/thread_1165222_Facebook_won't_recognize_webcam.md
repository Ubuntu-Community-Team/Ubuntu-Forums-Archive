---
title: "Facebook won't recognize webcam?"
date: 2009-05-20
forum: Multimedia Software
---

### Post by Tombo5150 on 2009-05-20
Hi there. I recently purchased an Xbox 360 Vision camera and got it setup with skype and such on my computer. However, when I go onto facebook to try and record a video of myself on someone's wall, facebook never sees the webcam? Has anyone run into any problems like this?

---

### Post by Arup on 2009-05-20
Do you have latest Java 1.6.13 update installed?

---

### Post by Tombo5150 on 2009-05-20
Pretty sure. I checked in the package manager and it says I've got the latest sun-java8-bin 6-13-1. Is that what I want or something else?

Tom

---

### Post by Arup on 2009-05-20
> **Tombo5150 said:**
> Pretty sure. I checked in the package manager and it says I've got the latest sun-java8-bin 6-13-1. Is that what I want or something else?

Tom

Nope you are fine and do you have Flash installed? If you are using x64 install Flash 10 alpha x64.

---

### Post by Tombo5150 on 2009-05-20
Pretty sure I've got that, I can watch youtube vids just fine. There isn't anymore I need to download for that right? The plugin on the page is there, but it just sits at the search with the icon in the middle like its looking for the camera. One time I actually had it say it couldn't find the device, but not it just sits there like its looking for it and nothing else happens passed that. :-!


EDIT 5/21/09 :
When it says it can't find a device, is when I am using another application with the webcam. When I am not using any other apps with the cam is when it keeps the search for a device going and nothing happens.....

---

### Post by xc3RnbFO8P on 2009-05-21
Read this:
[http://forums.sun.com/thread.jspa?threadID=5271863]("http://forums.sun.com/thread.jspa?threadID=5271863")
and this:
[http://www.linuxquestions.org/questions/linux-software-2/how-to-install-java-media-framework-jmf-on-ubuntu-522362/]("http://www.linuxquestions.org/questions/linux-software-2/how-to-install-java-media-framework-jmf-on-ubuntu-522362/")
[http://forums.sun.com/thread.jspa?threadID=5368614&tstart=1]("http://forums.sun.com/thread.jspa?threadID=5368614&tstart=1")

---

### Post by Tombo5150 on 2009-05-21
Okay, I followed those links and tried it however the output when executing the file goes like this:

```
JavaSound Capture Supported = true
JavaSoundAuto: Committed ok
Name = v4l:Video Camera           :0
Trying 4 320 240
Trying 3 160 120
Trying 3 320 240
Trying 3 640 480
Trying 3 176 144
Trying 3 352 288
Trying 3 768 576
Trying 4 160 120
Trying 4 320 240
Trying 4 640 480
Trying 4 176 144
Trying 4 352 288
Trying 4 768 576
Trying 5 160 120
Trying 5 320 240
Trying 5 640 480
Trying 5 176 144
Trying 5 352 288
Trying 5 768 576
Trying 6 160 120
Trying 6 320 240
Trying 6 640 480
Trying 6 176 144
Trying 6 352 288
Trying 6 768 576
Trying 7 160 120
Trying 7 320 240
Trying 7 640 480
Trying 7 176 144
Trying 7 352 288
Trying 7 768 576
Trying 8 160 120
Trying 8 320 240
Trying 8 640 480
Trying 8 176 144
Trying 8 352 288
Trying 8 768 576
Trying 9 160 120
Trying 9 320 240
Trying 9 640 480
Trying 9 176 144
Trying 9 352 288
Trying 9 768 576
Trying 10 160 120
Trying 10 320 240
Trying 10 640 480
Trying 10 176 144
Trying 10 352 288
Trying 10 768 576
Trying 11 160 120
Trying 11 320 240
Trying 11 640 480
Trying 11 176 144
Trying 11 352 288
Trying 11 768 576
Trying 12 160 120
Trying 12 320 240
Trying 12 640 480
Trying 12 176 144
Trying 12 352 288
Trying 12 768 576
Trying 13 160 120
Trying 13 320 240
Trying 13 640 480
Trying 13 176 144
Trying 13 352 288
Trying 13 768 576
Trying 14 160 120
Trying 14 320 240
Trying 14 640 480
Trying 14 176 144
Trying 14 352 288
Trying 14 768 576
Trying 15 160 120
Trying 15 320 240
Trying 15 640 480
Trying 15 176 144
Trying 15 352 288
Trying 15 768 576
java.lang.Error: Can't open video card 1
java.lang.Error: Can't open video card 2
java.lang.Error: Can't open video card 3
java.lang.Error: Can't open video card 4
java.lang.Error: Can't open video card 5
java.lang.Error: Can't open video card 6
java.lang.Error: Can't open video card 7
java.lang.Error: Can't open video card 8
java.lang.Error: Can't open video card 9

```

---

### Post by xc3RnbFO8P on 2009-05-22
See if this helps:
[http://ubuntuforums.org/showthread.php?t=624669]("http://ubuntuforums.org/showthread.php?t=624669")

---

### Post by no2498 on 2009-09-05
go to the adobe web site
settings manager
click
 allow
remember 
fot the web site you use

---

### Post by sneham429 on 2011-10-26
Hey, I had the same problem with my built in webcam on my acer aspire one happy 2. 
I realized that I hadn't correctly installed the Google Video Chat plugin, and decided to see if Facebook would recognize my webcam after I correctly installed the plugin. It did. 
I followed the directions from [http://www.ubuntuupdates.org/ppas/47]("http://www.ubuntuupdates.org/ppas/47"), and facebook recognized my camera immediately after. 
Hope that helps.:)

---

### Post by sneham429 on 2011-10-26
Speaking of, I Googled the Facebook problem first, and tried the other things mentioned on this page. They didn't work for me.

---

