---
title: "problems installing nvidia geforce 9500 driver"
date: 2010-07-02
forum: Multimedia Software
---

### Post by vapblack on 2010-07-02
Okay, so I've been having serious issues with this, it has caused me to just use windows exclusively for a few weeks, untill I remmebered that I hate windows. So I'm back and need to get this driver installed. 

I go to the nvidia website and download the driver. I then stop x and go to run it. I'm given the following error:

> ERROR: Unable to load the kernel module ‘nvidia.ko’.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

I went to this walkthrough and followed it, still getting the error.
[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

so now I'm at a loss. I hate windows, but I need my graphic cards (I have two connected to eachother) to work on my ubuntu. 

what gives :/

---

### Post by Detonate on 2010-07-02
I used the instructions found here.  Worked perfectly for me with my GeForce 9500.

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

Remember that if you install from source and not from the repositories, you will have to redo this every time there is a kernel upgrade.

I only have the one card, and am not using the SLI feature.

---

