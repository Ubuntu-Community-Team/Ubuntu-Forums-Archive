---
title: "Nvidia laptop kernel options tuning?"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by KjetilK on 2007-06-12
I was looking through the documentation from Nvidia at [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-i.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-i.html) and found that there are a few parameters that can be set for laptops in particular, namely NVreg_SoftEDID and NVreg_Mobile.

Is anybody using them, and if so, does it have any appreciable effect? 

On an Ubuntu system, where would be the right place to set them?

/etc/modprobe.d/nvidia-kernel-nkc or something?

Would it be:
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=4

My laptop is a Compal HGL30, would the above be the correct for it, or should I rely on the automagic to get it right?

---

