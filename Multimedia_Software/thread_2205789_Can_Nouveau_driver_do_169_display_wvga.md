---
title: "Can Nouveau driver do 16:9 display w/vga"
date: 2014-02-15
forum: Multimedia Software
---

### Post by jim38 on 2014-02-15
Hello I have:
 Ubuntu 13.10 saucy 
Using a Dell LCD 22 in wide  Flat screen Thats capable of 1920x1080 resolution

Video card
```
:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)
```
Current  display settings [COLOR=#ff0000]             Note:[/COLOR] Looks like I could do 1344x806
```
  jim@jimUbuntu:~$ xvidtune -show
"1024x768"     65.00   1024 1048 1184 1344    768  771  777  806 -hsync -vsync 
```

I had Nvidia non-propreitary driver version 304.  and it could do 1360x768(16:9) display only problem is now my kernal is up to 3.14 and Nvidia is still working on drivers for 3.14.

My question is.. Is it possible to get a[COLOR=#ff0000] higher[/COLOR] resolution from a vga input/output than 1024x768(4:3) using "Nouveau driver"?

Here's a pic of my display settings. They are at there highest resolution, It won't[COLOR=#ff0000] "autodetect"[/COLOR] display?? also last week neither would the 
 Nvidia non-propreitary driver version 304

Thanks for looking
Jim in central USA

---

### Post by jim38 on 2014-02-16
I found a link about the "Unknown display detected" as a newbie to Linux, I was playing around with xrandr
Link->   [http://ubuntuforums.org/showthread.php?t=1769019](http://ubuntuforums.org/showthread.php?t=1769019)

Following the instructions from the link above I can add a custom display, but thats as far as I have got

```
jim@jimUbuntu:/etc/X11$ xrandr --addmode VGA1 "CUSTOM"
xrandr: cannot find output "VGA1"
```

```
jim@jimUbuntu:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
  CUSTOM (0x313)   86.5MHz
        h: width  1328 start 1400 end 1536 total 1744 skew    0 clock   49.6KHz
        v: height  798 start  801 end  811 total  829           clock   59.8Hz
```
Has anyone ever played with xrandr before? 
Any further help appreciated Thanks

---

### Post by jim38 on 2014-02-16
UPDATE! Following the instructions in the "unknown display" link above I had to use VGA-1
```
jim@jimUbuntu:/etc/X11$ xrandr --addmode VGA-1 "CUSTOM"
```

Now I have a custom display 1328x798 (16:9) now w/nouveau driver. It seems maybe a little slower than an Nvidia driver and I'm new at this just playing around.:)
```
  jim@jimUbuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1328 x 798, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1 connected primary 1328x798+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   CUSTOM         59.8* 
jim@jimUbuntu:~$  
```

I have not rebooted yet because I can't find /etc/gdm/Init/Default.  To save these settings as the instructions say
```
   gksu gedit /etc/gdm/Init/Default & 
```

---

### Post by jim38 on 2014-02-16
I have found I'm using lightdm and not gdm so now I need to see how to add this custom  setting to etc/lightdm?? So it will stay on reboot I think?
Does anyone know ? I

---

