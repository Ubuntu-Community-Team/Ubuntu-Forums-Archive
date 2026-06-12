---
title: "3 monitor desktop config problem"
date: 2009-09-11
forum: Multimedia Software
---

### Post by belligerent_bill on 2009-09-11
I'm currently using a 3 monitor configuration in Jaunty.  When I initially had two monitors configured with twin view in NVIDIA X Settings I was able to create a separate panel at the bottom of each monitor.  I had them configured in such a way that when you drag a window from one monitor to the next the program would show up on the panel corresponding to the monitor the window is active on.  Also, when I would expand a Window on a monitor it would only expand on that monitor.  

Since I have added a third monitor things have changed.  The third monitor had to be configured as a separate X Screen.  So I can't drag application windows to or from this monitor.  The original two monitors that I had configured with twin view are now functioning as one large monitor.  When you expand a window it expands between the two monitors, and you can't configure a separate panel for each monitor.  

At the very least I would like the original two monitors to function like they did before I added the third monitor.  Also, if there is any way to get the third monitor to work without being a separate X Screen that would be great! I would love to be able to drag applications to and from the monitor.  Any assistance would be appreciated.  Xorg.conf is posted below.  
    


Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by belligerent_bill on 2009-09-14
Any suggestions?

---

### Post by belligerent_bill on 2009-09-15
I also am unable to enable desktop effects since I moved to the Ubuntu NVIDIA driver.  Desktop effects worked with the driver I downloaded and compiled from nvidia.com however every time there was a Ubuntu kernel update the driver would have to be recompiled.  If anyone knows how to get the effects working with the Ubuntu driver please let me know.

---

### Post by belligerent_bill on 2009-09-30
Bump, please read, please help....

---

### Post by markbuntu on 2009-10-01
Did you add a second gpu for the third monitor?

---

### Post by kitchenware on 2009-10-02
Sounds like the cards are incompatible. Check /var/log/Xorg.0.log for a warning message saying this and if so get another matching card.

---

### Post by belligerent_bill on 2009-10-16
> **markbuntu said:**
> Did you add a second gpu for the third monitor?

Yes, the first two monitors are on GPU-0 and the third monitor is on GPU-1. (Per Nvidia X Settings)

---

