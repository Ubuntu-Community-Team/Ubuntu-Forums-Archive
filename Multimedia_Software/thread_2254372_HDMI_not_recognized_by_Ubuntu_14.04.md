---
title: "HDMI not recognized by Ubuntu 14.04"
date: 2014-11-26
forum: Multimedia Software
---

### Post by zozonmr on 2014-11-26
Hi,

I know there are tons of threads about this but none of those helped me. I went through 3 types of Nvidia installation but my HDMI port is still not being recognized by Ubuntu 14.04 (32 - bit) and I cant use to connect to a TV. 
I am using an Asus laptop (P31S) with this VGA (lspci | grep VGA):

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev ff)

my xrandr looks like this:

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 293mm x 164mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
 ubuntu driver services:
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
model    : GF119M [GeForce 610M]
modalias : pci:v000010DEd0000105Asv00001043sd00002129bc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-331-updates - distro non-free
driver   : nvidia-331 - distro non-free recommended
driver   : nvidia-304-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304 - distro non-free

So I installed the Nvidia-331 and bumblebee but still no success. Installing binary driver from Nvidia failed with the message pr-installtion script failed. 
Does anybody know whether HDMI works under ubuntu14.04? If yes how to get it working?

Thanks

---

