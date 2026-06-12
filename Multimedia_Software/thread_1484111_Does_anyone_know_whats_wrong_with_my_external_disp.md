---
title: "Does anyone know whats wrong with my external display?"
date: 2010-05-15
forum: Multimedia Software
---

### Post by raggiskula on 2010-05-15
A bit of background:
It's broken in 10.04 but it works in earlier versions.
I'm running T60 Lenovo laptop. I'ts only the external display thats messed up, but the laptops display is fine. 
I'm using ATI Radeon x1400 display card with the default drivers, not fglrx.

Here's a 14 sec video of the display
[http://www.youtube.com/watch?v=HdMbMtbsv8s](http://www.youtube.com/watch?v=HdMbMtbsv8s)
and a photo
[IMG]http://i.imgur.com/KFnnpl.jpg[/IMG]
orginal res: [http://imgur.com/KFnnp.jpg](http://imgur.com/KFnnp.jpg)

Thanks for any info.

---

### Post by nierogama on 2010-05-16
I have the same issue (Ubuntu 10.04 x86 with the latest updates).

Laptop is Toshiba Sattelite M100-222, graphics is ATI Mobility Radeon X1400. External monitor is NEC MultiSync LCD 1770NX.

The configuration dialog (System -> Preferences -> Monitors) for external monitor has the following set of resolutions:
[LIST]
[*]1360x768 (16:9)
[*]1024x768 (4:3)
[*]800x600 (4:3)
[*]848x480 (16:9)
[*]640x480 (4:3)
[/LIST]

Only 1360x768 option works the same as in the previous post's screenshot/video. If I set other resolutions, monitor shows "Out of range" error message. 

The recomended NEC resolution is 1280x1024.

The laptop display works fine: right resolution, compiz effects, etc.

ATI website doesn't contain proprietary drivers for X1400 for Linux, it just refers to manufacturer website. But Toshiba driver page for my laptop contains only Windows drivers.

Any ideas how to fix this?

---

### Post by xc3RnbFO8P on 2010-05-16
Did you try to turn of Compiz?

---

### Post by nierogama on 2010-05-16
I've found this thread: [[SOLVED] Bad video output on secondary screen]("http://ubuntuforums.org/showthread.php?t=1466072")

And the information from errorson's post help to fix half a problem:
> **errorsson said:**
> The relevant bug might be [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/541501](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/541501)
and for me it worked to create file /etc/modprobe.d/radeon.conf with contents "options radeon new_pll=0 modeset=0" and reboot.

Apparently also fixed upstream: [http://bugs.freedesktop.org/show_bug.cgi?id=27278](http://bugs.freedesktop.org/show_bug.cgi?id=27278)

There is no more flickering on my external display at 1024x768 (4:3).

The other part of the problem is wrong resolution.

xrandr outputs
```

Screen 0: minimum 320 x 200, current 2304 x 800, maximum 2640 x 800
VGA-0 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)

```

cat /etc/X11/xorg.conf
```


Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2640 800
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


```

The question is how can I set recommended resolution 1280x1024 (instead of 1024x768) on my external monitor?

---

### Post by nierogama on 2010-05-16
I have fixed the problem.

**1. Fix flickering problem.**

Start terminal (Applications -> Accessories -> Terminal and create file /etc/modprobe.d/radeon.conf
```

$ sudo gedit /etc/modprobe.d/radeon.conf

```

with content
```

options radeon new_pll=0 modeset=0

```

Restart.

**2. Add monitor recomended mode (if it is absent).**

From Terminal
```

$ xrandr

Screen 0: minimum 320 x 200, current 2304 x 800, maximum 2640 x 800
VGA-0 connected 1024x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)

$ cvt 1280 1024

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
$ xrandr --addmode VGA-0 1280x1024_60.00
$ xrandr --output VGA-0 --mode 1280x1024_60.00

```

Running these would change your resolution but this is temporary.

Create file ~/.xprofile and fill it with previous commands to execute it every startup:
```

# Set up right resolution for external display (NEC MultiSync LCD 1770NX)
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00
xrandr --output VGA-0 --mode 1280x1024_60.00

```

**3. Correct virtual resolution**

Go to System -> Preferences -> Monitors, set relative screen positions and Apply changes (check that all screen resolutions are set right).

**4. Restart Ubuntu.**

All is fine, but a new problem appears, with gnome panel: there is a bug in rendering indicators. Some of them overlay each other, some don't appear at all (black square in its place).

The following command helps me:
```

killall gnome-panel

```

I found this information in the following posts (thanks to all):
[LIST]
[*][Bad video output on secondary screen]("http://ubuntuforums.org/showthread.php?t=1466072")
[*]["Unknown Monitor" and cant increase resolution beyoud 800x600]("http://ubuntuforums.org/showthread.php?t=1364460")
[*][X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")
[*][Refresh Gnome panel?]("http://ubuntuforums.org/showthread.php?t=365733")
[/LIST]

---

### Post by raggiskula on 2010-05-27
This worked for me, thanks a lot nierogama! :biggrin:

> **nierogama said:**
> 
**1. Fix flickering problem.**

Start terminal (Applications -> Accessories -> Terminal and create file /etc/modprobe.d/radeon.conf
```

$ sudo gedit /etc/modprobe.d/radeon.conf

```with content
```

options radeon new_pll=0 modeset=0

```Restart.



---

