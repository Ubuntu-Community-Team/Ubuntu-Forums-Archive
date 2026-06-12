---
title: "no sound in gOS - aka need help with alsa"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by go_dragons on 2007-11-06
For those of you who live under a rock or like to hide in holes, walmart has recently released a cheap computer with a linux operating system by the name of gOS. The operating system is basically n ubuntu 7.10 backend with e17 DE on top of it. I have been an ubuntu user for a couple of years and everyting has always worked great on my computer, and I thought it would be interesting to use an e17 DE so I decided to try this out.

At first glance, everything looks great. It is fast and responsive and lightweight but it still has some asthetically pleasing features. I can tell there are a few minor differances from ubuntu backend, such as the addition of xdebconfigurator that doesnt want me to change my x.conf file to install nvidia drivers. I do enjoy a good problem however and I had a good time fixing a few of the bugs that I saw. But I digress....

My overall impression of this wal-mart OS fairly positive with the exception of sound problem that I have been so far unable to solve.

 **here are my symptoms:**

invoking alsamixer from the xterm returns this error: " alsamixer: function snd_ctl_open failed for default: No such device"

I have tried dpkg-reconfigure alsa-base but I still get the same error. 


When I try to play a movie with totem I get this error message: "Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies." 
I do not know if that problem is related or a completely separate issue.

**other information about my system**: 

I have an HP pavillion a1483w
I am using the onboard Realtek sound card (which worked great in the regular ubuntu distro)
I am currently on the linux-image-2.6.22-14.46-generic kernel image. This system came stock witht the 386 image but the generic image is faster on my computer. 


Thanks for your help everyone! I will continue to troubleshoot and hopefully will get things worked out!:)

---

### Post by go_dragons on 2007-11-09
After doing a bit of research I found that alsa has modules that need to be added to the kernel in order to work. Although I did not test this beforehand, my guess is that alsa worked for me before I changed kernels. This problem was the result of my misunderstanding of the way the kernel apt packages worked. While I did install the kernel I needed to install the linux-generic metapackage instead to install the needed modules with the kernel. Problem solved.

---

