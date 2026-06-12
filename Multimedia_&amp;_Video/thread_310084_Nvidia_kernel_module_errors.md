---
title: "Nvidia kernel module errors"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by cshake on 2006-11-30
I updated xorg a little while ago (still on 6.06, xfce4 if that matters at all) and suddenly started getting a version mismatch with xorg and nvidia kernel module. I downloaded the nvidia package from their website and ran the install script and was able to start X fine, but then I restarted the computer and it keeps telling me the kernel module version is even older than what I first got the error with. I tried to run the install again, but now it doesn't work. I can only use nv right now, and would like to go back to nvidia.
I also reinstalled the linux-restricted-modules and nvidia-glx packages, with still no luck.
Does anyone have any idea?

---

### Post by KuriKai on 2006-11-30
I had this problem
I fully uninstalled and removed the nvidia drivers.
then reinstalled them from the repository

---

### Post by tseliot on 2006-11-30
Try envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cshake on 2006-11-30
Thanks! It works fine now.

---

