---
title: "NVIDIA driver won't work after reboot, works fine if I build it again."
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by TwoWordz on 2007-06-13
Hello,

I've had problems for some time with the nvidia drivers. 

I had the same issues on both ubuntu 7.04 and Debian Etch. 

After installing my system and bringing it up to date, I install the binary nvidia driver using the package on the nvidia site. Restarting X, everything works nicely with 3d acceleration. 

If I upgrade the driver with a new version, I can get start X and everything works again. If I reboot the machine, X would fail to start and nothing shows up in Xorg.0.log. It ends with this line:

(II) Initializing extension GLX

So I thought I would just disable it (modules section, comment GLX) my xorg.conf to see if I can bring up X and it worked. 

Does anyone had this problem? Better, do anyone have a solution? 

I've lost 3 hours yesterday trying to find some answers around the net. Google just brings out too much results. I have around 10 linux workstations to manage, I really need this to work.


Any help would be appreciated, 

TW

---

### Post by dabl on 2007-06-13
Have you tried the packaged driver, nividia-glx-new (or nvidia-glx if you have a "legacy" Nvidia card)?

---

### Post by TwoWordz on 2007-06-13
This is on debian so this package does not exist. 

I post here because the debian forums are not as popular as this one and since I had the problem on both distros I feel it is still relevant to ubuntu. 

There must be a clash somewhere with glx libs but I really don't know how to find out. My linux knowledge is limited on this topic.

TW

---

### Post by reidbold on 2007-06-13
Yeah I have the same problem, I need the newest drivers for my hardware. I'm still looking for an answer myself. 

two threads on this:
[http://ubuntuforums.org/showpost.php?p=2838435&postcount=4](http://ubuntuforums.org/showpost.php?p=2838435&postcount=4)

---

### Post by Citizin on 2007-06-13
I've been having a similar problem, only I can't even get into ubuntu if my nvidia card is used, it wont get me to X or a terminal to fix the problem.

I never heard of this nvidia-glx-new driver, and would a FX5700LE be considered a Legacy Card?

---

