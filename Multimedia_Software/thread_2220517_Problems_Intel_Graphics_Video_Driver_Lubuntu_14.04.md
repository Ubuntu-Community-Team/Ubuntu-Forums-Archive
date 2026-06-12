---
title: "Problems Intel Graphics Video Driver Lubuntu 14.04"
date: 2014-04-28
forum: Multimedia Software
---

### Post by roland4 on 2014-04-28
Hello,
i have Problems with my Intel Graphics Video Driver on Lubuntu 14.04.

The display size is not correct on my notebook. :-(

Output of lspci -nnk:
```

00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM 
Controller/Host-Hub Interface [8086:2560] (rev 03)
    Subsystem: Uniwill Computer Corp Device [1584:9000]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-
G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
    Subsystem: Uniwill Computer Corp Device [1584:9000]


```

Any help would be appreciated.

Roland

---

### Post by bapoumba on 2014-04-28
I happen to also have an intel graphic card:
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
	Subsystem: Sony Corporation Device [104d:820f]
	Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
	Subsystem: Sony Corporation Device [104d:820f]
	Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
	Subsystem: Sony Corporation Device [104d:820f]

```

What does **xrandr** return ?
Can you get to a config window with **lxrandr** ?

---

### Post by roland4 on 2014-04-28
Hello,

the output von [B]xrandr:
[/B]```
xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 32767 x 32767
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

 
```


[B]lxrandr:
[/B]=> There are no options to select. Only 640x48

---

### Post by roland4 on 2014-04-28
updated

---

### Post by bapoumba on 2014-04-28
Here is mine, what is you vga 1 ?
```
xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 32767 x 32767
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       59.9*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
You can try different resolutions with xrandr and make it permanent by creating a file /home/<your_user>/.config/autostart
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Here is a bug with nvidia (I know this is intel here), but looks like they cannot get the resolution changed via a menu either : [https://bugs.launchpad.net/ubuntu/+bug/1305610](https://bugs.launchpad.net/ubuntu/+bug/1305610)

---

