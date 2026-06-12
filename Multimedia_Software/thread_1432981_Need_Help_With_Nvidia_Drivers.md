---
title: "Need Help With Nvidia Drivers"
date: 2010-03-18
forum: Multimedia Software
---

### Post by L1nuxNewb1e on 2010-03-18
I recently purchased a new Dell Insprion (Windows 7x64, Intel Quad core, 6gb ram, 1TB HD, Nvidia 310). I install Ubuntu 9.04 using Virtualbox and it work fine. I went to Nvidia's website to see if there are any drivers compatible with this video card so I can get Ubuntu working, because Windows 7 sucks, but the only drivers I saw were for the Nvidia 210. I tried the lastest Nvidia drivers from there site (190 and the 195) and when I ran it in sh as root it said ' I do not appear to have an NVIDIA GPU Supported by the 195.30...'

If anyone can help me I would REALLY appreciate it... I HATE Windows!

---

### Post by RedSingularity on 2010-03-18
Install the nvidia drivers through synaptic.  It is much easier.

---

### Post by sprinda on 2010-03-18
i agree apprantly ubuntu can use use those drivers. for me it just a icon apperaed and I just clicked and it did it for me. Well when I was at 8.10 now I am at 9.10.

---

### Post by howefield on 2010-03-18
> **L1nuxNewb1e said:**
> I tried the lastest Nvidia drivers from there site (190 and the 195) and when I ran it in sh as root it said ' I do not appear to have an NVIDIA GPU Supported by the 195.30...'

You are running Ubuntu as a virtual machine using Virtualbox, yes ?

That being the case, Virtualbox will supply the graphics drivers, the drivers from Nvidias website will be of no use to you. If you haven't already installed guest additions, then do so, this will give you amongst other benefits, an improved graphics driver.

---

