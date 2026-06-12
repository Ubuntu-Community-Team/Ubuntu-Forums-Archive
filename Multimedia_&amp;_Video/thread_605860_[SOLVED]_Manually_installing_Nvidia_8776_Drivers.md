---
title: "[SOLVED] Manually installing Nvidia 8776 Drivers"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by waterloo_sunset on 2007-11-07
I am trying to manually install the Nvidia 8776 driver downloaded from here: [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html) for my onboard GeForce2 Integrated  GPU using the guide found here: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Now when i shutdown X11 and proceed with installing the driver i get a prompt sayin: Couldn't find a matching kernel interface, do you want the installer to download it from the nvidia site?

If i press No, then i get a prompt sayin: This means the installer will have to compile a new kernel interface. Proceed?

Am confused as to which is the correct step as the guide doesn't mention anythin regarding this. Plz guide me with step by step instructions if possible. 

p.s. the nvidia-glx and legacy drivers don't work and result in a blank screen during bootup. I believe this is a common issue with my gpu.

---

### Post by logos34 on 2007-11-07
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/chapter-02-section-03.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8776/README/chapter-02-section-03.html)

try Envy:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
(-->'install the nvidia driver manually')

OR his other guide:

[http://albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_2)

---

### Post by waterloo_sunset on 2007-11-07
Finally got them to work by modifying the xorg.conf a lil.

---

### Post by beczka2005 on 2008-01-23
Would you mind telling us what you did?

I can install the latest drivers from nvidia manually without a problem, but the 8776 driver just will not load. The Xorg.log just tells me it can't find the nvidia module!

---

