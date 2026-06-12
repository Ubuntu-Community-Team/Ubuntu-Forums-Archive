---
title: "Yet Another Nvidia Driver Problem"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by rem on 2007-05-06
Hello,

I searched the forums for the past 2 days and tried everything and I'm a bit worried I cannot bear it myself, so here I am asking for some help:

I have:

```
Ubuntu Feisty Fawn
nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]
01:00.0 0300: 10de:0181 (rev a2)
```

I installed the nVidia graphic driver with the Restricted Driver Manager, everything worked fine but video playback quality was very poor so I installed every video player out here, besides Totem and noticed no difference. I searched the forums and saw it might be a driver issue so using the Restricted Driver Manager again, I removed the nVidia driver and installed it again using Envy. After that, X crushed and couldn't log back into Gnome anymore. Removed the driver files again, reconfigured X and only then I was able to see GDM again. Re-installed the driver and the required components following the Ubuntu Guide and the How To's but each time I ended up with this error:

```
API mismatch: the NVIDIA kernel module has the version 1.0-7184, 
but this X module has version 1.0-963.  Please make sure that the kernel
module and all NVIDIA driver components have the same version
```

Could somebody here advice how could I sync back nVidia kernel module version with the current X module version and fix my system?

Thank you!

---

### Post by doina100 on 2007-05-06
you might try this

from a terminal

sudo dpkg-reconfigure xserver-xorg

going with the defaults/obvious should get your gui back.

Also I had to go with the nvidia glx "NEW" driver for proper operation.

zack

---

### Post by saracen on 2007-05-06
Did this work?  I'm stuck with this bug too.

---

### Post by rem on 2007-05-07
> you might try this

from a terminal

sudo dpkg-reconfigure xserver-xorg

going with the defaults/obvious should get your gui back.

Also I had to go with the nvidia glx "NEW" driver for proper operation.


Thanks Zack, but if you'll read my post you'll see that I already reconfigured xorg and my video card is nVidia GeForce4  MX 440 which requires nvidia-glx, not the new one ... I don't know what happened or how to fix it ... My computer is mainly for work so I couldn't waist anymore time with this and did a fresh reinstall. Until a proper fix, I will keep it nVidia free ;) Such a pity though ...

---

### Post by Nythain on 2007-05-07
sudo aptitude --purge remove nvidia-glx nvidia-kernel-common nvidia-settings
sudo aptitude install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
if that doesnt work at all, then try downloading the .run package for 9631 from here... [http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9631.html)
then follow these hopefully simple instructions:
```

    add nv to /etc/default/linux-restricted-modules-common
    ctrl + alt + f1
    login
    sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
    sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
    sudo rm /etc/init.d/nvidia-*
    sudo /etc/init.d/gdm stop
    sudo ln -s /bin/bash /bin/sh
    sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
    sudo ln -s /bin/dash /bin/sh

```not sure about the changing dash to bash part for feisty... does it still use dash default like edgy did

---

### Post by rem on 2007-05-07
Thanks for replying,  hopefully that will be useful for somebody with the same problems ... I tried everything and it didn't:

removed, reinstall driver + components several times, reconfigured xorg a hundred times, restored the backups, you name it ... I couldn't have a decent nVidia installation anymore. I managed to bring back GDM though, but it was so messed up, that it acted very weird, with no widgets... so I reinstalled the whole thing ...

---

