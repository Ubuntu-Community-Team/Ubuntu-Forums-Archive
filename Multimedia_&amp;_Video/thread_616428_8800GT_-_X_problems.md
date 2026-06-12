---
title: "8800GT - X problems"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by bluefightingcat on 2007-11-18
Hi,

I recently upgraded my computer. I've been using Kubuntu Feisty and Gutsy for a while now and I completely happy with Kubuntu. However I tried to install Gutsy on my new machine. 

I've had major problems. I had to install using the alternative CD. The live-CD simply wouldn't work. Now when I start my installation I end up at the commandline instead of KDE. It seems X-server fails to start. 

I have the new NVIDIA 8800GT and I've tried all the advice on this forum but so far nothing has worked. 
I even tried installing the latest NVIDIA drivers. 

Anybody got any advice? I have a AMD64 system. 

BFC

---

### Post by aoanla on 2007-11-18
> **bluefightingcat said:**
> Hi,

I recently upgraded my computer. I've been using Kubuntu Feisty and Gutsy for a while now and I completely happy with Kubuntu. However I tried to install Gutsy on my new machine. 

I've had major problems. I had to install using the alternative CD. The live-CD simply wouldn't work. Now when I start my installation I end up at the commandline instead of KDE. It seems X-server fails to start. 

I have the new NVIDIA 8800GT and I've tried all the advice on this forum but so far nothing has worked. 
I even tried installing the latest NVIDIA drivers. 

Anybody got any advice? I have a AMD64 system. 

BFC

Well, as you will have noticed, only the newest nvidia driver (169.04) will work with the 8800GT - the driver on the live CD for Gutsy is a bit older than that, so it didn't have a chance.

Which "latest" driver did you try to install? 169.04? 
What does your /var/log/Xorg.0.log look like?
Do you have "nvidia" as the driver loaded in your xorg.conf, not "nv" or "vesa"?
You may also like to follow this thread:
[http://www.nvnews.net/vbulletin/showthread.php?t=101476&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=101476&page=6)
where some people (but not all - it seems to depend on the maker of your card) are having issues with getting their 8800GT detected by the new driver.

---

### Post by bluefightingcat on 2007-11-18
Hi,

Thanks for your input. I tried 100.14.19 version of the driver. The latest one won't work because it is 32-bit so it throws errors. So it seems that I am going to have wait until NVIDIA come out with a 64-bit version of the driver. 

BFC

---

### Post by njparton on 2007-11-18
When you install make sure you chose the safe graphics option and remove splash and quiet from the options (F6 I think?).

This should give you a working new installtion using the VESA drivers and you should be able to install the nVidia drivers from there.

---

### Post by aoanla on 2007-11-18
> **bluefightingcat said:**
> Hi,

Thanks for your input. I tried 100.14.19 version of the driver. The latest one won't work because it is 32-bit so it throws errors. So it seems that I am going to have wait until NVIDIA come out with a 64-bit version of the driver. 

BFC

Well, 100.14.19 definitely won't work.

And, um, there *is* a 64bit version of the 169.04 driver...

[http://www.nvidia.com/object/linux_display_amd64_169.04.html](http://www.nvidia.com/object/linux_display_amd64_169.04.html)

(nVidia always release both versions at the same time)

---

### Post by bluefightingcat on 2007-11-18
Ohh!! my bad. Let me give it a try and see what happens. 

BFC

---

### Post by bluefightingcat on 2007-11-18
Hi,

The driver worked great. However for some reason X still doesn't want to start automatically. 

All the stuff loads as usual but when it gets to the line:

Running local boot scripts (/etc/rc.local) the system just stops. When I press enter I get a login prompt. I can login into my account and I have to manually enter "startx" for KDE to turn up. 

Strange!

BFC

---

### Post by aoanla on 2007-11-18
That is odd. Is it possible that you're not going to runlevel 5, but stopping at runlevel 3?

---

### Post by bluefightingcat on 2007-11-18
Could be. But how do I check and how do I force it to go to run level 5?

BFC

---

### Post by Wipster on 2007-11-18
Hey, just a little bit of input I was tinkering about inside my computer and took bits out and my computer froze when I got to that stage of boot, I found that my graphics card had changed its PCI address location so I edited xorg.conf to match, might be worth checking that it hasn't done somehting daft like that.

---

### Post by bluefightingcat on 2007-11-19
Thanks for the info. However my system started randomly working after a couple of reboots. Really strange but everything is fine now. 

BFC

---

### Post by themindrecoils on 2007-11-24
I'm having a similar issue where the driver works immediately after I install it (stopping and starting gdm, no reboot), but won't pick it up after I reboot (gusty starts up using vesa driver).   Reinstalling lets me use it until the next reboot.  Anyone else seeing anything like this?

---

