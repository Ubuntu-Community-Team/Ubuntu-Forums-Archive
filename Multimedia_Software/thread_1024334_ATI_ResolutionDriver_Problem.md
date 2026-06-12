---
title: "ATI Resolution/Driver Problem"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Ryangarve on 2008-12-28
Hey Everyone,

I'm running an IBM T60-2623-OTU on 8.10.  The Laptop has an ATI Mobility Radeon X1300 and has the capability to run in 1400 x 1050.  I can only run in 1024 x 768 and am currently running the open source driver.  I want to try and use the Proprietary driver, but when I try to activate it, it appears to install but never activates.  

I'm not sure if this helps, but here is the output from sudo lshw -C display

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: M52 [Mobility Radeon X1300]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

Thanks for any help in advance!

---

### Post by lavinog on 2008-12-29
what does glxinfo|head
and fglrxinfo report?

---

### Post by Ryangarve on 2008-12-29
I ran the two commands and got this first

**glxinfo|head**
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10
name of display: :0.0

**fglrxinfo**
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 143 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 10
Current serial number in output stream: 10

I did a search on that and found this on another forum and ran it also.

Based on this [https://bugs.launchpad.net/fglrx/+bug/292771/comments/9](https://bugs.launchpad.net/fglrx/+bug/292771/comments/9) it means that the neccessary kernel module has not been loaded.

I performed the following

# apt-get remove --purge xserver-xorg-video-radeon

# apt-get remove --purge fglrx-kernel-source

# apt-get install fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev

After this I was able to activate and use the proprietary driver, but I still only have a max resolution of **1024 x 768**.

[B]
glxinfo | head[/B]
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI

[B]
fglrxinfo[/B]
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.1.8087 Release

---

### Post by lavinog on 2008-12-29
I came across the resolution issue on one computer, it turned out to be the monitor didn't support the Extended display identification data (EDID).
I had to modify /etc/X11/xorg.conf to force it into the higher resolution.
give me a couple of mins to look up what I did.
If you have another monitor available, see if it displays the correct resolution.

---

### Post by lavinog on 2008-12-29
edit /etc/X11/xorg.conf
press alt-f2 and type
```
gksudo gedit /etc/X11/xorg.conf
```
near the bottom you should see a section called "Screen", and in it you should see a subsection called "Display"
if you see more than one display subsection you should enter this in each one
```
Modes "1400x1050" "1280x1024" "1024x768"
```

for example:
```

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes "1400x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection

```

after the change, save the file and reboot. (restarting X should be all that is needed, but a full reboot might offer better results)

If that doesn't work post your xorg.conf file.

---

### Post by Ryangarve on 2008-12-29
I went ahead and overlaid your code over the old screen section, but it did not work.  After I restarted the computer I had to revert back to the original graphics config.  Here is the post xorg.conf file.  As you can see I pulled out the code you had mentioed

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection  

When I had your code in there it looked like this


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes "1400x1050" "1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

---

### Post by lavinog on 2008-12-31
The problem was the identifiers didn't match up
Try this
```

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1400x1050" "1280x1024" "1024x768"
 EndSubSection
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection


```

The Indentifier names and the Device names have to be able to cross reference each other

---

### Post by dorush on 2009-10-27
Hi, I've been having the same problem here. I'm trying to force my resolution into 1680x1040 for a while now. Only everytime I try to change xorg.conf I get a fatal error at reboot. 
I have recently installed a driver for ATi Radeon RD4800 series, 3d works excellently now, but yeah... resolution fails.. If someone could help me with this, I'd really appreciate it, have spent a lot of hours on this =.=


my xorg.conf:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option        "VendorName" "ATI Proprietary Driver"
         Option        "ModelName" "Generic Autodetecting Monitor"
         Option        "DPMS" "true"
EndSection

Section "Device"
         Identifier  "Configured Video Device"
EndSection

Section "Device"
         Identifier  "aticonfig-Device[0]-0"
         Driver      "fglrx"
         BusID       "PCI:1:0:0"
EndSection

Section "Screen"
         Identifier "Default Screen"
         Device     "Configured Video Device"
         Monitor    "Configured Monitor"
EndSection

Section "Screen"
         Identifier "aticonfig-Screen[0]-0"
         Device     "aticonfig-Device[0]-0"
         Monitor    "aticonfig-Monitor[0]-0"
         DefaultDepth     24
         SubSection "Display"
                 Viewport   0 0
                 Depth     24
         EndSubSection
EndSection

```

---

### Post by lavinog on 2009-10-27
> **dorush said:**
> Hi, I've been having the same problem here. I'm trying to force my resolution into 1680x1040 for a while now. Only everytime I try to change xorg.conf I get a fatal error at reboot. 
I have recently installed a driver for ATi Radeon RD4800 series, 3d works excellently now, but yeah... resolution fails.. If someone could help me with this, I'd really appreciate it, have spent a lot of hours on this =.=
...
You should always start a new thread...especially since this one is pretty old.
Please specify which version of ubuntu are you using 9.04 or 9.10?
What changes to xorg.conf did you try that caused errors?
What model monitor do you have?

Have you tried using catalyst to change the resolution?

Does this work?
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option        "VendorName" "ATI Proprietary Driver"
         Option        "ModelName" "Generic Autodetecting Monitor"
         Option        "DPMS" "true"
EndSection

Section "Device"
         Identifier  "Configured Video Device"
EndSection

Section "Device"
         Identifier  "aticonfig-Device[0]-0"
         Driver      "fglrx"
         BusID       "PCI:1:0:0"
EndSection

Section "Screen"
         Identifier "Default Screen"
         Device     "Configured Video Device"
         Monitor    "Configured Monitor"
EndSection

Section "Screen"
         Identifier "aticonfig-Screen[0]-0"
         Device     "aticonfig-Device[0]-0"
         Monitor    "aticonfig-Monitor[0]-0"
         DefaultDepth     24
         SubSection "Display"
                 Viewport   0 0
                 Depth     24
**Modes "1680x1040" "1280x1024" "1024x768"**

         EndSubSection
EndSection

```

---

