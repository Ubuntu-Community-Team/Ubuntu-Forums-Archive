---
title: "can't Install Nvidia on my AMD 64 Ubuntu 8.04"
date: 2009-02-28
forum: Multimedia Software
---

### Post by Blk_Knight on 2009-02-28
I am trying to install Nvidia drivers for my video card. My gui looks terrible and my nvidia video card is not being used. When I tried using it the bootup changed my xorg file and replaced it with the default xorg cause it was having problems loading. 

I have a DELL pc that runs on AMD 64 Athlon X2. I read somewhere that I had to download the Nvidia drivers so I did so from Nvidia but when I run the drivers (from the prompt)after exiting Xwindows

 [ sh NVIDIA-Linux-x86_64-180.29-pkg2.run] 

I get an error message stating: This .run file is intended for the Linux-x86_64 platform, but you appear to be running on Linux-x86. Aborting installation. 

I don't understand the difference between the two... From the Nvidia site they also don't point out a difference.

Truth be told I just want to find a way to get around this message, have the nvidia drivers installed and bootup with my nvidia video card. Can someone pls help, get me out of this jam? I seam to be grasping at thin air... 

My overall objective was to run 3D, but at this point I don't know how I can achieve that goal when I'm having problems loading the video drivers :(

---

### Post by norwoods on 2009-02-28
i updated from
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)
on 64bit ubuntu intrepid and it works fine.

---

### Post by kelvin spratt on 2009-02-28
If you are running Ubuntu 32bit you need the x86 if you are running Ubuntu 64bt You need x86_64 its your distro not your operating system that is the divisive factor. hope that helps

---

### Post by Blk_Knight on 2009-02-28
Ok I'm try switching to 8.10 amd64 desktop n  see how that goes..

---

### Post by Blk_Knight on 2009-03-01
I'm afraid installing 8.10 64bit did not solve my problem whenever I manually install the nvidia graphics driver from hardware Drivers and did the reboot, it shuts me out from a regular resolution just 800x600. I get a message asking I review my xorg log or edit my xorgconf file. Can anyone help me with installing nvidia graphic card 650 le on my Dell athlon pc

---

