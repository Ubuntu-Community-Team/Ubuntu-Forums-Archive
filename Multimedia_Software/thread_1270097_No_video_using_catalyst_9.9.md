---
title: "No video using catalyst 9.9"
date: 2009-09-19
forum: Multimedia Software
---

### Post by f0nd004u on 2009-09-19
Hey,

I'm new to Ubuntu, but not new to Linux. I'm having an issue using fglrx with my Radeon HD 4850. The default drivers are fine but when I try the proprietary ones, I get no video output at all; analog or digital. I know the system isn't hanging, it's just the video.

Anyone got an idea of what's going on?

Also, does ubuntu use xorg.conf to specify the driver, or am I going to need to reconfigure hal to get the open-source drivers back?

Thanks.

---

### Post by maciejus on 2009-10-16
Hi, 

I have the same issue on my PC (Radeon HD3870, ubuntu amd64)
The screen goes black after installing fglrx deb packages generated from catalyst 9.9.
I have tried on jaunty and karmic as well.

I had to remove the drivers by running the OS in safe mode and uninstalling packages.

---

