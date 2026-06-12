---
title: "Geforce 5200 nividia driver problem"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by lungdart on 2006-07-06
I have a geforce 5200 and am tryin to get the nvidia drivers for it. I have installed nvidia-glx using synaptec and the linux-restricted-modules package for my kernal (2.6.15-25-686) I am using a pentium Celeron, and this kernel has been doing me well. I have followed up by switching the driver from "nv" to "nvidia" in xorg.conf and also doing sudo nvidia-glx-config enable.

Everytime I do this and restart the X server the server crashes. I have to change the drivers back to nv before I can restart X. ](*,)

Anyone understand a potential reason for this? is the 686 kernel not supported by the nvidia drivers?

---

### Post by mriedema on 2006-07-06
I've been fighting this (perhaps same) problem all day today and registered with the forum to post this...

I have a 5200 as well with a fresh install of 6.06.  I installed the nvidia drivers as per instructions here ([http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29") to no avail.  I tried installing legacy drivers as that was pointed out as a possible snag with the same results.

I've followed all the guides and undone the steps each time between but it seems to be a 5200 issue (especially so after I read this post).  Sorry for not offering any feedback, but I will post anything I find out here.  Good luck!

Anyone else? ;)

---

### Post by banin on 2006-07-06
I have the same problem.  I have a Geforce 5200 and I get an error everytime I try to enable the nvidia drivers.  Someone plz help!

---

### Post by lungdart on 2006-07-06
Culprit seems to be the 5200. I figured it was just my card/kernel combo. Is everyone else using the 686 kernel? or the stock 386 (for 32 bit pc)?

Also my 5200 has worked with nvidia drivers on all the previous ubuntus from 5.4 (first one I tried), and also Fedora core 3/4 and SuSE 10.1 with no problems what so ever.

---

### Post by raldz on 2006-07-06
I have the same video card and I'm using a 386 Kernel.. no problem for me.. the driver came from the Automatix download script..

---

### Post by tseliot on 2006-07-07
> **lungdart said:**
> I have a geforce 5200 and am tryin to get the nvidia drivers for it. I have installed nvidia-glx using synaptec and the linux-restricted-modules package for my kernal (2.6.15-25-686) I am using a pentium Celeron, and this kernel has been doing me well. I have followed up by switching the driver from "nv" to "nvidia" in xorg.conf and also doing sudo nvidia-glx-config enable.
Try using this instead of nvidia-glx-config enable (which is broken):
```
sudo nvidia-xconfig

```

---

### Post by raldz on 2006-07-07
Now I guess I have similar problems.. I have 5200 video cards on 2 identical machines.. one is running Ubuntu and the other one running Kubuntu.. the Ubuntu machine runs the nvidia driver well, with 3D accel and with the right resolution.. but the Kubuntu machine gets stucked at 800x640 resolution and I have to change the "nvidia" to "nv" to get the 1024x768 resolution..

---

### Post by tseliot on 2006-07-07
> **raldz said:**
> Now I guess I have similar problems.. I have 5200 video cards on 2 identical machines.. one is running Ubuntu and the other one running Kubuntu.. the Ubuntu machine runs the nvidia driver well, with 3D accel and with the right resolution.. but the Kubuntu machine gets stucked at 800x640 resolution and I have to change the "nvidia" to "nv" to get the 1024x768 resolution..
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by hobieone on 2006-07-07
i think its mainly a nvidia driver issue. nvidia driver doesn't fully support the new xorg in the recent linux releases acoording to it website and are currently working on new drivers according to thier gorums. i also had this issue with my fx 5500 card with kubuntu and never got it working right but some reson it s working alot better with regular ubuntu with the gnome interface but operate slower than it should even with the 3d allerater and direct rendering enabled. so i'm friad we may have to wiat tillnvidia releases it new drivers:-k

---

### Post by raldz on 2006-07-07
> **tseliot said:**
> Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

Yup, I found your link yesterday (now in my signature).. I have found out that the difference between my Ubuntu and Kubuntu machine is that my Ubuntu machine is running the legacy nvidia driver, while the Kubuntu is running the nvidia driver downloaded by Automatix (before the last 2 updates).. Now both are working fine.. and yes, POINT 5 of your howto worked..

---

