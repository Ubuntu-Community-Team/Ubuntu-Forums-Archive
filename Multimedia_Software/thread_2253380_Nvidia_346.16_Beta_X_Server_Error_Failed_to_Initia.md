---
title: "Nvidia 346.16 Beta X Server Error: Failed to Initialize GLX Extension"
date: 2014-11-19
forum: Multimedia Software
---

### Post by actionmystique on 2014-11-19
_**Environment**_: **MSI GE60 - GeForce GTX 765 M - Ubuntu 14.10 - Linux 3.16.0-24**
**X Server Error after installing Nvidia 346.16 driver: Failed to Initialize GLX Extension (Compatible Nvidia X Driver Not Found)**

I installed last Nvidia driver after having 
- purged xserver-xorg-video-nouveau and its dependency
- blacklisted Nouveau driver by inserting /etc/modprobe.d/blacklist-nouveau.conf:
    blacklist nouveau
    blacklist lbm-nouveau
    options nouveau modeset=0
    alias nouveau off
    alias lbm-nouveau off
- updated 'initramfs": update-initramfs -u
- rebooted
- entered a non graphical environment at login with ctrl-alt-F1
- stopped lightdm (display manager) with /etc/init.d/lightdm stop
- launched sh ./NVIDIA-Linux-x86_64-346.16.run
- verified that the Nvidia driver was loaded with **lspci**:

root@MSI-GE60-Ubuntu-14:-# lspci -vnn | grep NVidia -A 17 
.01:00.0 3D, controller [0302]: NVIDIA Corporation GK106M [GeForce GTX 765M] [10de:11e2] (rev a1) 
Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:1001 ]
Flags: bus master, fast devsel, latency 0, IRQ 16 
Memory at f6000000 (32-bit , non-prefetchable) [size:16M] 
Memory at c0000000 (64-bit , prefetchable) [size=256M] 
Memory at d0000000 (64-bit, prefetchable) [size=32M] 
I/0 ports at e000 [size=128]
Expansion ROM at f7000000 [disabled] [size=512K] 
Capabilities: [60] Powe Management version,3 
Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+ 
Capabilities: [78] Express Endpoint, MSI 00 
Capabilities: [b4] Vendor Specific Information: Len=14 <?>
Capabilities: [100] Virtual Channel 
Capabilities: [128] Power Budgeting <?> 
Capabilities: [600] Vendor Specific Information: ID=1 REv=1 Len=24 <?>
Capabilities: [900] #19 
Kernel driver in use: **nvidia** 

- and with **lsmod**:
root@MSI-GE60-Ubuntu-14:-# lsmod | grep nvidia 
nvidia 8422497 0 
drm  310919 5 i915,drm_kms_helper,nvidia 

The error described in this thread title happens before I launch **nvidia-xconfig** or after.
I have provided additional traces here:
- [modinfo nvidia]("https://drive.google.com/file/d/0B5fXyIn0-GDFQ2Y3T1BJNm9FZlk/view?usp=sharing")
- [cat /var/log/nvidia-installer.log]("https://drive.google.com/file/d/0B5fXyIn0-GDFVUJuTDlYT0lqTnM/view?usp=sharing")
- [cat /var/log/Xorg.0.log | grep -i nvidia]("https://drive.google.com/file/d/0B5fXyIn0-GDFOFRPR1J3MjBfLWM/view?usp=sharing")
- [cat /var/log/Xorg.0.log | grep -i nvidia -C 1]("https://drive.google.com/file/d/0B5fXyIn0-GDFaUQ3S05tVlc5MHM/view?usp=sharing")

**What could be done to solve or work around this issue**?

---

