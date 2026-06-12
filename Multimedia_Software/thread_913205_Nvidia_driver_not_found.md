---
title: "Nvidia driver not found"
date: 2008-09-07
forum: Multimedia Software
---

### Post by Elderberry on 2008-09-07
I just installed Ubuntu 8.04.01 on a machine with a 8600GTS video card. I went into hardware drivers and the NVIDIA accelerated graphics driver is listed. When I checked enable it tried to download the driver but I got this error:

 W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

I tried plugging in that address in Firefox and sure enough that file was not found. So where is the file and how do I enable the driver?

Mike

---

### Post by pblarry49 on 2008-09-07
> **Elderberry said:**
> I just installed Ubuntu 8.04.01 on a machine with a 8600GTS video card. I went into hardware drivers and the NVIDIA accelerated graphics driver is listed. When I checked enable it tried to download the driver but I got this error:

 W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

I tried plugging in that address in Firefox and sure enough that file was not found. So where is the file and how do I enable the driver?

Mike

Mike- I just did almost the same installation, just a bit older 6 series card. There was no trouble with the nvidia drivers. If you haven't got a lot of time invested in this just try re-installing, or,after the installation, you can go through the hardware drivers under "System" and try from there, or your drivers are still available on the nVidia site. 

you also might try re-installing nvidia-glx-new via synaptic.

---

### Post by pblarry49 on 2008-09-07
I just tried the link myself and indeed it would appear to be a bad URL

---

### Post by sousana on 2008-10-01
> **Elderberry said:**
> I just installed Ubuntu 8.04.01 on a machine with a 8600GTS video card. I went into hardware drivers and the NVIDIA accelerated graphics driver is listed. When I checked enable it tried to download the driver but I got this error:

 W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found

I tried plugging in that address in Firefox and sure enough that file was not found. So where is the file and how do I enable the driver?

Mike

i had this problem too, however when i added both canonical archives to synaptic repositories (settings>repositories>third party software) that seemed to do the trick. not only i got the nvidia driver installed but also found out that there were about a hundred software updates available :) (in the notification bar)

i'm a newbie to linux so i'm not sure whether that was the solution or rather i did something unconsciously that worked :)

i'm sorry for any grammar errors, english is not my first language.
woo hoo first post ! :)

---

