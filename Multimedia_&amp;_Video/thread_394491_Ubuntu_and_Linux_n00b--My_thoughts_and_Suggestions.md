---
title: "Ubuntu and Linux n00b--My thoughts and Suggestions so far"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by twitami on 2007-03-27
So, I am n00b to all this stuff. It started because I had an old Compaq PC that wouldn't run much anymore, and a friend suggested installing Linux. Of course, I balked at the idea. However, he sent me a link to Ubuntu, and suggested I try it. I gave it a go..and was hooked. So, I put it on my old Compaq..then put it on another old Dell I got for free....then even set up a dual-boot on my Velocity Micro PC. The installs themselves went flawless. My other plan was to decide if Ubuntu is right for my 70 year old father, who just doesn't get Windows still. So...next I decide to get the actual GPU drivers goin....SMACK! It all slams to a halt at this point. I realize this is just the way things are, due to many factors. But, to make things worse, even in the Ubuntu forums alone, there are 50 different install guides..and they all seem to be different. Here are a few of the things that messed me up (some still have me that way):

1. From what I can gather, there are 2 versions of the drivers...Ubuntu ones and Nvidia ones..yes?

2. There are Legacy drivers for Older cards. Again, 2 versions here also?

3. I tried using the Restricted Drivers that seem to be included in Ubuntu, but theydidnt seem to do much..no GPU adjustments or anything that I could find.

4. HUGE ONE: Every guide I found to install the Nvidia drivers (save one) never had the code "chmod 770 ......". It took me HOURS to figure out I had to do that after downloading the drivers to my Desktop in order to install them (HUB-1, who's instructions I ended up going back to again and again, even leaves this out).

5. Once I did get things going on a few of my PCs, I wasn't sure how to check things to see if they really ARE working. Even now, my older Compaq (has a Geforce 4 Ti4400 in it) isn't set up right (although everything seems to work more or less). I get a "API Mismatch: the kernel module has the version 1,0-9631 (which is the one I need for this GPU), but this client has the version 1.0-9755 (which I know is the newest driver). I am guessing this happens somehow when the Nvidia installer builds a kernel. And on my Velocity Micro, I have a 7950GT GPU, and I am not sure how to check to see if EVERYTHING is on and set correctly. I know to look in Xorg, and look for NVIDIA and not NV, but I am not sure what to look for all the higher end GPU effects.

6. EASY Ubuntu is amazing..when it works. Again, I understand this is people on their own time..just stating that when this is more reliable, it makes Ubuntu VERY attractive for my Dad :)

Anyway, my 2 cents. 

Now, back to trying to figure out Beryl :)

Brian

---

### Post by simonn on 2007-03-27
> **twitami said:**
> 1. From what I can gather, there are 2 versions of the drivers...Ubuntu ones and Nvidia ones..yes?


Nope.

There are two drivers:

1) nv - which is the open source 2D driver

2) nvidia - which is the binariy (i.e. non-open source) driver supplied by nvidia

I suspect however that we are talking at cross purposes and you are really interested in the following. With open source, the general idea is that the authors of software write their software and supply it as source code. It is then up to the distributions to package it.

I suspect you are talking about the drivers in the Ubuntu repositories (i.e. available via synaptic , apt-get, aptitude etc) and the drivers you download directly from nvidia.

Nvidia supply the drivers, Ubuntu package them (in a wierd way IMHO) in the linux-restricted-modules package (or .deb if you prefer).


> **twitami said:**
> 
2. There are Legacy drivers for Older cards. Again, 2 versions here also?


Same as the above.

> 
3. I tried using the Restricted Drivers that seem to be included in Ubuntu, but theydidnt seem to do much..no GPU adjustments or anything that I could find.


They do work, however, you have to make sure that your xorg.conf is loading them correctly.

A quick way of testing is tp type the following in a terminal command line:

```

$ cat /proc/driver/nvidia/agp/status

```

This should return something like:

```

Status: 	 Enabled
Driver: 	 AGPGART
AGP Rate: 	 8x
Fast Writes: 	 Disabled
SBA: 		 Enabled

```

If it pretty much anything else is returned, the driver is not installed properly or at all.

> 
4. HUGE ONE: Every guide I found to install the Nvidia drivers (save one) never had the code "chmod 770 ......". It took me HOURS to figure out I had to do that after downloading the drivers to my Desktop in order to install them (HUB-1, who's instructions I ended up going back to again and again, even leaves this out).


This is a standard unix thing. Every file can be given execute permissions and needs to be given exectute permissions to be run... well kind of... The following will also work (replacing  [nvidia driver.bin] with the proper .bin file name:

```

$ sudo sh [nvidia driver.bin]

```

> 
5. Once I did get things going on a few of my PCs, I wasn't sure how to check things to see if they really ARE working. Even now, my older Compaq (has a Geforce 4 Ti4400 in it) isn't set up right (although everything seems to work more or less). I get a "API Mismatch: the kernel module has the version 1,0-9631 (which is the one I need for this GPU), but this client has the version 1.0-9755 (which I know is the newest driver). I am guessing this happens somehow when the Nvidia installer builds a kernel. And on my Velocity Micro, I have a 7950GT GPU, and I am not sure how to check to see if EVERYTHING is on and set correctly. I know to look in Xorg, and look for NVIDIA and not NV, but I am not sure what to look for all the higher end GPU effects.


This is because you installed the restricted drivers over the nvidia supplied drivers. Uninstall the restricted drivers completely and then reinstall the nvidi drivers. Note - you cannot (or at least it is difficult to) have the restricted drivers installed at the same time as the nvidia supplied drivers.

---

### Post by twitami on 2007-03-27
That clears up some things for me, thanks.

And yes, you are right in what I was talking about with the two different drivers. So Ubuntu gets drivers that are also made by Nvidia for their Dist., but they number them differently?

---

### Post by simonn on 2007-03-27
> **twitami said:**
> So Ubuntu gets drivers that are also made by Nvidia for their Dist., but they number them differently?

No. There is generally a lag between a distro packaging the latest version of a piece of software and when the developers release it. The ubuntu repositories do not (or did not - I have no idea which version is is in the repositories) have the latest drivers when you installed the restriced drivers package.

---

