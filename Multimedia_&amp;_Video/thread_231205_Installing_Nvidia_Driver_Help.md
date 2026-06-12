---
title: "Installing Nvidia Driver Help"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by CeeDub on 2006-08-07
I am a huge newbie to linux, so I need quite a bit of help.  I'm trying to install the Nvidia driver (GeForce4 440 Go 64M).  I downloaded the driver from the Nvidia website.  The instructions say to run this command:

sh NVIDIA-Linux-x86_64-1.0-8762-pkg2.run

It runs, but it encoutners an error.  It says that X server is running and that I need to stop it.  How do I do that?  I first tried booting to GRUB and the the recovery mode (or whatever it's called).  But the installer comes up with more errors.  I've tried changing the /etc/inittab/ default init runlevel, but that freezes my computer on boot.  I'm really a newbie, so any help would really be appreciated. Thanks

---

### Post by 5-HT on 2006-08-07
Do you know that the nvidia proprietary drivers are available in the repositories? You may find that much easier than installing the ones from nvidia's site. 

The following excellent guide describes three different ways of installing the drivers (incl. from the repositories and nvidia's binaries) and also mentions how to stop X to do the install: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I would recommend you follow method 1.

Hope that helps.

---

### Post by Sutekh on 2006-08-07
This would be the best guide to help with installing NVIDIA drivers.

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

It's gotten really huge over time, but it's all there.  Method 1 is still the easiest way to go, and installs the drivers from the Ubuntu repositories (v8762).

There is no need to stop X, run sh NVIDIA-Linux-.... or any of that, it can all be done using Synaptic/apt-get.

... After looking at the guide again, it does look difficult to read, so sing out if you are stuck, and we can go through step by step.  But it really is easy if you try Method 1.

---

