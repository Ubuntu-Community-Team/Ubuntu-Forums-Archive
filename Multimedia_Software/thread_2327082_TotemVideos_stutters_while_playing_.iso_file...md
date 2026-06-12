---
title: "Totem/Videos stutters while playing .iso file.."
date: 2016-06-07
forum: Multimedia Software
---

### Post by Robert_Cline on 2016-06-07
System Information:

Model: Acer Veriton VN282G-UD5253W 
Processor: Intel Atom D525 1.80GHz 
Memory: 4GB DDR3
Hard Drive: 500GB
Graphics: NVIDIA ION GPU - GT218
OS: Ubuntu Desktop 16.04 LTS, 64bit
Browser: Google Chrome-Version 51.0.2704.84, 64bit

(This is my home theater PC, hooked to a 50" HDTV via HDMI @ 720p)

=================================================================

My issue: Totem/Videos stutters while playing video .iso file..

Scenario 1.  I am using the open-source video driver (X.Org X-Server, Nouveau display driver) included with Ubuntu 16.04 LTS install. 
It works great while streaming Netflix, YouTube, etc. but stutters when playing movies from an .iso file in Totem/Videos.

Scenario 2.  I am using the default Nvidia driver (Nvidia binary driver 340.96) in this new Ubuntu install, and it works, fixes the stutter in Totem, but performs poorly with Netflix, specifically. 

Opening Netflix and using HTOP, I view the processor as it gradually ramps up until it begins to redline, and the video begins to freeze and stutter. Takes a few minutes to become unwatchable.

I shut down all plugins in Chrome, including Flash, except for the WildVine decryption, which decodes Netflix stream.

I just switched this box over from LinuxMint 17.3 (using the proprietary Nvidia video drivers), and it played both Netflix and the .iso movie files perfectly with that.

How do I fix this?

I want to use the open-source video drivers, if possible, but mainly I want to be able to watch Netflix & switch to an .iso video file in Totem/Videos,and have it all work.

Thanks,

R.

---

