---
title: "Can the USB Video Capture Device HU3192-E work in Ubuntu?"
date: 2014-09-07
forum: Multimedia Software
---

### Post by ienne on 2014-09-07
Hello.

I just purchased Roxio Easy VHS to DVD 3 Plus.

I am a pretty experienced PC user but I am a total newbie to video  capture. The product in question works perfectly on my Windows 7 laptop. I  realized that I can use the included USB converter (labelled HU3192-E, more precise details below) also with  programs such as VLC, and works perfectly fine too.

I was thus wondering if I could connect the USB converter to my Ubuntu  machine (xubuntu 13.10) and capture VHS output with VLC on it. I tried  to insert it and no driver seems to be loaded for it even though the  device is recognized (it appears in lsusb, dmesg gives a reasonable output, etc.--see below for more details).

I searched for a while through Google, but I could not get any  conclusive result--not even to understand whether this is possible or  not.... [This closed post]("http://ubuntuforums.org/showthread.php?t=2099142") says that it is incompatible, [this later post]("http://ubuntuforums.org/showthread.php?t=2167360") seems to clearly imply that it works (almost) fine--whereas nothing at all works for me.

This is the closest to describe my situation: [http://www.linuxtv.o...xioEasyVHStoDVD]("http://www.linuxtv.org/wiki/index.php/RoxioEasyVHStoDVD").  Practically everything on my xubuntu machine is identical to what described there, but I still  do not understand whether it is supposed to work and/or how should I  get it to work. Yet, the sentence "To make it work, some have to do  modprobe..." seems to suggest that it can be made to work (and seems to be somehow related to the problem in the second post linked above).

In short, I do not know what to do at this point.

Any help greatly appreciated!

Thanks,

p.

---

### Post by Vladlenin5000 on 2014-09-07
13.10 is out of support now so the first thing you should do is upgrade to the current version 14.04.

---

### Post by ienne on 2014-09-07
Vladlenin5000,

thanks. I understand that, but 13.10 is anyway more recent than any of the posts I have read on the subject, thus I doubt that the upgrade would make a difference. Since upgrades have not always worked perfectly smoothly for me, I prefer not to do the upgrade speculatively until there is at least some sort of evidence that the upgrade would make the difference.

Do you know if anything significant has changed between these two adjacent distributions, with respect to the issue at hand?

Best,

p.

---

### Post by Vladlenin5000 on 2014-09-07
Here the thing (actually two things):

1. There's a policy for EoL versions here: [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)   =   NO SUPPORT.
2. Your reasoning is flawed: Newer Ubuntu versions with their newer kernel versions have better chances at supporting any given hardware (granted, there are exceptions and regressions but not for this kind of devices).

Lastly, if you have had problem with upgrades then do a clean install instead backing up whatever you need previously. Whatever your course of action is or will be just make sure you're running a support version, *for your own sake*.

---

### Post by ienne on 2014-09-07
Vladlenin5000,

unfortunately, I did the wrong thing and applied a bunch of updates to xubuntu 13.10 and then upgraded to 14.04 LTS. Unsurprisingly, a bunch of things are now broken:


[LIST]
[*]The minimize/maximize/kill buttons of all windows have disappeared. 
[*]The mouse pointer has disappeared (but reappears after some actions are taken, such as opening menus). 
[*]The desktop is black. 
[*]All the icons of the mounted disks have disappeared from the Desktop (got them back once, but restarting they are going away again). 
[*]Most of the setting windows do not seem to work anymore. 
[*]Audio is no longer working. 
[*]And perhaps others I have not noticed yet.... 
[/LIST]

Most are probably trivialities that I will manage to fix by spending a few hours Googling the forums, looking into menus, etc. But I would have rather spent hours doing something more meaningful. And, of course, the video capture does not work more than it did in 13.10.

Ah, and about the clean install: it was a very clean install, of course, because I refrain from playing with installations (I want my computers to just do the job...) and I have learnt never to do updates. Well, I **though **I had learnt it....  :-(

Will come back to this thread when I will have a working machine again. I am wondering if I will squander less time reinstalling xubuntu 14.04 from scratch or trying to fix the mess--probably the first one is a more deterministic path.

Maybe the EoL policy you refer to is not such a great policy, after all....

Best,

p.

---

### Post by lisati on 2014-09-07
What attracted me to this thread is the mention of video capture. Unfortunately, my experience of Roxio's products is Windows software. I have no experience of their capture devices: I use other means of importing video onto my computer.
> **ienne said:**
> 
Maybe the EoL policy you refer to is not such a great policy, after all....

The EOL policy is there for a reason. Amongst other things, you are unlikely to get updates, and, as a result, you [s]might[/s] will be susceptible to security issues that have since  been fixed in newer releases.

---

### Post by ienne on 2014-09-08
> **lisati said:**
> What attracted me to this thread is the mention of video capture. Unfortunately, my experience of Roxio's products is Windows software. I have no experience of their capture devices: I use other means of importing video onto my computer.

Thanks. Indeed (once my computer will work again), I guess I will look for another USB-connected video capture device clearly supported in Ubuntu. As I understand, most of such devices are in the 50 USD range. I have not checked on the web yet (I was focussed on trying to get mine to work) but if you happen to have at hand a pointer to a list of devices I could buy (input composite video plus stereo audio) and you know by experience that they work well, it would certainly help.

Best,

p.

---

