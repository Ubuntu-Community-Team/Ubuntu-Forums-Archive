---
title: "Cannot enable Compiz in Karmic Koala 9.10"
date: 2009-12-01
forum: Multimedia Software
---

### Post by AintJoe on 2009-12-01
I am running Ubuntu Karmic Koala 9.10 on a Dell Latitude D610 with a docking station and a monitor. 
The monitor is set as the primary display with resolution 1280x1024 and its extended to the laptop screen which is 1024x768. 

The graphics card for this machine according to "lspci -vvv" is:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Device 0182
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at ec38 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

```

I tried to enable Compiz (System-> Preferences -> Appearance -> Visual Effects -> Normal).
It says "Searching for available drivers..", then "Desktop effects could not be enabled." 

Then I tried, "compiz --replace &" and it returns:
```

xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect renderSKIP_CHECKS=yes compiz --replaceing:
**Checking for texture_from_pixmap: not present. **
aborting and using fallback: /usr/bin/metacity

```

Next, I tried, "SKIP_CHECKS=yes compiz --replace &":
```

xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
running under gnome seesion, checking for gnomecompat
**Checking for Xgl: not present. **
compiz.real: ../../src/xcb_io.c:542: _XRead: Assertion `dpy->xcb->reply_data != ((void *)0)' failed.
Aborted

```

xserver-xorg-video-intel is installed.

Does anyone have any other suggestions?

---

### Post by zasq on 2009-12-08
Hello!
Same problem here. Any solution?

Here's the output of "compiz --replace &":

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

---

### Post by psytrox on 2010-01-17
Same here. I had run a cleaning program, for old .deb files, config, residual, etc...(can't remember the name), and it seemed weird that it looked to be actually uninstalling packages, not just deleting extra files.  Now I have a black rectangle around anything compiz(AWN bar, specifically).  Any changes made in Ubuntu Tweak, have no effect(e.g. title bar won't shade, or "roll up" any longer, but middle-click still lowers the window, and double click maximizes still).  I'm going to attempt using envy, to fix.  If that doesn't work, I'll check /etc/X11/xorg.conf for composite settings.  Thank you.

---

### Post by psytrox on 2010-01-17
Envy doesn't look to support Intel drivers, and adding 

"Section "Extensions"
    Option         "Composite" "Enable"
EndSection"

to /etc/X11/xorg.conf....did nothing, except make metacity not work like it was.

(Earlier, I found that using metacity instead of compiz, gets rid of the black boxes around AWN bar, for instance, but that's not working the same, after adding above to /etc/X11/xorg.conf)


Still not working.

---

### Post by opto09 on 2010-01-24
Same here. Still no fix? I'd really like to get awn running again as I had it before updating.


```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Dell Device 01d8
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at eff00000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at eff8 [size=8]
	Region 2: Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at efec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: i915

```

---

### Post by Yellow Pasque on 2010-01-25
For those having problems, please check:
```
LIBGL_DEBUG=verbose glxinfo
```
and maybe:
```
cat /var/log/Xorg.0.log | grep AIGLX
```

> Checking for Xgl: not present.
Don't worry about that.

---

### Post by illbashu on 2010-01-30
nm...

---

### Post by opto09 on 2010-02-08
```
LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

Hm does that help?

---

### Post by Yellow Pasque on 2010-02-08
> **opto09 said:**
> ```
LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16
```

Hm does that help?
Yes, it means you have a bad libglx.so

What video chip do you have and what driver are you trying to use?

---

### Post by opto09 on 2010-02-08
I have an intel chip:

```
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
```

---

### Post by opto09 on 2010-02-08
And driver is xserver-xorg-video-intel (I think?). Although when I try to enable compiz via the appearance window it goes searching for drivers although i don't think it installs anything. Also if this helps:

$ grep EE /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "i810" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) intel(0): [drm] Failed to open DRM device for : No such file or directory
(EE) intel(0): Failed to become DRM master.
(EE) intel(0): Failed to initialize kernel memory manager
(EE) GLX error: Can not get required symbols.

---

