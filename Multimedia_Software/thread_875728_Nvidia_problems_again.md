---
title: "Nvidia problems again"
date: 2008-07-31
forum: Multimedia Software
---

### Post by Hunz on 2008-07-31
Hi, 

I got Kubuntu 8.04 and i have been trying various ways to configure my video card with failure.

My card is:

      "NVIDIA Quadro4 980 XGL"

please if any1 can help i would be really thankful

Thanks in advance

---

### Post by PmDematagoda on 2008-07-31
Could you please elaborate? What do you mean by "Problems"? And what are the various ways you've attempted?

---

### Post by Hunz on 2008-07-31
i tried these

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
[http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02/22/installing-nvidia-drivers-in-ubuntu-edgy/)

and by problems i mean enabling the card to be working with max ability, i cant use desktop effects it just crashes cause the video card isnt correctly configured.
probably i need a driver 
i have installed this 1 from nvidia "NVIDIA-Linux-x86-173.14.09-pkg1.run" but apparently i cant run it cause of this error that comes up

"Error: Unable to load kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improprerly configured kernel source, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphic device."

so wat do u guess i should do ??

---

### Post by PmDematagoda on 2008-07-31
What is the Nvidia VGA card you use by the way?

---

### Post by Hunz on 2008-07-31
NVIDIA Quadro4 980 XGL

---

### Post by PmDematagoda on 2008-07-31
Ok, now for a little more clarification(this maybe important), in what order did you actually follow the how-tos?

---

### Post by Israel Katz on 2008-07-31
> **Hunz said:**
> Hi, 

I got Kubuntu 8.04 and i have been trying various ways to configure my video card with failure.

My card is:

      "NVIDIA Quadro4 980 XGL"

please if any1 can help i would be really thankful

Thanks in advance

When You start TvTime it opens an startup window. Please click with the right mouse buttom. On the menu please check what does meet your TV system
like PAL SCCAM

---

### Post by Hunz on 2008-07-31
[http://www.pendrivelinux.com/2007/02...n-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02...n-ubuntu-edgy/)
then 
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
then
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

but after each time the xserver just crashes and i repair it using init 1 and xfix

---

### Post by PmDematagoda on 2008-07-31
> **Hunz said:**
> [http://www.pendrivelinux.com/2007/02...n-ubuntu-edgy/](http://www.pendrivelinux.com/2007/02...n-ubuntu-edgy/)
then 
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
then
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

but after each time the xserver just crashes and i repair it using init 1 and xfix

That is the problem, it is very likely that the nvidia_new driver is conflicting with the nvidia one. But something else, I think the driver installed by both methods maybe wrong since it seems that the Quadro series has different drivers in comparison to the GeForce, etc. series.

First off download the driver from here:-
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run)
and save it in your home directory for easy access.

Then install the driver:-
1) First get rid of the nvidia-glx-new packages with:-
```
sudo apt-get remove --purge nvidia*
```

2) Install the necessary prerequisites for installing the Nvidia driver with:-
```
sudo apt-get install build-essential
```

3) Kill the X-Server with:-
```
sudo /etc/init.d/gdm stop
```
if it gets you to a blank screen, then switch to a different virtual terminal with Ctrl+Alt+F1.

4) Execute the Nvidia installer with:-
```
sudo sh NVIDIA-Linux-x86-96.43.07-pkg1.run
```
allow it to configure the X-Server.

5) After that is done, restart the X-Server with:-
```
sudo /etc/init.d/gdm start
```
and see if that fixes the problems.

---

