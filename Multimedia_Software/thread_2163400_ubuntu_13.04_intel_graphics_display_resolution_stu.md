---
title: "ubuntu 13.04 intel graphics display resolution stuck at 1366x768"
date: 2013-07-18
forum: Multimedia Software
---

### Post by wahabakhtar on 2013-07-18
The resolution of my ubuntu desktop is only maximizing at 1366x768 where as in Windows 7 i used to get 1600x900. Not sure whether its the driver or its the hardware which is not recognized by the operating system. Below are the result from some commands i executed

```

wahab@wahab-latitude:~$ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (rev a1)
wahab@wahab-latitude:~$ 

```

```

wahab@wahab-latitude:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS-2 disconnected (normal left inverted right x axis y axis)
VGA-2 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
wahab@wahab-latitude:~$ 

```

Can anyone guide me in the right direction, that what is wrong with my display?

---

