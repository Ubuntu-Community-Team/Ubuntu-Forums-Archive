---
title: "[SOLVED] Cannot Enable Nvidia Drivers"
date: 2008-09-14
forum: Multimedia Software
---

### Post by Mhawkins1 on 2008-09-14
I am a Linux n00b. I have finally gotten my resolution correct, but I cannot enable my Nvidia drivers. I go to System | Administration | Hardware Drivers where it shows NVIDIA accelerated graphics driver (latest cards):  Not in use. I click on the check box to enable it and it tells me a system restart is required. But after the restart the driver is still not enabled. I have done this a few times. I searched Google and couldn't find an answer. Please Help. I'm getting really frustrated.:confused::confused::confused:

---

### Post by cdtech on 2008-09-14
Do you have your Proprietary and Restricted drivers selected in "System > Administrator > Software Sources"?

---

### Post by Mhawkins1 on 2008-09-14
> **cdtech said:**
> Do you have your Proprietary and Restricted drivers selected in "System > Administrator > Software Sources"?

Yes I do. I am still doing some research on my own also. Once I have this fixed I will need to find some help for my PCHDTV PC-5500 tuner card. That is why I'm trying to fix this.

---

### Post by cdtech on 2008-09-14
Did you use "envyng-gtk" to install your drivers?

---

### Post by cyclobs on 2008-09-14
> **Mhawkins1 said:**
> Yes I do. I am still doing some research on my own also. Once I have this fixed I will need to find some help for my PCHDTV PC-5500 tuner card. That is why I'm trying to fix this.

unfortunately i've heard tv tuner cards have very very poor support in linux

---

### Post by Mhawkins1 on 2008-09-14
> **cyclobs said:**
> unfortunately i've heard tv tuner cards have very very poor support in linux
This is the only tuner card i could find that is officially supported under Linux

> **cdtech said:**
> Did you use "envyng-gtk" to install your drivers?
No I did not. I just used the restricted drivers that were available. nvidia-glx-new. They worked before I had to reinstall Ubuntu (I made a mistake and messed things up bad).

---

### Post by Mhawkins1 on 2008-09-14
I installed nvidia-settings from the Synaptic Package Manager and it works. Don't know why I had to do this but It works.

---

