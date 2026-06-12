---
title: "ATI Driver: Radeon HD 8570A/8570M"
date: 2015-01-17
forum: Multimedia Software
---

### Post by penuel1310 on 2015-01-17
Hi everyone, I need ATI driver for ubuntu. Please help

Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun PRO [Radeon HD 8570A/8570M] (rev ff)

---

### Post by Rob Sayer on 2015-01-17
Try this:

[http://askubuntu.com/questions/465337/ati-graphics-driver-in-ubuntu-14-04](http://askubuntu.com/questions/465337/ati-graphics-driver-in-ubuntu-14-04)

---

### Post by penuel1310 on 2015-01-18
I tried the following:

sudo apt-get install fglrx-updates
sudo apt-get install xserver-xorg-video-radeon

But, I still get "The System is running in low-graphics mode" message.

However, if I disable "switchable graphics" from BIOS, everything works fine.
So is there any way I can actually use Radeon dedicated graphics instead of Intel integrated graphics under Ubuntu?

---

### Post by buzzingrobot on 2015-01-18
Use of onboard Intel video versus Radeon is controlled by the BIOS. If the Intel GPU alone is active at boot, the open source Intel driver will be used by default.  If the Radeon alone is active at boot, the open source Radeon driver will be used by default.

The fglrx driver is the closed-source proprietary driver. 
 
The safest way to install/remove a proprietary driver is via the "Additional Drivers" tool, particularly when it comes to rolling back a previous fglrx install when you want to switch back to the open source driver.

---

### Post by penuel1310 on 2015-01-19
Does this mean I'm using Radeon drivers now? How do I know which graphics card I'm actually using?

---

### Post by buzzingrobot on 2015-01-19
That image shows you are using the open source Radeon driver and the Radeon card. If you wish, you could install the proprietary Radeon drivers from AMD -- fglrx or fglrx-updates --. If the open source driver meets your needs, I'd recommend staying with it for the sake of stability.

---

