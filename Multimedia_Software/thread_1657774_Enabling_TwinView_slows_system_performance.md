---
title: "Enabling TwinView slows system performance"
date: 2011-01-01
forum: Multimedia Software
---

### Post by jdholman on 2011-01-01
Hello:

I am running 10.10 64-bit on a Dell M6400 with Nvidia sourced drivers.  The system preforms great when running on my primary laptop display, but when I enable TwinView to add another display, the performance of the system is terrible.  Everything gets slow, and this is especially noticeable when running CPU-intensive applications like VMWare.

I have tried running a separate X display instead of TwinView, but it doesn't seem to matter.  Why would extending my disktop to multiple displays kill my system performance?  The CPU stays at 100%  while it is only 25% or less on the primary display.  What's up with this?  

Jim

---

### Post by BicyclerBoy on 2011-01-01
I'm guessing but..

because this is a laptop ? it could be amount memory allocated to the GPU (graphics).

This is probably configurable in the BIOS/ startup config utility.

Could need a later nvidia driver ?
Could need more system RAM as sometimes the onboard GPU RAM is a ratio of the total.

Separate X screens may work better than twinview.
Turn off compiz/desktop  effects. 

Don't seem to be able to put icons on second screen with separate X screens but apps can be lauched by menus &/or forced to start on it.

VMWare is not a lightweight application, could you use Wine ?

---

### Post by jdholman on 2011-01-02
Thanks for the reply BB:

I implement accounting software here in the US and I need a VM to run SQL Server 2008 and all the Windows stuff related to that.  I agree that VMWare isn't lightweight and I have the absolute latest NVIDIA drivers direct from their website: 260.19.29.  These are a lot better than version 256 was, but still.

My GPU is a Quadro FX 3700M and has 1GB of RAM, but I imagine that all the eye candy is quite a load for the driver.  I have 8GB RAM in the system and I never get close to getting near this limit - it is all CPU utilization.

Since I can run 2 concurrent VMs easily when using only the laptop display, but this kills the system performance when running TwinView OR when running Separate X, I don't know what to do without ripping out all the Compiz/3D stuff.  If I was going to do that, I may as well forgo the NVIDIA drivers altogether and use Nouveau which doesn't have this problem.  I used to have 2 installs of Ubuntu - One with NVIDIA/Compiz for normal use and one with Nouveau for running VMs.  A big pain and I stopped this when I went to 10.10.

If I could easily toggle between Nouveau and NVIDIA without screwing with xorg.conf and Compiz, I would give it a try.  I just can't figure out with the latest native NVIDIA drivers choke so badly with dual displays.

Jim

---

