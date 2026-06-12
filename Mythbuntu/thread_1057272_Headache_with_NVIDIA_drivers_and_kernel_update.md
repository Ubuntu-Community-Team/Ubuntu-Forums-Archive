---
title: "Headache with NVIDIA drivers and kernel update"
date: 2009-02-01
forum: Mythbuntu
---

### Post by bmwman on 2009-02-01
I have Mythbuntu 8.04 and just ran the latest updates last night. It came with  new kernel headers. Everything seemed to be working "OK" until I went and tried to open some pictures in MythGallery. I came up with some error "OpenGL not available". I can see the little thumbnails but can't open the photo in full screen. Anyway, i thought I need to get the new NVIDIA drivers to work with the new kernel and I've done it few time before. So I downloaded the newest version 180.22 and installed from "Recovery mode" like last few times that I did it. Well, this time didn't work. My computer doesn't work ever since and I've tried everything i can think off. I even did :
```
sudo apt-get autoremove --purge nvidia-glx-173
sudo apt-get autoremove --purge nvidia-glx-177
sudo apt-get autoremove --purge nvidia-glx-180
sudo apt-get autoremove --purge nvidia*
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
 
```Now when I try to install again, it still telling me there is another version of the driver already installed and I can't uninstall. Then the installation comes to an error ```
unable to create '/lib/modules/2.6.24-21-generic-volatile/nvidia.ko'for copying
```and whole bunch of other ones after that. I even tried the older 177.82 driver and gets the same error.

Please help me fix it

---

