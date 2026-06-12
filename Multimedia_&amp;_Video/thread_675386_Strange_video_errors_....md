---
title: "Strange video errors ..."
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by arialth on 2008-01-22
i am having a problem with video on Ubuntu 7.04 on an hp dv9420us. The system itself runs smoothly, but when i shut down, i get a black screen, but it is not flat black, because i get some VERY strange anamollies which are like bars of distortion flying down the screen (it is hard to describe.) In addition, when i suspend/hybernate, i get the black screen, too, and i can shut down and logs tell me it was a normal shutdown, but i cannot even switch to tty1.

Also, and i am unsure if this is related or not, but flash does NOT work at all on my system (I have reinstalled recently, and it USED to work.) On top of that, i get horrible DVD playback quality, which i did not have before. I cannot find anything odd from dmesg, besides IRQ#7: nobody cared and the (try booting with irqpoll) thing, but i heard irqpoll causes problems.

---

### Post by mikelito on 2008-01-22
arialth, it is hard to help, as you don't give much information. from what you're saying, and since these problems started popping out after a reinstall, my first suspicion would be that something is going wrong with the video driver, which probably is not the one you used to have before.

start checking (and maybe posting, for additional help ;-)) your X configuration file (/etc/X11/xorg.conf) and log file (/var/log/Xorg.0.log) and maybe the output of lspci.

if you find video-card related errors (EE) or warnings (WW) in your X log, you're probably closer to the cause of your problems.

cheers
m

---

### Post by arialth on 2008-01-22
Alright. I am using the Nvidia-new drivers (with the nvidia new kernel). Actually, it only seems to happen when i update to kernel 2.6.20-16-generic, but it works on 15 just fine, and it only started happening within the last few weeks, because i used to be able to do a full install and install nvidia and everything would work just fine

in Xorg.0.log, the only (EE) entries i have are:
xf86OpenSerial: Cannot open device /dev/input/wacom

I looked this up the other day while i was scanning all my logs to fix this video error (I found nothing related to video or any libraries/modules relating to video) and this is just something i assume is auto-added on ubuntu install for a touchscreen.

Nevertheless, i shall post copies of xorg.conf, xorg.0.log, and lscpi output (actually xorg.0.log is too big but i printed the only (EE)'s out above)


EDIT!!!*******
I looked through the (WW)'s listed in xorg.0.log and found these:
(WW) NVIDIA: No matching device section for instance (BusID PCI:0:10:3) found
(WW) NVIDIA(0): 32-bit ARGB GLX visuals are only supported in depth 24.
(WW) NVIDIA(0): Disabling 32-bit ARGB GLX visuals


Could this be the source?

/EDIT*******

---

### Post by mikelito on 2008-01-22
hmm... tell more about this kernel issue. you mean that if you downgrade to 2.6.20-15-generic, the problem disappears? try it, in case you didn't, you can downgrade the package by selecting it in synaptic, and choosing "force version" from the "package" menu.

in that case, unless you have good reasons to need 20-16, I'd sggest that you stick with 20-15 until a new kernel gets to the repos.

btw, upgrading to gutsy could be a solution as well, even if probably it will spawn a whole new set of problems :-D

michele

---

### Post by arialth on 2008-01-22
Gusty is not really a solution... hehe it flat out refuses to load the xsession with a cryptic GTK error about setuid or something that i could not find help to fix. 

And what i mean is that when i use the 15 kernel, it is fine (that is what installs) but when i update to the 16 kernel i start getting these problems, and it did not used to happen, even with the 16 kernel

---

### Post by mikelito on 2008-01-22
ok. so at worst, 20-15 could be a reasonable workaround for you. 
but I understand you want to understand what's going on. 
I don't own an NVIDIA (i have an ati, and I can assure you I'd be really glad to be able to fix my problems with a kernel downgrade :-)), but looking better at your xorg.conf,  the
Option		"AddARGBGLXVisuals"	"True"
seems to be misplaced, as it shoud go into the "device" section, where you describe the graphic adapter.
BTW, if the warning does not disappear, check if it is there even with 20-15, in which case it is obviously an innocent warning, and the culprit  is elsewhere.

---

### Post by arialth on 2008-01-22
Well, i just went back to look at the 15 kernel ... and it does it, also. I am going to try and replace that line as mikelito said. At this time i am thinking that maybe the errors have been caused by a recent update in the nforce/nvidia drivers. Could this be correct?

***EDIT

And now, for some reason, USB refuses to work... and i cannot open gnome-system-log (due to a segemtation fault) 
WHAT IS GOING ON?!?! 

Also, i get the black screen when i attempt to restart the X server from gnome (using ctrl+alt+backspace)

/EDIT

---

### Post by mikelito on 2008-01-23
wow. the new-video-driver -> video problems sounds reasonable: maybe you can try downgrade the drivers, instead of the kernel.
these brand new problems with usb and segfaults instead sound really weird. I mean, you changed nothing into your system other than playing with xorg.conf and downgrading the kernel?
regarding the segfault (which I imagine you mention as it never happened to you before), check if you are suffering from 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

the USB problem persist even after re-upgrading to 20-16 (no reason to stick with the old kernel, if it doesn't fix your video issues)?

---

### Post by arialth on 2008-01-23
I fixed it by resorting to an old version of the nvidia driver, and now i no longer get video errors!

And i did not downgrade the kernel before, I UPGRADED to 16 from 15 after i installed. 

I do appreciate the help, thank you, i was worried i would never get this solved.

---

