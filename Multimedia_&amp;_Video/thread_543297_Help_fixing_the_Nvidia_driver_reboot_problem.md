---
title: "Help fixing the Nvidia driver reboot problem"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by H-Radical on 2007-09-04
Hi all, 

I have the standard problem with the Nvidia driver where I have to reinstall the driver after every reboot for it to work properly. (the funny thing with mine is that after one reboot, nvidia loads fine but the restricted modules aren't found so I can't get desktop effects... after the second reboot it just crashes completely and I have to reinstall the driver).

I read in another post that I must delete my nvidia driver, then delete all the "linux images" off my system except the latest one. and then reinstall the driver. But could someone tell me where/what all the "linux images" are and would deleting them do any possible irreparable damage?

Thanks
H-radical

PS. this is the post I'm referring to [http://ubuntuforums.org/showthread.php?t=409032&page=2](http://ubuntuforums.org/showthread.php?t=409032&page=2)

---

### Post by H-Radical on 2007-09-09
bump! Someone please help me... the posts in this forum sink to the bottom so fast. 
I've already tried a few solutions I read about online, but nothing's worked. If this one method has helped someone then it might fix my problem too. Please help.

Thanks

---

### Post by Unit01 on 2007-09-23
Isn't it enough that you remove it with the sudo apt-get remove --purge (driver name) and then reinstall?

Regarding the linux image if you got to synaptic and do a search for linux image you'll find what you seek. Though i don't think you can remove them while you're in the gui of ubuntu.

If you got multiple versions you can edit grub to choose which to boot with.
BTW have you updated everything else in the system?

---

### Post by wheatstraw on 2007-09-30
I found this:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

<from site>
Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed
</from site>

I had to remove the init script and add to the DISABLED_MODULES line and voila.

:guitar:

---

### Post by pieceofpeace on 2008-01-16
Thanks. Worked like a charm on Kubuntu 7.10 .

---

