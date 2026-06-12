---
title: "Cedar View drivers aren't working"
date: 2012-07-27
forum: Multimedia Software
---

### Post by AZorin on 2012-07-27
Hello everyone,
There has been a lot of commotion about Intel's Cedar View graphics (In the Intel Atom Cedar Trail CPUs including the N2800 and N2600) not working in Ubuntu because the GPU architecture was actually licensed to Intel by Imagination Technologies (a PowerVR GPU). Supposedly, the GPU isn't supported in Linux by Imagination Technologies (who own the Intellectual Property of the GPU's design) but Intel have created some closed source drivers for this GPU in MeeGo 1.2. 

I have personally tried out Ubuntu 12.04 and MeeGo 1.2 update 6 on my Intel Atom N2800 notebook. 
MeeGo seemed to work very well with the notebook's full screen resolution (1366 X 768) enabled automatically and the 3D graphics working flawlessly in the pre-installed Neverball game without skipping a beat. Suspend/Sleep mode worked perfectly in MeeGo as well. All of this was thanks to Intel's closed-source drivers. MeeGo 1.2 update 6 apparently has Linux Kernel version 2.6.37 according to this page: [http://goo.gl/315l0](http://goo.gl/315l0)
Ubuntu 12.04 didn't work as well out-of-the-box. The screen resolution was set to 800 X 600 and it could not be increased, Neverball worked horribly with a lot of skipped frames and a flickering black window and for some reason the mouse cursor randomly flickered. Suspend mode worked well and the system was fully usable after using Suspend. To try to get some more graphics support, I upgraded to the newest stable Linux Kernel version (3.4.6) using this guide: [http://goo.gl/pim3W](http://goo.gl/pim3W) Thankfully things got better and my screen resolution was back to the full 1366 X 768. Unfortunately the 3D graphics support still lacked and Neverball was still laggy and flickery, the cursor still flickered and Suspend mode now failed to work. After I put the computer to Suspend and woke it back up the screen's resolution went very low, many weird horizontal lines appeared and the screen looked cropped, yet the system could be used. The suspend glitch is shown in this image: [http://goo.gl/RZV35](http://goo.gl/RZV35)

I have found a project ([https://launchpad.net/~sarvatt/+archive/cedarview/](https://launchpad.net/~sarvatt/+archive/cedarview/)) which aims to bring Cedar View graphics support to Ubuntu and it has worked for some but not for others, including me. After I installed the drivers from the PPA and rebooted the system could only work in a console mode and the 'startx' failed. This has been the same with both Kernel versions 3.2.0-27 from the official Ubuntu 12.04 updates and with version 3.4.6.

Could anyone please help me get the Cedar View graphics working on my Intel Atom N2800 laptop by possibly fixing the cedarview packages from Launchpad or installing the closed-source drivers by Intel from MeeGo 1.2? I have made links to the outputs of the following commands from my notebook to help any problem solvers with this task:
dmesg: [http://goo.gl/1IVbW](http://goo.gl/1IVbW)
dmidecode: [http://goo.gl/EJXsW](http://goo.gl/EJXsW)
lshw: [http://goo.gl/RRqcW](http://goo.gl/RRqcW)
lspci: [http://goo.gl/k7wsz](http://goo.gl/k7wsz)

Thank you very much for your time!

---

### Post by apasnuy on 2012-08-15
Try to read:
[http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/](http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/)

And folow developing of this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944929](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944929)

---

