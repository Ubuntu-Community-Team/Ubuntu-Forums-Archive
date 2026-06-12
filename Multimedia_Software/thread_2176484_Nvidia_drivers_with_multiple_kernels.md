---
title: "Nvidia drivers with multiple kernels"
date: 2013-09-24
forum: Multimedia Software
---

### Post by mirko.guarniergmail.com on 2013-09-24
I have xubuntu 12.04 with two kernels
[LIST=1]
[*]generic , for normal stuff
[*]lowlatency, for music recording
[/LIST]

I want to install nvidia drivers that are on the repository , on both of them.
The problem is that when I install the drivers on the kernel  1, the installer first removes all the dmks modules (so also from the kernel 2) and it reinstall the modules only on the current kernel. 

This means that the drivers work properly but only in one kernel at the time.

Is there any way to install the module without removing it from the other kernel? 

I would also prefer to not use the manual method (the one with the .run file)

---

### Post by TheFu on 2013-09-24
Sorry, don't have an answer, but I can suggest a workaround.

2 installations.  Each with a 20G / partition, but put your /home on a different partition. They can share swap too.

Workaround, not solution.

---

### Post by mirko.guarniergmail.com on 2014-09-19
Solution here [http://www.linuxquestions.org/questions/slackware-14/nvidia-driver-installation-for-multiple-kernels-910355/](http://www.linuxquestions.org/questions/slackware-14/nvidia-driver-installation-for-multiple-kernels-910355/)

install the NVIDIA official driver and user -k and -K options to load the proper module in both kernels

---

