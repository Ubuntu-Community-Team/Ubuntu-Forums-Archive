---
title: "Nvidia GeForce FX 5200 TV and Monitor editing xorg"
date: 2009-06-18
forum: Multimedia Software
---

### Post by Hendershot on 2009-06-18
Im stuck and need help

I got my new graphics card in the mail today everything works but i need to edit Xorg to get the s video out to work

Im using 9.04 and the tv goes blank before it gets to the login screen.  I've changed the resolution and I've even tried fixing it in recovery mode. All the resourses i've found say i need to edit the x org file, and they provide settings that might work, my main problem here is im a noob and don't know how to get to the file to edit it.

also when i go to use the driver utility i get a message saying 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

How do i go about doing that?

Please help.

---

### Post by Hendershot on 2009-06-18
Development!

I installed envygn and then installed the proper video driver but i keep getting the same error when i go to save my settings

"Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Im so close to getting this to work....
yet so far.

Please help.

---

### Post by xc3RnbFO8P on 2009-06-18
> but i keep getting the same error when i go to save my settings
Did you try **sudo nvidia-settings** in Terminal?

---

### Post by Hendershot on 2009-06-19
> **Ringi said:**
> Did you try **sudo nvidia-settings** in Terminal?

Thank you, that worked, but  how would i set up icon properties to sudo so i can just click the nvidia icon instead of running in terminal?

---

