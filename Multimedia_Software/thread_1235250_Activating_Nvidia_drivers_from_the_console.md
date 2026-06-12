---
title: "Activating Nvidia drivers from the console?"
date: 2009-08-08
forum: Multimedia Software
---

### Post by apokkalyps on 2009-08-08
I am trying to find if it is possible to activate the restricted Nvidia driver from the console.  I am trying to write a script to set up my computer for me after reformats so I can reformat at a moments whim.  This is the only thing I havent figured out how to do.

I figure it will take two steps, downloading the driver and activating/enabling it.  I'm think the package is nvidia-glx-180.  But I cannot find any way to activate it whatsoever.

From googling I have found there used to be a command > nvidia-glx-config enable that would do it, but now that command doesnt seem to exist on my pc or in the files lists of the nvidia-glx-* packages.

Any suggestions?

---

### Post by 67GTA on 2009-08-08
Should be ```
apt-get -y install nvidia-glx-180
``` The -y argument will assume "yes" to any questions such as "Do you want to also install the dependencies?" Then ```
nvidia-xconfig
``` to set up xorg.conf. You can pass more arguments to nvidia-xconfig such as ```
--composite
``` to enable compositing. Have a look at the "advanced options" in /usr/share/man/man1/nvidia-xconfig.1.gz/nvidia-xconfig.1 for options. I think it would also be a good idea to update your sources before installing anything on a new install. I would probably do ```
apt-get update && apt-get -y install nvidia-glx-180
```

---

### Post by Grishka on 2009-08-08
> **apokkalyps said:**
> I am trying to find if it is possible to activate the restricted Nvidia driver from the console.  I am trying to write a script to set up my computer for me after reformats so I can reformat at a moments whim.  This is the only thing I havent figured out how to do.

I figure it will take two steps, downloading the driver and activating/enabling it.  I'm think the package is nvidia-glx-180.  But I cannot find any way to activate it whatsoever.

From googling I have found there used to be a command  that would do it, but now that command doesnt seem to exist on my pc or in the files lists of the nvidia-glx-* packages.

Any suggestions?

I guess the easiest way to do it would be to install dkms, nvidia-glx-180, and nvidia-180-kernel-source. nvidia kernel source is necessary for compiling nvidia kernel module (the driver won't work without it), while dkms should automatically handle its compilation and installation. it may also be necessary to modify xorg.conf to use the proper driver afterwards.

---

### Post by apokkalyps on 2009-08-11
ohhh ok.  I was overcomplicating it.  I had installed the nvidia-glx-180 package, but I kept looking at the System > Administration > Hardware Drivers menu and expecting it to light up the version 180 driver when it was working, but it stayed dim and left the "activate button" there.  After reading what you wrote I realized it maybe didnt need "activation" when installed as a package rather than through this menu, so I checked it out again and realized the subtitle of text that says "A different version of this driver is in use".  So I checked and low and behold the compiz desktop effects were working.  

Anyway to make a short story long: problem solved!  Thanks

---

