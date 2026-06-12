---
title: "ATI Big Desktop - TV is primary :("
date: 2008-07-29
forum: Multimedia Software
---

### Post by bartoon on 2008-07-29
Hi,

I got an ATI X1650 Pro AGP / Unbuntu 8.04 Hardy Heron and I'm trying to set the big desktop.. :???:

I've followed the tutorial made by Ziox (thx btw for that thread)... but I can't solve my problem : I got the big desktop but not the way I want it.. the extended desktop is on my LCD and the 'primary' desktop is on the TV... and just want the reverse.. I want the extended desktop on the TV not on the LCD..

I tried the 'horizontal,reverse' but there is no change.. 

(Both LCD and TV are in 1024x768 right now.. I'll try to change this when the big-desktop will work properly)

Thank you in advance.
bartoon


fglrxinfo :
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)


```

xrandr:
```

Screen 0: minimum 320 x 200, current 2048 x 768, maximum 2048 x 768
default connected 2048x768+0+0 0mm x 0mm
   2048x768       60.0* 
   1024x768       60.0     43.0  
   800x600        60.0     56.0     47.0  
   720x576        50.0  
   720x480        60.0  
   640x480        60.0  
   640x432        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  

```

lpsci:
```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)

```:sad::(

---

### Post by Stolea on 2008-07-29
I am not sure, but I think you can determine the primary display in the ATI Catalyst Control Center.
If you haven't got it installed, go to Applications>Add/Remove>Other and tick the ATI Catalyst Control Center object.
By rights you should be able to do pretty much the same thing that you can in Windoze and select which the primary display is.

---

### Post by bartoon on 2008-07-29
right Stolea, you can identify displays under the control center..

I tried this too.. under the ATI Catalyst Control Center (amdccle) when I click on the 'Identify Displays' button my TV is always detected as '1' and my LCD as '2' it's weird :???:.. especially that the first time i've lunched amdccle the detection was correct (LCD n°1 & TV n°2). I've also tried to drag/drop/switch the tv/lcd order in the display manager of the ati control center.. no change

---

### Post by markbuntu on 2008-07-29
Since fglrx says you are using mesa, the ati driver is not properly installed and so the Catalyst Control Center will not work properly. Follow these directions to install the driver properly, use method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by Stolea on 2008-07-29
Come to think of it, I had a very similar problem with the ATI driver when I ran the 64 bit version on my AMD64 machine. I could not get the driver to install properly, no matter what I tried. There were some other frustrating problems but the problem was resolved when I installed the 32-bit version. I don't even try to understand the finer reasons why. I am just happy that it works nowhttp://ubuntuforums.org/images/smilies/icon_smile.gif

---

