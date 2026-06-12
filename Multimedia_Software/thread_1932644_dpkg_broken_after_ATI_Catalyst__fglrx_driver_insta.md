---
title: "dpkg broken after ATI Catalyst / fglrx driver install"
date: 2012-02-27
forum: Multimedia Software
---

### Post by ninenagon on 2012-02-27
Hello Ubuntu Forum, 

Hope someone can shed light on this frustrating problem:

I typically boot my Ubuntu 11.04 from a 8 gig usb flash drive, on my Sony PCG-TR3AP laptop. I've been using this method for a few years, no problems and on various computers other than my own.

FYI, the Sony TR3AP Graphics Card: Intel 855GM Chipset Integrated Graphics

[http://www.amazon.com/Sony-PCG-TR3A-Laptop-Pentium-Centrino/dp/B00017H7QW](http://www.amazon.com/Sony-PCG-TR3A-Laptop-Pentium-Centrino/dp/B00017H7QW)


Recently I booted my Ubuntu usb flash drive on a HP PAVILION DM1. 

[http://www.amazon.com/HP-Pavilion-dm1-3020us-Entertainment-Laptop/dp/B004H0OA7S/ref=cm_cr_pr_product_top](http://www.amazon.com/HP-Pavilion-dm1-3020us-Entertainment-Laptop/dp/B004H0OA7S/ref=cm_cr_pr_product_top)

I was curious to experience the HP's 'AMD Radeon™ HD 6310M' graphics performance, and installed the ATI proprietary driver to my Ubuntu usb flash drive. (I recall installing it via a sh script which I've since deleted).

Here's when the problem started...

Now, when I boot my Ubuntu usb flash drive on the Sony TR3AP and attempt installing or removing anything, I experience the following error:

'E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.'

I've attempted running 'sudo dpkg --configure -a' a few times which result in the 'fglrx' module configuring, and 'depmod' filling the terminal screen with sequential dots, which run endlessly, until it fills up all remaining free space on my Ubuntu usb flash drive!

The main issue: I can't use 'apt-get' to install or remove anything. Very frustrating to say the least.

How should I proceed?

Thank you,

---

### Post by Johnny Buffalkill on 2012-02-28
I think the problem is that you installed the ATI graphics drivers, but  now you're running a pc that has intel graphics.  I'm actually surprised  its working as well as it is.

I would try reverting back to the  open source graphics drivers and see what that does.  It is a bit of a  process this guide makes it a matter of cutting and pasting into  terminal.

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

Give it a try and see if it fixes things.

---

### Post by ninenagon on 2012-03-01
Thanks for your quick reply Johnny, 

My ubuntu usb flash drive boots on any computer, (except I can't install or remove any applications). Graphics architecture doesn't seem to affect it.

Thanks, I remember the 'http://wiki.cchtml.com/index.php/Ubu...talyst.2Ffglrx' in my travels.

Unfortunately I can't process the 'apt-get install / remove' commands due to 'dpkg' being broken ('apt' is a front-end for 'dpkg'). All attempts lead to the error message: 'E: dpkg was interrupted, you must manually run sudo dpkg --configure -a to correct the problem'.  

I have a feeling, when I initially tried installing the ATI 'fglrx' driver (via the HP laptop), it wasn't configured correctly. Which is why executing 'sudo dpkg --configure -a' reconfigures the 'fglrx' driver and for some reason depmod fills up all remaining space on my drive (last time I had 1 gig free).

The main issue seems to be 'dpkg'.

Furthermore I don't know where to start looking for the files the depmod process created, in order to reclaim the space used.

Hopefully someone has some insight.

---

### Post by ninenagon on 2012-03-12
For anyone interested in the solution to this thread, I found the following page helped:

[http://linux.koolsolutions.com/2009/03/30/a-comprehensive-command-guide-to-debians-apt-get-and-dpkg/](http://linux.koolsolutions.com/2009/03/30/a-comprehensive-command-guide-to-debians-apt-get-and-dpkg/)

dpkg commands which worked for my situation were:

"dpkg --remove fglrx"

"dpkg --purge fglrx"

After running "dpkg --remove fglrx" the system started configuring DKMS which I had to interrupt using "CTRL C" a few times as it was filling up my usb flash drive's free space to capacity again. 

When I tried "dpkg --purge fglrx" I also tried "dpkg --purge fglrx-amdcccle" and every fglrx related package indicated from the link Johnny kindly supplied:

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

Specifically at this line:

"sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx"

After a while the system reported using an alternative diversion and then dpkg miraculously started working again and apt-get was working as well.

I removed all traces of "ati / amd" from my system using synaptic and now all is well much to my relief after 4 months of frustration!

Hope this helps anyone with similar issues.

---

