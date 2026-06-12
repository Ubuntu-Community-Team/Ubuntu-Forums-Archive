---
title: "Change in Monitor Preferences caused Compiz to fail to load"
date: 2010-12-26
forum: Multimedia Software
---

### Post by Gforce20 on 2010-12-26
I recently got a Radeon HD 2400 Pro. After installing it and getting dual monitors working, Compiz was fine. But I did something in "Monitor Preferences" that caused it to break - I tried to change the resolution of my 19" monitor to 1440x900 (its highest resolution), and received a dialog box saying something about an unsupported resolution and virtual screens, and I needed to authenticate via something like gksudo. I was also instructed to reboot. After rebooting, Compiz would no longer load, leaving me with Metacity. Error messages point to a lack of OpenGL support:

```
$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
``````
$ compiz
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Window manager warning: "" found in configuration database is not a valid value for keybinding "show_desktop"
```
What else should I check?

---

### Post by tjones00 on 2010-12-26
What driver are you using?
How are the monitors connected?
Are you editing the resolutions manually in xorg.conf yourself or using a gui tool?


Post your xorg.conf (/etc/X11/xorg.conf) and Xorg.0.log (/var/log/Xorg.0.log)
Also, if you are using the radeon driver (not sure if xrandr is used with ati prop) the output from ```
sudo xrandr -q
``` might help.

Link to Radeon HD 2600 tech specs.
[http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-2000/hd-2400/Pages/ati-radeon-hd-2400-gpu-specs.aspx](http://www.amd.com/us/products/desktop/graphics/ati-radeon-hd-2000/hd-2400/Pages/ati-radeon-hd-2400-gpu-specs.aspx)

---

### Post by Gforce20 on 2010-12-26
How do I determine the driver I'm using? If it matters, XOrg loads modules "ati" and "radeon" upon initializaton.

The monitors, which use VGA, are connected to two DVI &#8594; VGA converters, which are each connected to what looks like a DMS-59 &#8594; DVI splitter (if that's what it's called). The DMS-59 output comes from the Radeon card.

I only used Monitor Preferences when the error occurred. I have since tried to fix the problem through xorg.conf, but to no avail.

My current xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver          "ati"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
EndSection
```
There was no xorg.conf before the error. Truncating or deleting the file does not fix the problem, unfortunately.

[Xorg.0.log](http://pastebin.com/dwYCehqY) (pastebin'd due to length)

```
# xrandr -q
Screen 0: minimum 320 x 200, current 2720 x 1024, maximum 8192 x 8192
DVI-0 connected 1280x1024+1440+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DIN disconnected (normal left inverted right x axis y axis)
DVI-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1
```

---

### Post by Gforce20 on 2010-12-26
After taking the time to look through the output of xrandr, I have a strong feeling that this is relevant to the issue:

```
DVI-0 connected 1280x1024+1440+0 (normal left inverted right x axis y axis) 338mm x 270mm
```

This should probably read 1280x1024+0+0, instead of +1440+0. I'll see if I can figure out how to change that and report back.

EDIT:

```
(EE) GLX error: Can not get required symbols.
```

This is probably significant too.

---

### Post by Gforce20 on 2010-12-26
I fixed the original problem by reverting to fglrx. This wasn't the intended solution, as fglrx was extremely slow the last time I tried it, but it seems to be doing better now for whatever reason.

---

### Post by tjones00 on 2010-12-27
If you go back and revisit the problem. Here's some information.

When doing lsmod if "ati" or "radeon" are displayed that is the open source radeon driver, if "fglrx" is displayed that is the proprietary ati driver.

The xrandr output with +1440+0 was just positioning of the 2nd monitor. It was offset 1440 to the right so it would not overlap the 1440x900 monitor.

1440x900 monitor @ 0,0 then the 1280x1024 monitor 1440,0 to the right of the first monitor.

The displays appeared to be setup properly with radeon.

As to GLX lets leave that for now unless you revisit the radeon driver.

It seems people are having issues setting up dual monitors with the opensource radeon driver lately. I bet we would have had to fuss with some driver options in xorg.conf for your issue.

---

