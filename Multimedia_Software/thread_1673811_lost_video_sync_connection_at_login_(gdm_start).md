---
title: "lost video sync connection at login (gdm start)"
date: 2011-01-23
forum: Multimedia Software
---

### Post by Machtyn on 2011-01-23
I recently purchased a new motherboard and processor to replace an existing system.  I transferred the video card.  OS remains the same, Ubuntu 10.10 x64.  Video worked fine in the first system (eVGA motherboard, Intel E6600 CPU, 4GB RAM), but the old motherboard had a SATA controller issue.

New system: Gigabyte GA-890FXA-UD5, AMD Phenom II X4 955 Black Edition Deneb, 8GB RAM

Transferred hardware: 
 Graphics: eVGA nVidia 8800GT, 
 Monitor 0: Hanns-G JW199D 1440x900@60Hz
 Monitor 1: Gateway FPD1975W 1440x900@60Hz

The Problem:
1. Fresh OS install, everything starts up as expected, login, etc. 
2. I use the Additional Drivers link from the menu and select the recommended nVidia driver and enable it.
3. After reboot, the following things happen:
3a. BIOS
3b. Ubuntu startup scripts
3c. Ubuntu logo with spinning dots
3d. Monitor goes black
3e. Monitor notifies it has lost sync

I believe 3d is where I would normally get the login dialog.  I can use failsafe mode, but everything I've tried to fix the graphics display hasn't worked.  I've even tried to load the latest nVidia driver, nvidia-config, nvidia-settings, etc.  There are some options I've tried where the nvidia-x command returns "can't find device".  I've tried to modify the xorg.conf file, to no success.

Any ideas what I can do to resolve the error?  I'm not that strong on the xorg.conf file, but all I've read is that it's not too necessary anymore.  Though, it was modified in my old system to get Twinview working.  I've looked through a bunch of log files, but I may not have been looking in the correct log file.  

Thank you for any suggestions and help!

---

### Post by Machtyn on 2011-01-23
I wanted to add some more information about where I've now ended up.  

I've reinstalled the NVIDIA driver a number of times, tried nvidia-xconfig, nvidia-detector (which reports "none"), xrandr (reports "Can't open display"), and some other things.  My system is now booting straight to the shell and not X.  (I'm not sure how or why it started doing that.)  sudo start gdm and sudo startx does nothing for me.

startx returns the following:
```

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0): *** Aborting ***
(EE) Scree(s) found, but none have a usable configuration.

```

The above also mentions something about a version mismatch, but it doesn't make sense since I used nVidia's run file and nothing else.

I'll copy the relevant sections of my xorg.conf file.  

```

Section "ServerLayout"
   Identifier   "Layout0"
   Screen    0  "Screen0" 0 0
   InputDevice  "Keyboard0" "CoreKeyboard"
   InputDevice  "Mouse0" "Corepointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
   ... stuff for the mouse ...
EndSection

Section "InputDevice"
   ... stuff for the keyboard ...
EndSection

Section "Monitor"
   Identifier    "Monitor0"
   VendorName    "Hanns-G"
   ModelName     "JW199D"
   HorizSync     28.0 - 33.0
   VertRefresh   60.0 - 72.0
   Option        "DPMS"
EndSection

#Section "Monitor"
#   Identifier    "Monitor0"
#   VendorName    "Gateway"
#   ModelName     "FPD1975W"
#   HorizSync     28.0 - 33.0
#   VertRefresh   60.0 - 72.0
#   Option        "DPMS"
#EndSection

Section "Device"
   Identifier    "Device0"
   Driver        "nvidia"
   VendorName    "NVIDIA Corporation"
#   Option        "TwinView"            "True"
#   Option        "TwinViewOrientation" "RightOf"
   Option        "UseEdidFreqs"        "True"
#   Option        "MetaModes"           "1440x900,1440x900; 1280x1024,1280x1024"
#   Option        "UseDisplayDevice"    "DFP"
EndSection

Section "Screen"
    Identifier    "Screen0"
    Device        "Device0"
    Monitor       "Monitor0"
    DefaultDepth  24
    SubSection    "Display"
       Depth      24
    EndSubSection
EndSection

```

If I change the Driver "nvidia" to Driver "nv", I get X back, but trying to use the NVIDIA X Server Settings form gives me 
```

You do not appear to be using the NVIDIA X driver.
Please edit your X configuration file (just run `nvidia-
xconfig` as root), and restart the X server.

```
Again, I really do appreciate any help a person may give me.

---

### Post by Machtyn on 2011-01-24
I finally pulled out a CRT monitor to see if it was a resolution or refresh issue.  But the same thing happened - Ubuntu logo during OS load, then as the login screen was about to display, I get blackness and the monitor loses signal.

Unfortunately, it doesn't appear any here is going to be able to assist me.  Thanks to those who took a gander at my post.  I'm going to have to put Windows XP on this thing for just a little longer, I guess.

Additional notes:
1. I did uninstall the Nouveau drivers.
2. In order to get a Gnome desktop back, I changed my xorg.conf file so that the driver read Driver "nv" instead of Driver "nvidia".

As mentioned before, my nvidia driver worked fine with an Intel motherboard and CPU and this same graphics card.  Now I have an AMD motherboard and CPU.

---

### Post by Machtyn on 2011-01-29
I'm still no further than I was before :(  I've read through every chapter and appendix of the NVIDIA README file, nothing in there has helped me, yet.

I can't tell if Nouveau is being started by initrd, or if Ubuntu even uses that during the boot process.

Still the same problem after multiple OS wipe and reinstalls (it's nice that the install process is only about 15 minutes).  Each time I tried some different configuration, some different steps in different order (such as remove Nouveau, install nvidia driver; remove nouveau, install all updates, install nvidia driver; booting with one monitor, only; booting with monitors switched on port).  Each time I see the Ubuntu load screen, then right before the login screen displays, the monitor goes dark and loses "connection".

I'm attaching in a bz2 file, my Xorg.conf file and Xorg.0.log file from previous boot (I've booted off the liveCD).  I've also attached the log files from the gdm folder (in the bz2 file)

I'm trying to figure out how to have X start in logverbose level 5 or higher, but I can't find the correct file to edit, yet.  I'll track it down soon enough.

Again, any and all help is appreciated.

---

