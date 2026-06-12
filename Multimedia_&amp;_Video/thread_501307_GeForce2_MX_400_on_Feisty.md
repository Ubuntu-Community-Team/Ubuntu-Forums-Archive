---
title: "GeForce2 MX 400 on Feisty"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by bla2000 on 2007-07-15
My card appears to need the 9631 set of nvidia drivers.  This same card was working correctly on the same monitor when I had Edgy installed and followed the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29").  But I can't get it working in Feisty.

I tried installing by following [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04") but the colours are off and the menu is fainty visible.  It looks like an over-exposed photo or kind of like I have a visualization running on top of my screen to distort things.  Perhaps the restricted driver is installing nvidia-glx-new instead of nvidia-glx.

Next I tried method #1 using the nvidia-glx [http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") but x fails to load.

Next I tried method #2 at [http://doc.gwos.org/index.php/Latest_nvidia_feisty]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") and x fails to load.

Here is some output of /var/log/Xorg.0.log where it fails.

```

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

What else can I try or do you know why it's failing?  Thanks.

---

### Post by T-MAN3000 on 2007-07-15
The solution is, I think, very simple: use the nvidia-glx-legacy drivers. I used this card through many versions of Ubuntu with this driver without problems whatsoever.

---

### Post by bla2000 on 2007-07-15
I'll give that a try using method #1 [http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1]("http://doc.gwos.org/index.php/Latest_nvidia_feisty#METHOD_1")

---

### Post by bla2000 on 2007-07-15
I tried using method #1 with the nvidia-glx-legacy but x-server did not start and the log show the same error as above.  I ran 

```
modprobe nvidia
```

and it returned

```
could not open /lib/modules/2.6.20-16-generic/kernel/drivers/nvidia.ko
```

---

### Post by T-MAN3000 on 2007-07-15
I think you should try to remove and purge all installed nvidia drivers by issuing this command:

```
sudo apt-get remove --purge relevant-package-names
```

relevant packages are eg. nvidia-glx, nvidia-kernel-common etc.

then reinstall the legacy drivers using your preferred method.

---

### Post by bla2000 on 2007-07-15
In method #1 the unstall procedure for nvidia-glx-legacy is

```
sudo apt-get --purge remove nvidia-glx-legacy nvidia-xconfig nvidia-settings
```

I don't see nvidia-kernel-common included so I'll give that a try as well.  Thanks.

---

### Post by bla2000 on 2007-07-15
Removing the nvidia-kernel-common and then using method #1 to install nvidia-glx-legacy worked.  Does the command nvidia-settings work for you?  When mine opens I can only quite and it shows at the command line:

```
ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.9.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.
```

---

### Post by Brendt2 on 2007-07-18
I too cannot access the nvidia-settings and get the same error as posted above.   

Also I cannot get the colors about 8... so it works... but looks funky! 

Does anyone know what I can do?

If i adjust it in dkpg-reconfigure and try and change it to 24 color or even 16 color the server will error out!

What to do... what to do... ?

---

