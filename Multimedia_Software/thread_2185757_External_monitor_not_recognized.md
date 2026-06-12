---
title: "External monitor not recognized"
date: 2013-11-04
forum: Multimedia Software
---

### Post by danone83 on 2013-11-04
Hello,

I am running Ubuntu 12.04 on an ultrabook DELL xps13. I have some problems connecting an external monitor via a VGA cable. The laptop does not have a VGA output, so for the connection I actually use a DELL docking station SuperSpeed USB 3.0. The docking station seems to work fine for all the other features (ethernet connection, USB ports, ...).

Some more info below:

```
daniele@dellino:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
```

The driver:
```
daniele@dellino:~$ sudo lshw -c display | grep driver
[sudo] password for daniele: 
       configuration: driver=i915 latency=0
```

Here is the output of xrand with the external monitor connected:
```
daniele@dellino:~$ xrandr | grep connected
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

It seems nothing happens. Can anybody help?

---

