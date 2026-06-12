---
title: "What packages excately needed to play youtube videos in Totem Movie Player"
date: 2008-12-17
forum: Multimedia Software
---

### Post by lidengdeng on 2008-12-17
Hi, when my Totem movie player tries to play Youtube videos online, I get an error which reads "Totem cannot play this type of media (YouTube) because you do not have the appropriate plugins to handle it". According to its information, I installed the following packages:
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad
gstreamer0.10-ffmpeg
gstreamer0.10-Pitfdll

But I still meet the same error after I have stalled those packages and run the Totem move player again.

Any help??
thanks

---

### Post by wolfen69 on 2008-12-17
go [here]("http://get.adobe.com/flashplayer/?promoid=DXLUJ") and download the .deb file for ubuntu and click to install. then restart totem or firefox.

---

### Post by gandaran on 2008-12-17
> **lidengdeng said:**
> Hi, when my Totem movie player tries to play Youtube videos online, I get an error which reads "Totem cannot play this type of media (YouTube) because you do not have the appropriate plugins to handle it". According to its information, I installed the following packages:
gstreamer0.10-plugins-base
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad
gstreamer0.10-ffmpeg
gstreamer0.10-Pitfdll

But I still meet the same error after I have stalled those packages and run the Totem move player again.

Any help??
thanks
you do need a gstreamer plugin for totem not adobe flash plugin for firefox, I don't know exactly which gstreamer plugin to install, I usually  install all of them except the doc and debugger ones,  if you running ubuntu 8.10 install the ubuntu-restricted-extras, this package nearly installs all gstreamer plugins but watch out it also installs adobe flash so if you install the adobe flash from adobe.com remove one of them either the one from synaptic or the one from adobe.com

---

### Post by meka4996 on 2009-05-23
Try this one...
[http://ubuntuforums.org/showthread.php?t=1103825](http://ubuntuforums.org/showthread.php?t=1103825)

---

