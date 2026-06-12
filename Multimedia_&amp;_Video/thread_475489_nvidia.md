---
title: "nvidia"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by Trew on 2007-06-16
i've been trying to install dirvers for my geforce go6150.

but i'm running into a problem.
I've been reading the README file from the Nvidia site but i dont understand the following:

Currently, the NVIDIA driver will attempt to detect edge triggered interrupts and X will purposely fail to start (to avoid stability issues). This behavior can be overridden by setting the "NVreg_RMEdgeIntrCheck" NVIDIA Linux kernel module parameter. This parameter defaults to "1", which enables the edge triggered interrupt detection. Set this parameter to "0" to disable this detection.

now i have to set the paramet to "0"...but i wouldnt know how

this is the link to the readme.

[http://us.download.nvidia.com/XFree8...hapter-08.html](http://us.download.nvidia.com/XFree8...hapter-08.html)

gr
Trew

---

### Post by dabl on 2007-06-16
Have you tried to use the Envy installer?  If it works for your GO 6150, it would be way easier than the path that you are on now!  Here's the site -- read the instructions and download & install the stable version of Envy, and then run it to install your Nvidia driver.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


HTH  :)

---

### Post by Trew on 2007-06-16
thanks for the tip :-)

i've allready tried envy, but what ever i try i get the same error message

(EE) NVIDIA(0): The interrupt for NVIDIA graphics device PCI:0:5:0
(EE) NVIDIA(0):      appears to be edge-triggered. Please see the COMMON
(EE) NVIDIA(0):      PROBLEMS section in the README for additional information.

:-(

gr
trew

---

