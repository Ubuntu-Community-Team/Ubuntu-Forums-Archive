---
title: "Cairo Dock - Transparency Doesn't Work"
date: 2008-10-15
forum: Multimedia Software
---

### Post by Rakanishu on 2008-10-15
Hi.

I have a fresh install of Ubuntu 8.04. And I just installed Cairo Dock.
When I start it up though, I can't get the background of the dock to be transparent, and instead I end up with an ugly black box.

Compiz is installed, and I have a Geforce 9800 GSO GPU.

 [QUOTE=sudo lshw -C display]*-display UNCLAIMED     
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0[/QUOTE]

What do I do?

---

### Post by overdrank on 2008-10-15
> **Rakanishu said:**
> Hi.

I have a fresh install of Ubuntu 8.04. And I just installed Cairo Dock.
When I start it up though, I can't get the background of the dock to be transparent, and instead I end up with an ugly black box.

Compiz is installed, and I have a Geforce 9600 GSO GPU.

 

What do I do?

Hi and you will need compiz to remove the black box around cairo.

---

### Post by Rakanishu on 2008-10-15
But I have compiz installed. It says so in synaptic package manager...

What do I do?

---

### Post by overdrank on 2008-10-15
> **Rakanishu said:**
> But I have compiz installed. It says so in synaptic package manager...

What do I do?

Hi and have you installed the drivers for you nvidia graphics? Have you tried to change the visual effects under system, preference, appearance, then the visual effects tab. You may also look at the FAQ's link in my signature.

---

### Post by Rakanishu on 2008-10-15
It says that enhanced effects couldn't be enabled.
Which is strange, because I remember installing a xorg nvidia driver through synaptic when I first had started the system...

Compiz-Check says that the nv driver is not compatible with Ubuntu. I'll try to install the Nvidia driver separately.

---

### Post by Rakanishu on 2008-10-15
Hmm, I don't understand how to install the NVIDIA driver. I've tried runlevel 1, but then it says that runlevel 1 may cause problems when installing.

And I've tried installing nvidia-glx-new through synaptic, but nothing happens.
And I've checked "hardware drivers", but it says I've got no proprietary drivers...

The Desktop Effects FAQ doesn't provide anything more on this subject, so I'm in the dark here.
It's kind of strange, because I've also googled for how to install the NVIDIA drivers but can't find anything helpful.

---

### Post by Rakanishu on 2008-10-15
Now I installed the NVIDIA drivers by shutting down X and Gnome.
But when I restart, I get the message that the computer is running in low graphics mode because it could not detect the graphics card and drivers. I then chose NVIDIA, but desktop effects still dont work and I cant run higher than 800x600. Also, the NVIDIA installer recompiled my kernel so now it seems my keyboard settings have been reset, probably more too.

Help. Please.

---

### Post by overdrank on 2008-10-15
> **Rakanishu said:**
> Now I installed the NVIDIA drivers by shutting down X and Gnome.
But when I restart, I get the message that the computer is running in low graphics mode because it could not detect the graphics card and drivers. I then chose NVIDIA, but desktop effects still dont work and I cant run higher than 800x600. Also, the NVIDIA installer recompiled my kernel so now it seems my keyboard settings have been reset, probably more too.

Help. Please.

Ok I have not had the privilege of using the Geforce 9600 but from what I have seen on the forums is that you have to install the driver from nvidia as you did.
If you are stuck at the resolution you can try and use the nvidia settings to adjust. ```
gksu nvidia-settings
```
You may also have to use the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` to setup your monitor.

---

### Post by Rakanishu on 2008-10-15
Thanks for your assistance so far.

When I try gksu nvidia-settings, it says that no X driver is installed. I think the kernel recompilation messed up the system.
But let's ignore that, because I'm going to reinstall Ubuntu.
Now, when I have reinstalled it, how do I go about for installing NVIDIA drivers correctly?

By the way, my GPU is 9800 GSO, not 9600.

---

