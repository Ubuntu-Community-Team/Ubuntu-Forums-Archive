---
title: "why make sudo chmod 777 /dev/nvidiactl works permanently ?"
date: 2011-11-22
forum: Multimedia Software
---

### Post by rhoyerboat on 2011-11-22
This thread was old, I hope the guy who was asking got it figured out or will come back, but here:

As far as why, perhaps you are on old nvidia-drivers where this hadn't been applied yet, something was buggy, or something got changed that shouldn't have been changed, it's hard for me to say. 

As to how you solidify the permissions fix:

 make sure you have recent drivers, and check your modprobe configuration (on mine, not actually ubuntu, /etc/modprobe.d files, I'm just not going to go check right now). 

ANYWAY: modprobe is where the nvidia device files get ther permissions set.

 I have an /etc/modprobe.d/nvidia file, which contains the line
<code>
options nvidia NVreg_DeviceFileMode=432 NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=27 NVreg_ModifyDeviceFiles=1
</code>

DeviceFileMode could theoretically be set to 0666 with the same affect, but these device file permissions which I do not know anything about at all are serving my setup quite well. Of course, the rest of these set root to owner in UID and group to video (happens to be 27 on mine) and writeable, of course, I am not sure why that setting is here after the file-mode has already been set.

For further reference:
There is this archlinux thread where people just hack this together without figuring out why the permissions were fudged to begin with, but hey, they are on arch anyway. ([https://bbs.archlinux.org/viewtopic.php?id=11490](https://bbs.archlinux.org/viewtopic.php?id=11490))

Anyway, I saw the recent revisitation of this issue, minutes after finding the explanation of my file, so here it is.

---

