---
title: "nvidia problem- can't get splash screen on fresh drapper install"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by av05 on 2006-08-13
Hi all,

after installing fresh ubuntu, and upgrading to latest, i'm trying to install the nvidia fx 5500.
i followed the guidelines at [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) -
- installed nvidia-glx
- installed all relevant linux-restricted-modules
- ran nvidia-glx-config enable
- restarted X
and dont get the expecetd nvidia splash screen.
i followed all the troubleshooting items, and ran "dpkg-reconfigure xserver-xorg" - set to "driver" to nvidia (not nv) and "Activate kernel framebuffer device interface" to yes, 
but then when I restarted X I got:
```
Module NVIDIA not found
NVIDIA(0): Failed to load the NVIDIA kernel module
NVIDIA(0): Aborting
```

and X didn't load, until I reverted back to the old xorg file.
Does anyone have any idea to share ?

](*,)

---

### Post by tseliot on 2006-08-13
Follow Method 1 of this guide:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

---

### Post by Crooksey on 2006-08-13
```


$ sudo apt-get insatll nvidia-glx

$ sudo gedit /etc/X11/xorg.cong


```

Now look in your xorg.conf for the word "drivers" next to it at the moment it should say "nv" change that to "nvidia". All done :)

---

### Post by av05 on 2006-08-18
Ok. Tseliot, I followed method 1- which is really simliar to the first wiki I saw. Nothing- it's still doesn't work.
When I followed Crooksey's advice and set Driver to "nvidia" at the xorg.conf, I got the same" NVIDIA(0): Failed to load the NVIDIA kernel module" when starting X.

I'm running kernel 2.6.15-26-386 - which is what I got with Ubuntu 6.0.6 after the update, yet on the package manager I notice that most of the packages are of 2.6.15-23 and 2.6.15-25. I have the following installed:
linux-image-2.6.15-23-386
linux-image-2.6.15-23-686
linux-image-2.6.15-26-386
linux-restricted-modules-2.6.15-23-386
linux-restricted-modules-2.6.15-23-686
linux-restricted-modules-common

Could the error I'm getting be related to the fact that the restricted modules installes is of 2.6.15-23 and that uname -r gives "2.6.15-26-386" ??

any help would be appreciated!

PS- to add a bit more of info, on the device manager I can see the video card, appears as VT8237 PCI Bridge->NV34 [GeForce FX 5500]
I hope this helps... ](*,)

---

### Post by tseliot on 2006-08-18
> **av05 said:**
> Ok. Tseliot, I followed method 1- which is really simliar to the first wiki I saw. Nothing- it's still doesn't work.
When I followed Crooksey's advice and set Driver to "nvidia" at the xorg.conf, I got the same" NVIDIA(0): Failed to load the NVIDIA kernel module" when starting X.

I'm running kernel 2.6.15-26-386 - which is what I got with Ubuntu 6.0.6 after the update, yet on the package manager I notice that most of the packages are of 2.6.15-23 and 2.6.15-25. I have the following installed:
linux-image-2.6.15-23-386
linux-image-2.6.15-23-686
linux-image-2.6.15-26-386
linux-restricted-modules-2.6.15-23-386
linux-restricted-modules-2.6.15-23-686
linux-restricted-modules-common

Could the error I'm getting be related to the fact that the restricted modules installes is of 2.6.15-23 and that uname -r gives "2.6.15-26-386" ??

any help would be appreciated!

PS- to add a bit more of info, on the device manager I can see the video card, appears as VT8237 PCI Bridge->NV34 [GeForce FX 5500]
I hope this helps... ](*,)
1) Try with:
```
sudo apt-get install linux-686
```

2) Set the driver to "nvidia"

3) Reboot

---

