---
title: "nvidia 7150/compiz"
date: 2007-11-12
forum: Multimedia &amp; Video
---

### Post by eeerik on 2007-11-12
Been working on this for hours, none of the other threads have helped me.
Problem is that I get the error message "Desktop effects can not be enabled" when I try to activate them. 

I have a Nvidia Geforce Go 7150, and have activated the restricted driver.
nvidia-settings shows that it recognizes it for what it is, but the Open GL/GLX Information tab only shows that "Fail to query the GLX server vendor".

In one of the other threads, the workaround to get compiz working here is to go to synaptics and activate xserver-xgl. I can go in and do this, but upon restarting X it only gets as far as to let me login and then restarts the process. I can select session Gnome Failsafe and uninstall xserver-xgl and things are back to normal.

Here is somet other information for you:

(from /etc/X11/xorg.conf)
> Section "Device"
        Identifier      "Failsafe Device"
        Driver          "nvidia"
        Busid           "PCI:0:18:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   16
                Modes           "800x600"
        EndSubSection
EndSection


Here the weird thing is that it says 800x600, but Im running it at the native which is 1280x800. I dont know if this is whats causing trouble, or what do do if it is. In Screens/graphics and nvidia-settings it lists 1280x800.

lspci grep VGA gives:
> 00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2)

Running compiz from terminal gives :
> 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:12.0 0300: 10de:0531 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 



Does anybody have any ideas?
Thanks for any elp!

---

