---
title: "can't connect my xps ubuntu 12.10 to samsung tv"
date: 2013-01-19
forum: Multimedia Software
---

### Post by antobbo on 2013-01-19
Hi there, I have a dell xps17 and I have recently purchased a hdmi cable. When connected it works ok in windows 7 (I have dual booting) but not in ubuntu, the tv says "No signal". I had a look around on the net, some other people seem to  have the same problem but no good definitive solution seems to be available. SOmebody said it is the nvidia drivers or something like that, can anybody help me please? 
This command ```
lspci | grep -i graphics
```
returns the following
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
antobbo@antobbo-xps17-ubuntu:~$ 


```
xrandr returns this instead:
```

Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 382mm x 214mm
   1600x900       60.3*+
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```
thanks

---

### Post by nonstick on 2013-01-19
I seem to be having the same issue but I have a Compaq cq58 laptop, and I have my laptop hooked to my tv with a vga cord. :(

---

### Post by antobbo on 2013-01-22
Could it be the nvidia graphic card playing up in Ubuntu?

---

### Post by antobbo on 2013-06-05
any idea at all?

---

