---
title: "NVIDIA96 - must re-run NVIDIA driver script every time I reboot"
date: 2013-11-09
forum: Multimedia Software
---

### Post by 3WrKB4C on 2013-11-09
I'm running LUBUNTU 12.10. I have a legacy NVIDIA card working with the 96-series drivers. 
To work around the incompatibility with recent versions of Xorg, I installed the makson96/fglrx version from makson-PPA.
The system was running smoothly for some months. Then a few weeks ago the PC did not reboot to the graphic environment.
I only managed to have everything working after running again the sh script re-installing the NVIDIA driver. 
Now this is the standard procedure I have to follow everytime I restart the PC, to get the graphic environment.
After I sudo service lightdm restart, ubuntu informs me a component crashed and sends a report, with following content:
============
ExecutablePath: /usr/bin/Xorg
Package: xserver-xorg-core 3:1.12.4+git20121105-makson1~ppa2 [modified: usr/lib/xorg/modules/extensions/libglx.so] [origin: LP-PPA-makson96-fglrx]
ProblemType: Crash
ApportVersion: 2.6.1-0ubuntu13
Architecture: i386
Coredump: binary
DistroRelease Ubuntu 12.10
...
MarkForUpload: True
NonfreeKernelModules: nvidia
ProcCmdline: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
...
ProcVersionSignature: Ubuntu 3.5.0-43.66-generic 3.5.7.23
================

I would be glad if anybody could point me in the right direction to stop this annoying problem. Where should I look at?
Thanks
Luca

---

### Post by 3WrKB4C on 2013-11-11
Ok, nevermind: the misbehaviour disappeared on its own, gone as it was come.
I close this case.

---

### Post by 3WrKB4C on 2013-12-04
Yesterday a kernel upgrade was deployed to ubuntu 12.10, and the problem reappeared. I suspect (but I'm a noob on this) that everytime a new kernel is deployed I need to re-build the kernel with the NVidia drivers. Does it make sense what I am saying? Is there a way to automate this process?

---

### Post by Yellow Pasque on 2013-12-05
Where are you getting the nvidia-96 package from (or are you just running the installer from nvidia's site)? Typically, one uses dkms to auto rebuild the kernel modules when there'

---

