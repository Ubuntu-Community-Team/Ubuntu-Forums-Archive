---
title: "OpenGL not functional, glxgears produces black screen. How to debug?"
date: 2012-08-15
forum: Multimedia Software
---

### Post by kerryhall on 2012-08-15
How do I gather more debugging info to post?

I have two video cards, a Geforce 460 and a Geforce 6600. The Geforce 6600 has worked fine with OpenGL in the past.

If I try and run glxgears in a window displayed by the 6600, I get a black window. Sliding the window over to a display used by the 460, and I can see the gears. This is a pretty interesting bug.

---

### Post by kerryhall on 2012-08-17
Bump

---

### Post by kerryhall on 2012-08-18
I tried uninstalling the nouveau drivers and installing the lastest drivers from the ppa. (304.37)

Same exact problem. 

Black OpenGL window on one screen, but not the other two.

---

### Post by kerryhall on 2012-08-19
Any ideas?

---

### Post by kerryhall on 2012-08-20
$10 via paypal if you can solve this.

---

### Post by kerryhall on 2012-08-22
Any ideas? Thanks!

---

### Post by BicyclerBoy on 2012-08-22
The X server GL engine only runs on one video card unless you can support SLI etc..
AFAIU The 6600 is only used as an output buffer.

There is no point using multiple video GPUs unless:
- sli
- must use an old video connector missing on GTX460
- too many monitors

I assume you are using the new twinview (nView) & not xinerama..

So your problem could be some compatibility bug with latest driver.
Did it ever work (both video cards) ?

I think the performance across both displays would be better if the 6600 is removed.

---

### Post by kerryhall on 2012-08-25
Thank you for the help on this! But I seem to recall having this same setup with a 10.04 install and being able to have OpenGL acceleration across all three displays. Perhaps I was mistaken. So I need to connect the video cards with the sli connector then? Or I should really just get a second GTX460? I think they don't even sell the GTX460 that I have now, so I really need to get two new video cards then? :mad:

Using xinerama with "separate x screen", not using twinview.

My goal is to be able to play openarena across all three monitors, a 6600 should be able to play openarena no problem, considering I was able to play quake 3 on my geforce 2. :D

When loading nvidia-settings, I do get "Xlib:  extension "RANDR" missing on display ":0.0"." dumped to the command line. 

Thanks!

---

### Post by kerryhall on 2012-08-28
Bump?

---

### Post by Dr.Paneas on 2012-08-28
Try my script:  [https://github.com/ubuntuxtreme/Nvidia-installer/tarball/master](https://github.com/ubuntuxtreme/Nvidia-installer/tarball/master)

more info: [http://ubuntuxtreme.com/howto/how-to-install-nvidia-304-43-with-one-click/](http://ubuntuxtreme.com/howto/how-to-install-nvidia-304-43-with-one-click/)

---

### Post by BicyclerBoy on 2012-08-29
Did not say it would not work (using 6600).

But the 6600 was never doing any openGL computation, all the openGL runs in the one card (unless SLI).
SLI requires both cards to be same /very similar so forget the 6600.

Using the 6600 prob just lowers the max frame rates.

AFAIK Xorg xinerama breaks nVidia openGL (version 173 to 295 appox).
Certainly breaks composite extension. 
Xorg xinerama is not same as nVidia xinerama extension.

Comments about dissimilar GPUs:
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/xineramaglx.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/xineramaglx.html)
Check your /var/log/Xorg.0.log

The fermi & kepler cards have >=3 monitor jacks.
Some of the kepler cards can drive 4; prob because the comparative AMD can.

---

### Post by kerryhall on 2012-08-30
I would like to be able to drive 4 monitors at some point, but only worries about the 3 atm. 

I see that SLI is out, but it sounds like that is ok. 

I'm ok with the lower frame rates from using the 6600.

My goal is simply: play Openarena across all three monitors with current hardware setup. If you can get me up and running I will paypal you $20. 

I have the xinerama box ticked in nvidia-settings, not sure if that is xorg xinerama or nvidia xinerama. 

Thank you for the assistance, I will post relevant output from /var/log/Xorg.0.log tonight.

---

### Post by BicyclerBoy on 2012-08-30
AFAIK nVidia has made significant changes to twinview with this driver version..the readme does **not** seem to reflect these changes..
Unfortunately only the driver release "highlights" tab contains the change detail.
There does not seem to be any change summary vs driver version..

As you using latest driver this link is better:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/configtwinview.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/configtwinview.html)

[http://us.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/xineramaglx.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/xineramaglx.html)

And check the log file for error/warnings

Is your GL/GLX installed ?
glxinfo | grep OpenGL
should be noted in the log file as well..

---

### Post by kerryhall on 2012-08-30
I think I found the key line:

"Using identical GPUs is recommended. Some combinations of non-identical, but similar, GPUs are supported. If a GPU is incompatible with the rest of a Xinerama desktop then no OpenGL rendering will appear on the screens driven by that GPU. Rendering will still appear normally on screens connected to other supported GPUs. In this situation the X log file will include a message of the form"

So yeah, I need "similar" GPUs for Xinerama across cards! I will check the logs when I get home tonight, but I think the solution here is either "troll nvidia devs" or "buy new video card(s)" 

Ugh! Thanks for your help though. I'm going to dig a little bit deeper. If I can't get openarena working I will still paypal you $10 for your assistance.

---

### Post by kerryhall on 2012-08-31
[    19.528] (WW) NVIDIA(1): The GPU driving screen 1 is incompatible with the rest of the
[    19.528] (WW) NVIDIA(1):     GPUs composing the desktop.  OpenGL rendering will be
[    19.528] (WW) NVIDIA(1):     disabled on screen 1.

*facepalm*

Ugh.

Looks like I need to just buy two new video cards. What a stupid issue. pm me your email and I'll paypal you $10 for your assistance.

---

### Post by BicyclerBoy on 2012-09-01
I don't require any payment..glad to help.

AFAIK With linux/X server it is easier to get the performance from one card.
Unless you have a known working soln with twin cards, I would buy a GTX660Ti or better.
Note: one output is displayport.

AFAIK Dual cards in SLI requires working mobo soln as well as the driver etc..

---

### Post by kerryhall on 2012-09-05
Thanks again!! 

As an item of note: I was able to play openarena across all three monitors in windows 7 on the same machine, so it's not a hardware issue. Rather, it appears to be a limitation of the Linux driver.

---

