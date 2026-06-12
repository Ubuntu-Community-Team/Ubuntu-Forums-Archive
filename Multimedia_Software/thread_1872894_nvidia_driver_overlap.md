---
title: "nvidia driver overlap?"
date: 2011-10-31
forum: Multimedia Software
---

### Post by lostinsauce on 2011-10-31
After installing the distro, I was stuck with 800x600 resolution so I installed the following nvidia driver from their website: NVIDIA-Linux-x86-270.41.06.run 

It installed fine and the resolution bumped up and everything was great.  I was able to install a few basic programs I wanted and it all seemed to go okay.  When I rebooted however, I wasn't able to install sun-java6-plugin.  After seeing the error during this particular installation, I've found that the same error occurs during nearly every type of installation.  The error that comes up every time is:     

Processing triggers for python-support ...  
Errors were encountered while processing:  nvidia-current  
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Looking further into it, I see that the very first thing that happens after unpackaging is this:    

Setting up nvidia-current (195.36.24-0ubuntu1~10.04) ... 
 Removing old nvidia-current-195.36.24 DKMS files... 
 ------------------------------ 
 Deleting module version: 195.36.24 completely from the DKMS tree. 
------------------------------ Done.  
Loading new nvidia-current-195.36.24 DKMS files...  
First Installation: checking all kernels... 
 Building only for 2.6.38  Building for architecture i686  Building initial module for 2.6.38       

So my question is, am I experiencing an overlap of my nvidia driver?  I installed 270-41-06, but apparently this distro came with 195.36.24, or at least it is what my kernel wants to load.  Any ideas on how I can fix this in order to install programs?  TIA

---

### Post by lostinsauce on 2011-10-31
Sorry for the first post being parsed without the returns.

---

### Post by BicyclerBoy on 2011-10-31
Do you know how to install the nVidia driver from the their website?
(kernel headers, console login, stop gdm X, etc)

I guess that your install did not work.

Just get the latest driver (as a deb package) from std repos or
xorg-edgers ppa or
x-swat team ppa

By using the nVidia driver install method you get the latest driver but your system breaks with every kernel update etc..

---

### Post by wildmanne39 on 2011-10-31
Hi, if your ability to install and remove packages is not completely broken I would remove the driver, then activate the one from additional drivers.
Thank you

---

### Post by lostinsauce on 2011-11-03
Removing the driver from nvidia's website and using the one from the standard repositories did the trick.  I had to clean out quite a bit of crap left over and rebuild the kernel module.

---

### Post by wildmanne39 on 2011-11-03
Hi, I am glad it helped.
Enjoy

---

