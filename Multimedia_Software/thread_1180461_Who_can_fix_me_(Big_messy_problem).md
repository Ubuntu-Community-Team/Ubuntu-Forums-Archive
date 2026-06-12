---
title: "Who can fix me? (Big messy problem)"
date: 2009-06-06
forum: Multimedia Software
---

### Post by pepperphd on 2009-06-06
Hi I'm Dr. Pepper, and Ubuntu 9.04 does not want to use my video card. When I first installed Ubuntu 9, it told me that if I wanted to use my 8600GT that I should download and install the proprietary, unsupported drivers. So I did that, restarted and I get this error (note that this is a crude approximation): 

  Ubuntu is running in low graphics mode because it failed to initialize your video card.  No screens found. Screen found, but no valid configuration.  And it boots me up in 800x600.   Nothing changes if I follow the instructions given to me by the Nvidia X Server settings manager:   

 You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  

 Doing so gives me the following garbage:   

 Using X configuration file: &quot;/etc/X11/xorg.conf&quot;. Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup' New X configuration file written to '/etc/X11/xorg.conf  

 I'll be here, watching this thread in case people decide to help me so I can post any information you think might be relevant to a diagnosis. I have no idea where to start, and the official documentation doesn't seem to come within a ballpark of what I need help with. I would have left it all alone but videos on screen were plagued with terrible frame rates and vertical sync problems.

---

### Post by RedRat on 2009-06-06
> **pepperphd said:**
> Hi I'm Dr. Pepper, and Ubuntu is giving me hell. When I first installed Ubuntu 9, it told me that if I wanted to use my 8600GT that I should download the proprietary, unsupported drivers. So I did that, restarted and I get this error (note that this is a crude approximation):  Ubuntu is running in low graphics mode because it failed to initialize your video card.  No screens found. Screen found, but no valid configuration.  And it boots me up in 800x600.   Nothing changes if I follow the instructions given to me by the Nvidia X Server settings manager:   You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  Doing so gives me the following garbage:  Using X configuration file: "/etc/X11/xorg.conf". Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup' New X configuration file written to '/etc/X11/xorg.conf  I'll be here, watching this thread in case people decide to help me so I can post any information you think might be relevant to a diagnosis. I would have left it all alone but videos on screen were plagued with terrible frame rates and vertical sync problems.

Two things did you download the proprietary or Nvidia X driver using Snaptic manager? From what you wrote it sounds as if you merely downloaded but not installed the driver. This seems to be an annoyance in Ubuntu both 8.04 to 9.04. You might want to download, via synaptic package manager, a program called envyng-core and envyng-gtk. 

Once installed, you can run it from the command line if it doesn't show up in your Applications>System Tools. Run this and it will go out and retrieve the appropriate driver. EnvyNG works fine with my setup which is 8.04LTS. This may be a late suggestion but for someone just starting out, I would suggest perhaps sticking with 8.04LTS, since it has most of the bugs worked out. I have seen what appears to be a stream of problems with 9.04 just because it is new.

---

### Post by pepperphd on 2009-06-06
I'm going to try what you said so this EnvyNG is currently being installed. The hardware drivers pane however tells me that &quot;This Driver is activated and currently in use&quot;. Even though the rest of the machine disagrees.

 EDIT: EnvyNG seems to have the same effect as the Hardware Drivers application. Nothing has changed.

---

### Post by RedRat on 2009-06-06
> **pepperphd said:**
> I'm going to try what you said so this EnvyNG is currently being installed. The hardware drivers pane however tells me that &quot;This Driver is activated and currently in use&quot;. Even though the rest of the machine disagrees.

 EDIT: EnvyNG seems to have the same effect as the Hardware Drivers application. Nothing has changed.

tell me, when you rung EnvyNG from the command line do you uses the following code:
sudo envyng

It is important that you run it as root using sudo or gksudo. Otherwise any changes don't seem to take affect. Same goes when you run nvidia-settings. You must run it using either sudo or gksudo, e.g.,
gksudo nvidia-settings

If you run nvidia-settings just by calling nvidia-settings, it will apparently run but the changes it writes to the xorg.config file do not take, since you need root priv to do that.

---

### Post by pepperphd on 2009-06-06
> **RedRat said:**
> tell me, when you rung EnvyNG from the command line do you uses the following code:
sudo envyng

It is important that you run it as root using sudo or gksudo. Otherwise any changes don't seem to take affect. Same goes when you run nvidia-settings. You must run it using either sudo or gksudo, e.g.,
gksudo nvidia-settings

If you run nvidia-settings just by calling nvidia-settings, it will apparently run but the changes it writes to the xorg.config file do not take, since you need root priv to do that.

 I used sudo.  Also I've lost sound with this most recent restart.

---

### Post by RedRat on 2009-06-06
> **pepperphd said:**
> I used sudo.  Also I've lost sound with this most recent restart.

Ok, there must be some other issues here. I run 8.04 and you are running 9.04 and I have seen similar problems with the newer version of Ubuntu. I hesitate to make any more suggestions and hopefully some 9.04 users might shed some light on this. I have seen here and in the usenet groups similar problems with the 9.04 release and video drivers. 

You might try this code:
sudo dpkg-reconfigure xserver-xorg

Some have had success with this. Sorry that I couldn't be of more help.:sad:

---

### Post by pepperphd on 2009-06-07
I thought I'd let anyone watching know that downgrading to 8.04 worked.

---

### Post by RedRat on 2009-06-07
> **pepperphd said:**
> I thought I'd let anyone watching know that downgrading to 8.04 worked.

I have found over the years that sometimes upgrading to the "latest and greatest" can be problematic. I bought a Dell with Ubuntu 7.10 pre-installed and it worked great but waited about 3 months before upgrading to 8.04 after it was released before installing it. Even then I had problems for several months, all seemed to be related to the video drivers. 

Ubuntu 8.04 is the LTS (Long Term Support) which means it is supported for about 2 years or more. For newbies, which I am even after about 2 years of using Linux, it is best to stay with the tried and true. As you become more familiar with Ubuntu, you might try upgrading to the later versions. For my purposes, 8.04 works very well and most of the Linux apps are OK. 

As I have blogged elsewhere, you are going to find many of the apps to have a somewhat unfinished feel to them, perhaps they are about 80% completed. But that is the nature of the open source community, they are volunteers. Perhaps that will change over the next few years, at least I hope so.

---

