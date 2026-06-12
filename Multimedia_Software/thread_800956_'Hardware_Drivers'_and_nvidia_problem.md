---
title: "'Hardware Drivers' and nvidia problem"
date: 2008-05-20
forum: Multimedia Software
---

### Post by neuralnet on 2008-05-20
Hi,

I've been having a problem setting up compiz which I've now almost resolved [*LINK*]("http://forum.compiz-fusion.org/showthread.php?t=8414") and I have my spinning desktop back (*Cheer!*) I still have a couple of problems though..

The short version of the original problem being that I could not set up Compiz (despite having it run under feisty and gutsy) because of some references to a long since removed 'Fglrx' driver. A long time ago I had attempted to install and get Compiz running on an Radeon 9600 ATI card, failed miserably and switched to an AGP nVidia GF 7600 GT. Once these references had been removed with AdamK's help, it allowed the NVIDIA driver (nvidia-glx) to work properly and Compiz to function.



The residual problems are that 1) I cannot install nvidia-glx-new (when I do, on rebooting before loading the login window it drops me into the display configuration window and I have to do is select 'vesa' driver in order to continue, as it will not accept 'nvidia') and 2) even when I have 'nvidia-glx' installed when I open the "hardware drivers" applet I am informed that 'no proprietary drivers are in use on this system'.



Any ideas what's causing this? Thanks in advance :)

System: dual core AMD, nVidia GF 7600 GT, 2gb RAM, Abit AV8 mobo, 2x300gb raid 1, ubuntu hardy heron (feisty install, upgraded to gutsy, upgraded to hardy)

---

### Post by man_bash on 2008-05-20
Your card seemingly isn't supported by the nvidia-glx-new package. nvidia-glx package is independently maintained by nvidia, but is restricted to older videocards, while nvidia-glx-new is restricted to the newest ones. My advice - don't fix what's working, and keep using nvidia-glx. If you REALLY want to try, try EnvyNG - it will find dependencies for you, if you need any, but it might (and most likely will) simply reinstall the nvidia-glx package.

---

### Post by Lorathal on 2008-05-20
Ye problably best way is to install envy if it cant configure your graphic to the max then im afraid theres no other way i think.

---

### Post by neuralnet on 2008-05-20
Thanks for the reply. Hmmm, well I would have thought that a 7600GT *is* normally supported under nvidia-glx-new, it's hardly a legacy video card !

Appreciate what your saying along the lines of 'if it ain't broke don't fix it',  but the fact that the 'hardware drivers' applet can't see any proprietary drivers despite NVIDIA drivers being active leads me to suspect something else is broken too.

I'll give envy a go. Thanks.

---

### Post by neuralnet on 2008-05-20
Curious. EnvyNG starts, I click 'Install nVidia Driver', a black command window appears and instantly minimises & vanishes. 30 secs of CPU processing and this gets thrown up;

```
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
```

Envy did not solve the problem ;)

---

### Post by neuralnet on 2008-05-20
well I installed the NVIDIA driver from the NVIDIA website, not the one from synaptic, but as per this post [*LINK*]("http://ubuntuforums.org/showthread.php?t=800925").

I have the NVIDIA driver installed, Compiz works and the NVIDIA driver is now showing in the 'hardware drivers' applet. Result!

---

