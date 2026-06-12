---
title: "[SOLVED] FATAL: Error running install command for nvidia"
date: 2008-10-17
forum: Multimedia Software
---

### Post by cuiousmind on 2008-10-17
After installing latest nvidia drivers from nvidia over ubuntu supplied nvidia drivers in ubuntu hardy, nvidia x driver doesn't load and "modprobe nvidia" results "FATAL: Error running install command for nvidia" message. 
   There was a solution in a previous closed thread ( [http://ubuntuforums.org/showthread.php?t=721609]("http://ubuntuforums.org/showthread.php?t=721609") i didn't tried it) but after searching i found in a thread ( [http://sudan.ubuntuforums.com/showthread.php?t=901001]("http://sudan.ubuntuforums.com/showthread.php?t=901001") ) that this error was caused by lrm-video and simply solved by commenting out "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS" line in "/etc/modprobe.d/lrm-video". This fixed the problem for me but i didn't find it graceful.
   Again after hacking around a bit i realized that lrm-video is a very useful utility that loads the most suitable nvidia kernel module. Ubuntu restricted nvidia modules is installed in "/lib/modules/[version]/volatile" and there are nvidia_legacy.ko, nvidia_ko and nvidia_new.ko on that location. "lrm-video nvidia" loads the kernel module accordingly, in my case nvidia_new.ko . 
   nvidia installer searches and deletes conflicting driver versions during setup (this includes my nvidia_new.ko) so when i "modprobe nvidia" lrm-video can't find nvidia_new ko (Even if it doesn't delete old kernel drivers they will not work because of version mismatch with newly installed nvidia x driver). This could be simply solved by (without doing previously mentioned commenting) copying "/lib/modules/[version]/kernel/drivers/video/nvidia.ko" (-> nvidia installer installs the module there) to "/lib/modules/[version]/volatile/nvidia_new.ko" .


I know this problem may already be solved but i cant help but share this simpler solution.

Note [version] is your kernel version for example "2.6.24-21-generic".

---

### Post by cuiousmind on 2008-10-18
Update: it seems at every reboot ubuntu restores restricted kernel modules (to nvidia 169) so the best method for working with current 177.80 (installed with nvidia installer) still seems to be commenting out "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS" line in "/etc/modprobe.d/lrm-video".
Sorry if my method didn't worked.

Note: to check if the 177.80 kernel module is loaded type "lsmod | grep nvidia" if nvidia's memory size is 7806272 it is the correct module. Alternatively you can install the kernel module without using modprobe, First press ctrl+alt+F1 to switch to console, login then stop gdm by typing "sudo /etc/init.d/gdm stop" type "sudo insmod /lib/modules/[version]/kernel/drivers/video/nvidia.ko", check if it is the correct one, then restart gdm "sudo /etc/init.d/gdm start". if errors persist check /var/log/Xorg.0.log .

---

### Post by asmund1 on 2009-04-16
Also solves problem when upgrading to Ubuntu Jaunty Jackalope 9.04 and X windows starts in low graphics mode with the message:

(EE)Failed to load module "type1" (module does not exist,0)
(EE)Failed to load module "freetype" (module does not exist,0)
(EE) NVIDIA(0) Failed to load the NVIDIA Kernel Module
(EE) NVIDIA ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Thanks
-Asmund

---

