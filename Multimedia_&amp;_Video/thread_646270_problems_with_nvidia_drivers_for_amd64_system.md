---
title: "problems with nvidia drivers for amd64 system"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by arrre on 2007-12-21
Hello,
I've been trying to install nvidias drivers for my 7600 GS card. I'm running kubuntu gusty gibbon on my amd64 system (2.6.22-14-generic is the kernels name). I had some trouble with the installer to actually start, but I solved them by
1. Installing headers (seemed to be installed)
2. Installing libc6-dev
3. Installing g++

The installation finished but then x could not start. Here are the error messages I get when I run startx:
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.
xauth: error in locking autority file /home/*my user name*/-Xauthority

Anyone who knows what to do? 

(I dont know how to get the xorg.conf or it's log file from my computer since ssh don't seem to work... Tell me what you are looking for and I post it.)

---

### Post by chewearn on 2007-12-21
Are you trying to compile the nvidia source code manually?  Is there a particular reason to do so?

The easiest way to install nvidia driver, is go to Restricted Drivers Manager, and enable nvidia.

Another way is to download and run the envy script:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by garydale on 2007-12-21
I had to do a custom kernel to install the Creative labs X-Fi drivers, so the restricted devices application didn't work for me. However, Envy worked perfectly. So google Nvidia Envy and install it. That should end your problems.

---

