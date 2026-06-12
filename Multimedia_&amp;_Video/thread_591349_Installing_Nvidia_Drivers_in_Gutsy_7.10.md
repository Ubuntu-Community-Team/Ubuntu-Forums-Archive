---
title: "Installing Nvidia Drivers in Gutsy 7.10"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by reuyl on 2007-10-25
Hi folks. I'm running a FRESH INSTALL of 32-bit Gutsy with an Nvidia 6600GT, and I have absolutely no idea where to start installing drivers. I used Envy in Feisty, but it doesn't seem to work in Gutsy. I wouldn't consider myself a total n00b when it comes to Linux, but I sure feel like one when it comes to video card drivers.#-o

So, any help regarding Nvidia driver installation would be much appreciated:guitar:

---

### Post by sanddgroper on 2007-10-26
What happens when you use System->Administration-> Restricted drivers

Cheers
Sandy

---

### Post by ibizatunes on 2007-10-26
Install this
[www.getautomatix.com/](www.getautomatix.com/)

select your version of ubuntu

Select automatix > load app > click install nvidia drivers & other apps if you want> install > reboot 

Then check that restricted driver are in use! 

And your done!! Easy!!

---

### Post by Qwerty_ on 2007-10-26
Nah I would pass on automatix I have seen a few people having problems with automatix,

Just install via System>Administration>Restricted Drivers.

---

### Post by Steve1961 on 2007-10-26
The restricted drivers manager works fine with a 6600gt

---

### Post by PmDematagoda on 2007-10-26
I definitely do not recommend Automatix as I've had very bad luck with it, using Automatix is worse and in the end, more time-consuming than the manual way when considering the amount of problems you get when using it, I would recommend you to first try what Qwerty_ suggests.

---

### Post by Qwerty_ on 2007-10-26
Yes and just to as a confirmation for you I am running a 6600GT and I installed the restricted drivers flawlessly. Not a single thing messed up :)

---

### Post by chrx on 2007-10-26
its for feisty but is it any difference installing following this guide, Or installing via Administration>Restricted Drivers?

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#HOWTO:_Latest_NVIDIA_drivers](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#HOWTO:_Latest_NVIDIA_drivers)

---

### Post by PmDematagoda on 2007-10-26
Installing using the Restricted Drivers Manager is a pretty reliable way and it did install my Nvidia 6200 properly, so first give it a try, if it doesn't work, we can try other methods.

---

### Post by Maxymillion on 2008-01-21
Not for me

Just performed a clean install of Ubuntu 7.10, only thing i did was active the restricted driver, reboot. And I'm in safe graphics mode.

I spent days on my previous installed version of Ubuntu 7.10 with Envy and advice from every post so much as mentioning a 6600 video card. 

Do all these threads I've been reading apply for 64bit Ubuntu as well?!

---

### Post by PmDematagoda on 2008-01-21
> **Maxymillion said:**
> Not for me

Just performed a clean install of Ubuntu 7.10, only thing i did was active the restricted driver, reboot. And I'm in safe graphics mode.

I spent days on my previous installed version of Ubuntu 7.10 with Envy and advice from every post so much as mentioning a 6600 video card. 

Do all these threads I've been reading apply for 64bit Ubuntu as well?!

Well, as it is the Restricted Drivers Manager is not always effective and it may work on some PC's or hardware and may not work on others(But it does usually work well). 

Concerning whether you can follow advice in threads that concern 32 bit Ubuntu on 64 bit Ubuntu. In short, **yes** you can:).

---

### Post by notsatch on 2008-01-21
Another Linux newb here...

I just installed 32 bit 7.10 with restricted driver for my nvidia 7600 gt and everything works fine.  The only problem is the resolution and refresh rates I have to choose from are well below what my monitor (19" CTX EX951F) is capable of.  How do I correct this?

---

### Post by Maxymillion on 2008-01-21
notsatch, that would be sorted by the xorg.conf. Back up your xorg.conf and try running 

dpkg-reconfigure -phish xserver-xorg     will hopefully autodetect your monitor putting info into xorg.conf, then if other things have gone weird you can copy the refresh rate/resolution information from the new xorg.conf to the backed up one. 




Any suggestion's for what i can do?!   Clean installed 64bit Gutsy 3 times now, trying envy / restricted driver manager / manual ways of doing it. Starting to get abit flustered never had a piece of hardware so insistent on not working. My laptop with all its legacy hardware was easier :/. Tried old/new nvidia drivers. Don't do anything else, just standard start/install ubuntu, then first things first restricted manager or envy, reboot and safe graphics mode everytime :/

Currently installing 32bit so i can try the restricted manager with that :/

---

### Post by Maxymillion on 2008-01-21
Note before the 3 clean installs i wasted an entire week messing with the original install, trying every possible envy/restricted manager/sh nvidiadriver.run combination, cleaning the drivers and retrying in different ways, using apt-get to install nvidia-glx-new and nvidia drivers, blacklisting different nv modules, rebuilding xorg.conf, manually rebuilding xorg.conf using numerous guides vaguely relating to 6600 woes. Sorting through logs during all these was quiet unhelpful, got most every error at some stage from nvidia driver/kernel conflicts, to glx_ioerrors apparently caused by firefox/flash from the threads I read locking the system every 5minutes which isn't my issue. 

I'm no linux expert but I think I've been pretty thorough, out of ideas myself, its either throw the rig in the bin or get help :/

---

### Post by Maxymillion on 2008-01-21
*sigh*

Ubuntu 7.10 32bit clean install,   enable restricted driver manager, reboot, safe mode

syslog, this repeats itself  3 times i think for the 3 times it tries to load X

WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
CRITICAL: gdm_config_value_get_bool: assertion value->type == GDM_CONFIG_VALUE_BOOL ' failed




AMD FX53, MSI K8N Neo2 Platinum, Winfast AGP 6600GT

---

### Post by elcasey on 2008-01-24
Disregard

---

