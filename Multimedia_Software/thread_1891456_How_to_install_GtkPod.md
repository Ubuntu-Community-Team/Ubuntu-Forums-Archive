---
title: "How to install GtkPod?"
date: 2011-12-05
forum: Multimedia Software
---

### Post by PDA1 on 2011-12-05
I have spent DAYS trying to get GtkPod 2.0.1 installed in Ubuntu 11.04 but it simply doesn't work.

The ./Configure.....make.....make install is useless for installing it.  Then it creates error messages telling you to install some file, which when you go to find it, that requires a master's degree in computer science to even understand!

Sure, I can get version .99 which is in Synaptic and it sort of works.  By that I mean I can add a file to one of the out-of-alphabetic-order playlists but can't copy any music or videos back to the local drive.

Yamipod?  It doesn't even work.  Floola?  Slow as mud but sort of works.

Banshee?  Ugh.


Surely there has to be a program that'll manage an iPod?!  My iPod has over 4,200 songs on it including a pile of videos.

For the sake of mankind DO NOT tell me, ""have you tried "name a program" I've never tried but here's a link to it.""  

Having said all of that good stuff.....can ANYONE tell me exactly how to get GtkPod to work?

---

### Post by enjoijesus94 on 2011-12-05
open a terminal window:D


> sudo apt-get install gtkpod 

---

### Post by PDA1 on 2011-12-06
'Never heard that one before.

There are HUNDREDS of users who can't get GtkPod to work properly.  Sure it loads but beyond that there are numerous issues that haven't been fixed by the developers.

My thought is why even make programs like GtkPod which promise so much and deliver nothing but frustration?

---

### Post by stafio on 2012-01-03
GtkPod 2.1.0 is in the repositories for Ubuntu 11.10. You could try downloading it from there. 

You can download the .debs directly from the "Binary Packages" links on [_this page_]("https://launchpad.net/ubuntu/+source/gtkpod/2.1.0-1ubuntu1/+build/2733797"). The 64-bit packages can be found through [_this page_]("https://launchpad.net/ubuntu/+source/gtkpod/2.1.0-1ubuntu1/+build/2733795").

---

### Post by PDA1 on 2012-01-03
11.10?  I'm running 11.04


  Nuts.

---

### Post by stafio on 2012-01-03
> I'm running 11.04

Right, but I think you should be able to download the two .debs from 11.10 and install them in 11.04. Download the two .debs, open a terminal and navigate to the directory where you downloaded the files and run ```
sudo dpkg -i gtk*.deb
```

If there are any dependencies on other packages from 11.10 vs 11.04 it won't work, but it's worth trying.

---

### Post by PDA1 on 2012-01-03
I'll give it a try later today.  Something tells me I tried it before but it didn't work.

Do you have to execute all of that ./make ./configure, etc?

If so, I'm not one bit good at that stuff.

---

