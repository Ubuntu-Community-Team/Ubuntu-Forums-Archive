---
title: "My video Card is not working at its best"
date: 2012-09-19
forum: Multimedia Software
---

### Post by chitrankdixit on 2012-09-19
I am using Ubuntu on hp pavillion g6 laptop but my video card intel HD graphics family is set always to standard and not performs best. When I minimize any application windows in my Ubuntu 12.04 the outline of the window remains on the screen and even it does not give me option to resize the doc at the left hand side. Please help me out I have installed
mesa-utils 
and updated the system 

Even did the grub settings with nomodeset but do not know the grub settings Intel HD graphics Family (Sandybridge).

---

### Post by BicyclerBoy on 2012-09-20
If you use "nomodeset" you are guaranteed to have bad performance but should always get a desktop running..

The "nomodeset" causes the vesa driver to be used, this is slow & resolution limiting.

Did you have to use "nomodeset" to get any X server running ?

I'm reluctant to suggest the "best solution" (xorg-edgers ppa) because it is very unstable at present YMMV..
There is no other option..

---

### Post by chitrankdixit on 2012-09-20
thanks ByCyclerBoy .
for suggesting me I want to ask you like we use 
with Geforce graphics card : xforcevesa

so is there any means of using something like this with intel HD graphics.

---

### Post by BicyclerBoy on 2012-09-20
AFAIK VESA support is a mandatory requirement for PC graphics cards.
They do not have to achieve any real performance.

I would use the nVidia proprietary driver or open source nouveau driver with Geforce card..
I would never use vesa driver unless there was no other option..
The vesa driver only exists for when there is no choice..

The HD intel graphics in the iCPUs SNA & ivybridge & *view need to have the latest kernel & intel drivers.

These latest packages are likely unstable..

---

