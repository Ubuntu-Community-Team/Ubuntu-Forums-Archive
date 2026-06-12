---
title: "NVIDIA 640X480 Hardy"
date: 2008-06-03
forum: Multimedia Software
---

### Post by ilushkin on 2008-06-03
My friends, maybe you could advice me on this issue. I followed these steps successfully, when Hardy came out.

1. Download the 173.08 nvidia beta driver here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) click on archive and find the 173.08 driver.
2. Purge the nvidia restricted package and the nvidia-kernel-package if installed by doing a "dpkg --purge nvidia-glx-new nvidia-kernel-common"
3. Kill the gdm server, "/etc/init.d/gdm stop"
4. Install the driver downloaded in step 1, unless you are brave you need to let the nvidia installer modify the xorg.conf file.
5. start gdm server "/etc/init.d/gdm start"

I was using Ubuntu happily, till this black Friday, when I run the apt-get update. Update ruined my xorg cofig I guess. So I downloaded the latest driver and followed the steps provided by you in Revision 3 again. 

The driver installed successfully, but now my resolution is limited to 640 x 480... . It feels very uncomfy... .

I suspect that the resolution is limited due to the incorrect monitor setting. 

I'm using Nvidia 7600 gt with Samsung SynchMaster 17 inch.

I don't know much about configuration, but can follow the instructions patiently.

Could someone help me to troubleshoot the cause of this inconvenience, please.

Thank you in advance.

---

