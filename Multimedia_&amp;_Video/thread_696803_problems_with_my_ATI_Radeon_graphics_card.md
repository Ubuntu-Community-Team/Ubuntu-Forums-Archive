---
title: "problems with my ATI Radeon graphics card"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by jorik42 on 2008-02-14
hi; im not sure if this is the best/most correct place to direct this post, but, i suppose ill learn.  

I am currently having problems using my ati radeon hd 2600 graphics card on ubuntu 7.10.  Admittedly, im new to ubuntu (and linux in general) so this may be nothing more than my compounded ignorance, but i find that there is a low degree of plausibility for that.  

I have been perusing forums and google, ect for the past couple weeks, trying to find a solution.  With that said, here is the issue:

     It doesnt work.  When i attempt to enable desktop effects, it tells me (only) that they cannot be displayed.  when i look at the device manager (system->preferences->hardware information) there is no ati graphics card listed.  when i type lspci into the command line, the only mention of ati is:

01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9581
01:00.1 Audio device: ATI Technologies Inc Unknown device aa08

I have tried updating the driver as per [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
but when i update/use the restricted drivers, it tells me that "your system does not need any restricted drivers."  

thinking that perhaps i had the driver, i followed the above links instructions to manually install via the command line, and the result that i get is:

jorik@jorik-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages

Further, i have tried going manually into system->administration->screens and graphics and assigning the driver, however, it will not change from using the VESA generic driver (likely because it does not detect the graphics card).  


thusly, I am not quite sure how to proceed or what to do. I apologize if this post is overly long, but i was trying to be thorough.  ^_^

anyhow, any help would be appreciated

thanks
    -jorik

---

### Post by Giannis68 on 2008-02-14
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

** Enable "restricted" Repository **

 Make sure the *restricted* repository is enabled in */etc/apt/sources.list* or this guide will not work! 
System > Administration > Software Sources.  Check "Proprietary Drivers for Devices (Restricted)" box. 

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

---

