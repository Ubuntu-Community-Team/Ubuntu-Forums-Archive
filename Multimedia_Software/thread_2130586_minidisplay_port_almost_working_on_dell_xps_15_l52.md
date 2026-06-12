---
title: "minidisplay port almost working on dell xps 15 l521x"
date: 2013-03-29
forum: Multimedia Software
---

### Post by MartinLL on 2013-03-29
Hello!

On this laptop, there is an HDMI port and a mini display port. I have the whole bumblebee/optimus thing setup and working great.

As far as I can tell, both the HDMI port and the mini display port are connected to the intel card, which is good news!

The problem is, only the HDMI port 'just works'. The minidisplay port seems to detect and possible ID the monitor (according the the Xorg.0.log), but the display tools do not seem to recognize what is going on.

I am using a minidisplay port to DVI adapter from monoprice. The same thing below happens if I use minidisplayport to VGA. Both work in windows.

Here is xrandr -q output with nothing plugged in:
```

Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080      60.0*+   59.9     40.0  
*** snip ***
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```

Here is xrandr -q output and the last couple lines of the Xorg.0.log with the HDMI plugged in:

```

Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080      60.0*+   59.9     40.0  
*** snip ***
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
*** snip ***
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)

AND the last couple lines from the Xorg.0.log ->

[ 19435.331] (II) intel(0): EDID vendor "AUO", prod id 237
[ 19435.331] (II) intel(0): Printing DDC gathered Modelines:
[ 19435.331] (II) intel(0): Modeline "1920x1080"x0.0  136.20  1920 1968 2068 2086  1080 1083 1084 1088 +hsync -vsync (65.3 kHz eP)
[ 19435.331] (II) intel(0): Modeline "1920x1080"x0.0   90.80  1920 1968 2068 2086  1080 1083 1084 1088 +hsync -vsync (43.5 kHz e)
[B][ 19435.496] (II) intel(0): Allocated new frame buffer 1920x1080 stride 7680, tiled
[/B]


```

When I plug into the mini display port, the screen flickers, but xrandr -q shows the exact same info as if nothing was plugged in. BUT, the Xorg.0.log shows the following... its the same thing as the HDMI, but it is missing the last line! (when I run the display tool, the monitor does not show up).

```

[ 19511.024] (II) intel(0): EDID vendor "AUO", prod id 237
[ 19511.024] (II) intel(0): Printing DDC gathered Modelines:
[ 19511.024] (II) intel(0): Modeline "1920x1080"x0.0  136.20  1920 1968 2068 2086  1080 1083 1084 1088 +hsync -vsync (65.3 kHz eP)
[ 19511.024] (II) intel(0): Modeline "1920x1080"x0.0   90.80  1920 1968 2068 2086  1080 1083 1084 1088 +hsync -vsync (43.5 kHz e)

```


Here is the entire Xorg.0.log ->
[http://paste.ubuntu.com/5660023/](http://paste.ubuntu.com/5660023/)

The log for Xorg.8.log ... the optimus/bumblebee stuff has nothing of interest and DISPLAY=:8 xrandr -q shows only a single 'screen' at 640x480

I have no xorg.conf file.

From my uneducated guessing it looks like X is just not taking the next step and setting things up on the display port?

---

### Post by MartinLL on 2013-04-02
Just an update...

I figured out that some of my statements above are wrong... so here are the updates:

- The xorg.0.log does not show anything being plugged into the DP1 as I had thought.... that info is for the built-in LCD! I know this because I tried plugging into a 1600x1200 monitor and the exact same thing was printed, which are the specs for the LCD and not the specs for the external monitor.

- I tried the xorg-edgers ppa which updated the intel driver and everything else. It did not fix anything.

- I've been searching for things like 'ubuntu intel display port monitor not detected' and the like and possibly found people with similar problems, but no real solution.

So... I'll revise my question to: The xorg startup log shows that DP1 is there, and xrandr shows that DP1 is there, but how do I get it to actually detect something is being plugged in?

---

### Post by MartinLL on 2013-04-02
I think this thread should be in the hardware subforum?  Can I move this over there somehow?

I did some more digging and I think this is a driver issue. The driver is not reporting the monitor as connected or enabled.

There are a couple files in /sys/ --->
```

martin@xps15:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640M] (rev a1)

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/status
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/enabled

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1/status
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1/enabled

```

The status file contains either 'connected' or 'disconnected'. The enabled file contains either 'enabled' or 'disabled'.

HDMI works, so when I plug in my monitor via HDMI, the files report connected and enabled.

For the display port, the files always report disconnected and disabled.

Does this mean this is a driver issue? If so, where can I find info to start debugging, or where can I post some information to help anyone working on the driver out?

---

### Post by quazi on 2013-04-08
> **MartinLL said:**
> I think this thread should be in the hardware subforum?  Can I move this over there somehow?

I did some more digging and I think this is a driver issue. The driver is not reporting the monitor as connected or enabled.

There are a couple files in /sys/ --->
```

martin@xps15:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640M] (rev a1)

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/status
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/enabled

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1/status
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1/enabled

```

The status file contains either 'connected' or 'disconnected'. The enabled file contains either 'enabled' or 'disabled'.

HDMI works, so when I plug in my monitor via HDMI, the files report connected and enabled.

For the display port, the files always report disconnected and disabled.

Does this mean this is a driver issue? If so, where can I find info to start debugging, or where can I post some information to help anyone working on the driver out?

While looking into this issue myself, I found someone else who devised an undesirable workaround: [http://ubuntuforums.org/showthread.php?t=2105839](http://ubuntuforums.org/showthread.php?t=2105839)

They uninstalled bumblebee and found an xorg configuration that allowed them to use the mini display port. I'd much prefer to leave bumblebee installed as the battery life advantage is very significant.

---

### Post by MartinLL on 2013-04-10
> **quazi said:**
> While looking into this issue myself, I found someone else who devised an undesirable workaround: [http://ubuntuforums.org/showthread.php?t=2105839](http://ubuntuforums.org/showthread.php?t=2105839)

They uninstalled bumblebee and found an xorg configuration that allowed them to use the mini display port. I'd much prefer to leave bumblebee installed as the battery life advantage is very significant.

Yes... I found that too and agree that it is undesirable. For now I'm fine with HDMI... I have a DVI to HDMI dongle that works well. It is the scenario when I go somewhere and there is a random projector with VGA only.

Should this be filed anywhere on the intel driver site as a bug issue? Or maybe put into the Dell specific ubuntu subforum here? I'd be willing to collect debug info and test out thing.

---

