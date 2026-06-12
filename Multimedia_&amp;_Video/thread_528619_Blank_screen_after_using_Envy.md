---
title: "Blank screen after using Envy"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by poekinoeni on 2007-08-18
Hi All

Hope there is someone that can help me out, I've just upgraded my PC and reinstall 7.04

Here are the specs of my new PC just in case there is an issue with the hardware compatibility :
Intel Core 2 Duo E6750
Asus P5N-E SLI
2 Gig Ocz Ram
160 Gig HDD
2 x Bfg 8800Gts 320

When I installed the restricted drivers (nvidia-glx-new) via Synaptic I get the blue screen when the XServer fails. It was taking to long to try and get that working so I read through all the forums and decided to try Envy ( which has an excellent working rate ).

It downloaded and installed everything without error but on restart I get a blank black screen when the Nvidia logo should display and I can hear the Ubuntu tune play when the login screen appears. 

Trawling through some more forums I found that it could be something to do with EDID ( not to sure ). The advice was to add this line.

Option "ModeValidation" "NoVertRefreshCheck"

This seems to work and I can login and test the 3D using "glxgears -info"

BUT it seems to fix my resolution at 640x480 which is unusable, I have tried everything to change the resolution but nothing seems to work. 

My only work around now is to remove that above line and use the vesa driver which allows me to use the resolution at 1680x1050 but then no 3D.
It would be nice to have this working to be able to use the desktop effects and some 3D games.

I don't need the SLI working but would like some 3D.

Hope there is someone that can help. I have attached my Xorg.0.log if there is any other info needed just ask. 

thanks

---

### Post by tseliot on 2007-08-18
set the driver to "nvidia" and restart the Xserver.

then type:
```
sudo nvidia-settings
```

and set the refresh and resolution from there

---

### Post by poekinoeni on 2007-08-18
Thanks for your quick response.

When I try using nvidia-settings the largest resolution is 640x480 or below.

It seems to be the Option "ModeValidation" "NoVertRefreshCheck" that forces the system to that res but if I remove it I get the blank black screen so it seems to be the only way of booting into Ubuntu at the moment when using the nvidia driver.

:(

As a test I put 1 of those video cards ( 8800 GTS ) into a Dell Dimension 8400 and that works fine with nvidia-glx-new drivers ??

Would like to get everything working in the new PC rather.

---

### Post by tseliot on 2007-08-18
It might depend on the motherboard.

Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by poekinoeni on 2007-08-18
Thanks for your help.

I've posted the same question on that forum if I can find out a solution for my problem I'll post it here.

Thanks for Envy it is really good.

---

### Post by poekinoeni on 2007-08-21
tseliot:
Thanks for your help.

I sorted the issue, I did try that other forum but had no joy. I installed the restricted drivers from Ubuntu (nvidia-glx-new) and fix the lib problem with the link below.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)
(Followed the post by  Aaron D. Campbell )

FYI
The weird thing is after trawling through forum after forum I decided to test my hardware, thinking there could be a problem with it, so I installed Vista 32bit (thinking Windows must work). 
I had the exact same problem after installing lastest NVidia drivers for Vista32, on the windows forums they spoke about the EDID not being detected (same as the Linux version ) if I uninstall the NVidia driver and used the Microsoft Nvidia drivers through their auto updates everything works fine. 
As a second test I installed XP everything worked fine first time.
So I thought there must be something with the NVidia drivers I decided to reinstall Ubuntu and try their restricted drivers again as mentioned above.

I'm a happy boy now.

I want to try and get this working with Envy as I think you have done a great job with this project as it works with my other systems.

---

### Post by tseliot on 2007-08-21
> **poekinoeni said:**
> tseliot:
Thanks for your help.

I sorted the issue, I did try that other forum but had no joy. I installed the restricted drivers from Ubuntu (nvidia-glx-new) and fix the lib problem with the link below.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)
(Followed the post by  Aaron D. Campbell )
I'm the one who provided the 2 patches in that bugreport. I hope the developers will commit my fix soon.

---

### Post by poekinoeni on 2007-08-22
oops, saw that now! :)

thanks again.

---

### Post by pkarlos_76 on 2007-08-24
A solution I found was the system was showing a fake monitor in the Xorg.0.log, so I switched my DVI cable from the 2nd DVI port to the 1st DVI port on the video card and I got my desktop back, the 2nd DVI port was working find under vesa drivers, but doesn't seem to work under nvidia drivers for me. It is possible to use override statements too,but changing connector is more easy.

---

