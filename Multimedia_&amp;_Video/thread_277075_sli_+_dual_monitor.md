---
title: "sli + dual monitor"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by thexaspect on 2006-10-13
so has anyone out there actually gotten sli to work with dual monitors? I had my two monitors working with twinview, but sli apparently does not support twinview and my computer tells me, and i've been trying everything i can find, but noone has posted a sli specific dual monitor set up howto, so if there's anyone out there that can point me in the right direction, the help would be much appreciated. thank you =)
bryan

---

### Post by sandbagger on 2006-10-28
I am trying to do this at the moment too. Not having much luck. If anyone knows how to do this, please help us out.

---

### Post by Spacesurfer on 2006-10-29
I was just reading the FAQ on the nVidia SLI  [website.]("http://www.slizone.com/page/slizone_faq.html") Here is what it had to say:
> How many monitors are supported when running in SLI mode?
When in multi-GPU mode, SLI currently supports one monitor. When in single-GPU mode, users have the ability to use up to four monitors using NVIDIA® nView® multi-display technology and Windows XP Dualview.

---

### Post by carterhemphill on 2008-04-27
I have (somehow) managed to get 2 monitors to work with an nvidia SLI system.  I have 2 GeForce 6 series cards driving 2x1600x1200 monitors. I'm using Ubuntu 7.10. While I can't remember the precise steps to make everything work, the basics are:

Attach each card to the monitor it will be driving (one card per monitor for SLI multiple monitor system).
use Envy to get Nvidia proprietary drivers.
After the Nvidia driver has installed, use the terminal command: 'sudo nvidia-settings' to start the nvidia GUI.  
The rest is pretty self explanatory; twinview is greyed-out as SLI does not support twinview (I think).

There are some problems with the SLI setup:  
1.) If you are using a VNC like TightVNC to access your desktop remotely, the SLI configuration makes it unusable: the left monitor will display, the right monitor will appear as a dark space and mouse inputs will mis-register onto the right display (attempting to click a target on the left display results in a click to the right display - which you cannot see).  
2.) The "extra visual effects" such as wobbly windows or any custom open GL eye candy you have installed will cease to function.  This has a fix, but results in other issues.

You can use xserver-xorg if you want to have compiz eye candy: you must install xserver-xgl (available through synaptic).  This allows all of the cool screen effects and also will allow a properly functioning VNC.  Howerver the following issues will result:

1.) the system sees the two monitors as one giant screen (3200x1200 in my case).  As such, most programs open half-way between monitors.  

2.) Full-screen functions of programs stretch across both screens.  This has the irritating  result of putting the center of a movie screen at the intersection of the monitors.  I haven't figured out how to fix this yet.

Hope this helps.

---

