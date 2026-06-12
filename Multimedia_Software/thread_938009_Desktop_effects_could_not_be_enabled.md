---
title: "Desktop effects could not be enabled"
date: 2008-10-04
forum: Multimedia Software
---

### Post by fuzzbuzz85 on 2008-10-04
Hi all,

I'm a newbie to all this, but here goes

I tried to upgrade my system effects to 'normal' in System > Appearance >Visuals, and it said 'Desktop effects could not be enabled', and downloaded the driver for my nVidia graphics card (NV5M64). Tried again when this had installed and it didn't work. Searched online and one thread suggested installing XGL, which I did, but has made my graphics worse! Another suggested making alerations to xorg.conf in gedit, but the 'composite' section it mentions in the thread does not appear in my xorg file.

The only other issue which might be relevant is that every time I try and install or update anything in synaptic (or indeed in terminal), I get the following error:

E: gnome-system-monitor: subprocess post-installation script returned error exit status 1

which hasn't resolved itself.. and I've no idea how to do that either!

So, if anyone has any suggestions... I'm a student and really don't fancy buying a new graphics card, and I'd love to get compiz up and running and making my ubuntu look all funky...

Cheers guys!

---

### Post by cariboo on 2008-10-04
Have you tried System-->Administration-->Hardware Drivers, to install the proper drivers for your video card. To fix your broken package problem go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

Jim

---

### Post by GuDoN on 2008-10-04
Had same problem yesterday, fixed it up here:
[http://www.openportal.co.za/index.php?option=com_content&view=article&id=97:ubuntu-804lts-nvidia-driver-failsafe-low-res&catid=39:software]("http://www.openportal.co.za/index.php?option=com_content&view=article&id=97:ubuntu-804lts-nvidia-driver-failsafe-low-res&catid=39:software")

Good luck, and read the entire article!

---

### Post by linux2.6.24-19-generic on 2008-10-04
Did you install the nvidia card after installing the OS?  

I installed an Nvidia card after installing the OS (replaced an ATI card) and it was a disaster.  I wasted many hours trying to get it to work properly and finally just reinstalled the OS, which worked.

---

