---
title: "Nvidia 190 restricted driver wants to uninstall mythtv in my 9.10 installation!"
date: 2009-11-12
forum: Mythbuntu
---

### Post by yonkiman on 2009-11-12
So Nvidia finally [released (sort of)]("http://www.nvidia.com/object/linux_display_amd64_190.42.html") the 1.90 driver.  So I followed the instructions [here]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") and very quickly had the repo all set up.

I thought I had it made!

But when I go into Synaptic to update the driver, it tells me that to install nvidia-190-libvdpau, I need to uninstall nvidia-185-libvdpau.  Fair enough.  But the dependencies are such that removing nvidia-185-libvdpau requires removing libmyth-0.22-0, mythtv, mythtv-backend, mythtv-frontend, and a few others.

I tried it anyway.  It removed all the mythtv stuff, and I eventually got 1.90 running.  So then I go to reinstall mythtv, and it tells me it needs nvidia-185-libvdpau, which of course means removing 190.  Which I did.  And I eventually ended up with the same 185 Mythbuntu system I started with a few hours earlier.

So what do I need to do?  I imagine it involves recompiling something, but that's beyond my expertise. 

I was *so close*!

---

### Post by ian dobson on 2009-11-13
Hi,

Maybe wait until ubuntu releases a 190 Nvidia driver package.

Mythtv is marked as needing VDPAU/CUDA so when you deinstall the 185 driver mythtv is deinstalled aswell. As your not using a ubuntu package for your 190 driver the package manager doesn't know anything about it and when you try to install mythtv again it thinks you don't have a VDPAU/CUDA compatible driver installed and installs it for you (185).

So just wait abit or maybe have a look at the JYA repositry, maybe he has a 190 driver package that mythbuntu can use.

Regards
Ian Dobson

---

### Post by byronmyth on 2009-11-13
Any idea when 190 will be implemented?

---

