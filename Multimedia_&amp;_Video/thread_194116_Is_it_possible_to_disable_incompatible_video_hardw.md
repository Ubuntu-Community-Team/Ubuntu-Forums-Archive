---
title: "Is it possible to disable incompatible video hardware?"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by jhaskins on 2006-06-11
Hi,

I'm completely new to GNU/Linux and Ubuntu.  I have a system that still has two 3Dfx Voodoo 2 3D accelerators in an SLI configuration in it.  Ununtu 6.06 will not boot Live off the CD and says there's an X configuration problem.  Installing via the text mode installer works until it tries to start X, then something very similar happens.

If I try to reconfigure X it seems to believe that the first Voodoo 2 card is the primary video adaptor instead of the AGP GeForceFX 5950 I have installed, and I believe this is the cause of my problems.  Removing the Voodoos solves the problem, but I'd prefer not to do this.  As wacky as it may seem, I need the Voodoos for some old school stuff I'd like to have available, and I don't want to be pulling cards in and out when I switch tasks.

Surely there must be a simple way to tell X which bus and device to use, or just disable the problem hardware somehow.  Would recompiling the kernel to remove any Voodoo components be a possibility?

---

### Post by Dr. Nick on 2006-06-11
[quote=jhaskins]Hi,

I'm completely new to GNU/Linux and Ubuntu.  I have a system that still has two 3Dfx Voodoo 2 3D accelerators in an SLI configuration in it.  Ununtu 6.06 will not boot Live off the CD and says there's an X configuration problem.  Installing via the text mode installer works until it tries to start X, then something very similar happens.

If I try to reconfigure X it seems to believe that the first Voodoo 2 card is the primary video adaptor instead of the AGP GeForceFX 5950 I have installed, and I believe this is the cause of my problems.  Removing the Voodoos solves the problem, but I'd prefer not to do this.  As wacky as it may seem, I need the Voodoos for some old school stuff I'd like to have available, and I don't want to be pulling cards in and out when I switch tasks.

Surely there must be a simple way to tell X which bus and device to use, or just disable the problem hardware somehow.  Would recompiling the kernel to remove any Voodoo components be a possibility?[/quote]

you can edit your xorg to tell what bus to use.

Here is my xorg for my agp nvidia card, note the busid.

> Section "Device"
        Identifier      "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
EndSection


not sure what your file looks like so cant say specifically how to set it up for you, but the agp busid will be the same.

You may also look into your bios for "initial display select" and make it agp not pci

---

### Post by jhaskins on 2006-06-11
Thanks for the help.

My BIOS was set to use the AGP card as the primary adaptor, but Ubuntu had other ideas.  Using the info you provided I was able to specify the right bus and device and now it's working perfectly!  Again, thanks!

---

