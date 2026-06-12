---
title: "Module options for nvidia driver getting ignored on boot"
date: 2012-11-05
forum: Multimedia Software
---

### Post by a-user on 2012-11-05
ubuntu 12.10.

Well, i tried to enable msi for my nvidia card using the nvidia proprietary drivers from the x-edgers ppa.

for this to work i added options.conf to /erc/modprobe.d
and added this line (obviously this alo enable page attributed tables):
options nvidia NVreg_EnableMSI=1 NVreg_UsePageAttributeTable=1

beside of this i also added this:
options snd_hda_intel enable_msi=1
to enable msi also for my audio device.

after a reboot this only worked for my audio device. both options for the nvidia driver got ignored.

so i shut down gdm service, removed the module nvidia and then loaded the module again via:
modprobe nvidia

interesting, it loaded the module with the specified option, so MSI worked.

now i thought that maybe due to some preloading during boot i have to  use a special config file within modeprobe.d and maybe also need to  rebuild the initramfs.
i tried putting the options line within
modprobe.d/nvidia
modprobe.d/dkms.conf
and within the existing modprobe.d/nvidia* files
also tried rebuilding the initramfs and updating grub2. nothing worked. on boot it seems that no options are read.

anybody an idea?

---

### Post by a-user on 2012-11-05
Solved it myself:

actually, the modul loaded during boot is called "nvidia_current". i do not know why it is also possible to load it via "modprobe nvidia" instead of "modprobe nvidia_current". That's why i though the name actually is always nvidia.

anyway, changing my options line to
options nvidia_current NVreg_EnableMSI=1 NVreg_UsePageAttributeTable=1
actually fixes this problem.

---

