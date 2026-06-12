---
title: "how install libgstreamer0.10-plugins-bad on ubuntu 16.04"
date: 2016-07-21
forum: Multimedia Software
---

### Post by Mattia_Adducchio on 2016-07-21
I can't find two gstreamer package on repository: 
[LIST]
[*]libgstreamer0.10-plugins-bad
[*]libgstreamer0.10-plugins-ugly
[/LIST]

How can install it on Ubuntu 16.04 64bit?
Is it safe to install 15.10 deb version?

---

### Post by Frogs Hair on 2016-07-21
I'm seeing them in synaptic, and were installed as part of the ubuntu-restricted-extras package.

---

### Post by Mattia_Adducchio on 2016-07-21
I have checked ubuntu-restricted-extras  but it contains packages for gstreamer1.0 not for gstreamer0.10.

---

### Post by mc4man on 2016-07-21
gst-0.10 has been removed though a couple of the base packages remain. What do you need it for?

---

### Post by Mattia_Adducchio on 2016-07-21
My application is compiled with qt4.8.5 and it require gstreamer0.10. 
in the past I have used your repository for Ubuntu 14.04, but now I would move to ubuntu16.04 to test the stability of the new Intel graphics driver.

Have you any idea? I'm trying to compile the plugin from the source with no result for now

---

### Post by mc4man on 2016-07-21
You *may* be able to install the 15.10 packages though you'd want to pre-install any deps that aren't in 16.04 first. libx264-146 would be one.
So download & install that first from here - 
[http://packages.ubuntu.com/wily/libx264-146](http://packages.ubuntu.com/wily/libx264-146)
Then download the ugly plugin from here, should install - 
[http://packages.ubuntu.com/wily/gstreamer0.10-plugins-ugly](http://packages.ubuntu.com/wily/gstreamer0.10-plugins-ugly)

And try the bad, may be more of an issue - , seems to need these 3 15.10 packages - 
Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-8.1ubuntu3)  
Depends: libsoundtouch0 (>= 1.8.0) 
Depends: libvpx2 (>= 1.4.0)
 
So browse the dep list at below & see if the 3 listed above can be installed, quick look suggests they can
[http://packages.ubuntu.com/wily/gstreamer0.10-plugins-bad](http://packages.ubuntu.com/wily/gstreamer0.10-plugins-bad)
So you'd need to get those 3 & see if they can be installed without causing issue...

all individual packages can be installed with apt, it will attempt to resolve deps, ex.'s
sudo apt install '/home/doug/Downloads/libx264-146_0.146.2555+git0c21480-1_amd64.deb'
sudo apt install '/home/doug/Downloads/gstreamer0.10-plugins-ugly_0.10.19-2.1ubuntu3_amd64.deb'

If you need to install a group at once then use dpkg

---

### Post by Mattia_Adducchio on 2016-07-26
I haveinstalled the ugly and bad packets, and I also added from your reposistory (**ppa:mc3man/gstffmpeg-keep**) gstramer0.10-ffmpeg. But when I try to play a video with this pipeline


gst-launch-12:10 playbin uri = file: /// ...


I get 

***stack smashing detected***

---

### Post by mc4man on 2016-07-26
> **Mattia_Adducchio said:**
> I haveinstalled the ugly and bad packets, and I also added from your reposistory (**ppa:mc3man/gstffmpeg-keep**) gstramer0.10-ffmpeg. But when I try to play a video with this pipeline


gst-launch-12:10 playbin uri = file: /// ...


I get 

***stack smashing detected***
not sure what -12:10 means but you'll not be able to play video with aac audio. aac audio only or video with some other audio codec should be ok. As far as solution hardly worth any effort. Better to move up to gst1.0 or use a distro release still on gst-0.10

---

### Post by Mattia_Adducchio on 2016-07-27
> **mc4man said:**
> not sure what -12:10 means but you'll not be able to play video with aac audio. aac audio only or video with some other audio codec should be ok. As far as solution hardly worth any effort. Better to move up to gst1.0 or use a distro release still on gst-0.10

Sorry, I mean -0.10. 
Before to move up to gst1.0 I will try to compile the plugin source, maybe it will be the last attempt. 

Thank you mc4man for your help.

---

### Post by mc4man on 2016-07-28
It could be the version of faad in 16.04 vs 14.04. The error, which is from a buffer overflow,  has occurred since 14.04 for some players though generally music. The solutions however aren't of much use here, in all cases they ported to gst-1.0

---

