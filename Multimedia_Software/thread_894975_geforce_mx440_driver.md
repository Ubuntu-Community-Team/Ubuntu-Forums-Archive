---
title: "geforce mx440 driver"
date: 2008-08-19
forum: Multimedia Software
---

### Post by yenson on 2008-08-19
hello all, i just cant get my mx440 to work prefectly in my rig,any1 using the same card with me?which driver should i install

my rig
xubuntu 8.04.1 64bit
sempron 64
geforce 4 mx440
512mb of ram

i wonder if the problem is driver do not match with my 64bit hardy

---

### Post by benerivo on 2008-08-19
Is it nvidia-glx, and what do you mean by 'perfectly'?

---

### Post by yenson on 2008-08-20
> **benerivo said:**
> Is it nvidia-glx, and what do you mean by 'perfectly'?

i get shitty graphics and whenever i boot wit hthe driver installed,it tends to just white out at desktop,pls help me:confused::confused::confused::confused:

---

### Post by USAF Long on 2008-08-24
I had Ubuntu 7.10 working just fine with this graphics card. Then I updated it to 8.04 and now my max resolution is only 800x600.

I went to nVidia site and downloaded the "nvidia-linux-x86-96.43.07-pkg1.run" driver. I can't run it from the terminal even as SU. If I right click that file and then select "open with other application" and then choose "use a custom command" and type in "sh NVIDIA-Linux-x86-96.43.07-pkg1.run" my hard drive starts making noise and the light blinks, but after a minute it stops. Then I go to the screen resolution menu and I still have only a max of 800x600. I'd like at least 1024x768 or 1280x1024 resolution.

Am I doing something wrong? It worked great before I updated to 8.04 so something in the new kernel must have changed. When I go to system - administration - hardware and tell it to use the nVidia proprietary drivers, it downloads a package and then tells me to reboot. I reboot and my login screen is all messed up (has white boxes with missing background fill) but the text I type to login is noticeably smaller. When I log in, it lowers my max resolution down to 640x480 and that's as high as it can go.

Suggestions? Mine downloads nvidia-glx and then i used synaptic to download nvidia-settings but it only goes to 640x480.  I need at least 1280x1024

---

### Post by Unicast on 2008-08-24
I'd maybe try Envy.

It'll automatically detect your hardware and download / install the appropriate driver.

[http://albertomilone.com/envyngfaq.html](http://albertomilone.com/envyngfaq.html)

---

### Post by Cabel on 2008-09-12
HI, I am new to UBUNTU and have the same problem, I am running a p4 2.4ghz, 1028mb ram, Nvidia MX 440. 

My max resolution is 800x600 on the driver from the NVIDIA website. I have tried the 3 the nvidia packages in the add/remove programs (new, GLX, legacy) and none of these seem to work and the max resolution goes down to 640x480. I downloaded Envy and after installing this the max resolution is 640x480. 

I have edited the xorg.conf file to change to 'nv' instead of nvidia but will still not go above 800x600 or allow me to have the update the visual effects.

I have been working on this for a few days now and not really got anywhere (except possibly go back to an old graphics card which seems to give me a better resolution but is not the ideal solution).

please let me know if you need more info or what drivers you are using if anyone is successfully using this card, i really want to get this going!!!

---

### Post by Cabel on 2008-09-12
Turns out I just needed to set my monitor it may not have been the nvidia driver at all, i followed the directions below (unsure if the changes i made to the xorg.conf file etc. contributed however)

[http://ubuntuforums.org/showthread.php?t=221313&page=46]("http://ubuntuforums.org/showthread.php?t=221313&page=46")

[COLOR="RoyalBlue"]Well, long story short: I've installed Ubuntu 8.04 and everything was ok, then with the kernel update the drivers got screwed up, and I was stuck with a 640x480 resolution. The workaround that solved the problem:

1) Typed
Code:

gksudo displayconfig-gtk

2) On the window that showed up I could choose Screen1 > Generic > LCD 1280x1024 (in my case). It then asks to logoff, and so did I. Once the logon was done, the resolution was the correct one: 1280x1024. [/COLOR]

---

