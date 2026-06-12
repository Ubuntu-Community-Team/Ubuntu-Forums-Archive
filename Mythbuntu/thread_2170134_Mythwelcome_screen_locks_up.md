---
title: "Mythwelcome screen locks up"
date: 2013-08-25
forum: Mythbuntu
---

### Post by Pierre_duParte on 2013-08-25
Hi all

I am having a problem with mythwelcome on HDMI. Once it starts and the "start frontend" button is is clicked it locks up the screen. The mythfrontend does actually seem to load, bu the mythwelcome screen stays up. At this point no key combination works (move to alt desktop, shell etc), but the mouse cursor is alive and well. Here's a typical log output:

```

Aug 25 14:58:57 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 14:58:58 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 14:59:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 14:59:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 14:59:30 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 14:59:30 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 14:59:57 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 14:59:58 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:00:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:00:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:00:30 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:00:30 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:00:57 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:00:58 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:01:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:01:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:01:30 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:01:30 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:01:57 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:01:58 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:02:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:02:00 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:02:01 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2538 (LockInputDevices) Locking input devices
Aug 25 15:02:01 mythserver01 mythwelcome[2435]: I CoreContext mythmainwindow.cpp:2540 (LockInputDevices) Unlocking input devices
Aug 25 15:02:05 mythserver01 mythwelcome[2435]: I CoreContext mythrender_opengl1.cpp:280 (DeleteOpenGLResources) OpenGL1: Deleting OpenGL Resources
Aug 25 15:02:05 mythserver01 mythwelcome[2435]: I CoreContext mythrender_opengl.cpp:1038 (DeleteOpenGLResources) OpenGL: Deleting OpenGL Resources
Aug 25 15:02:05 mythserver01 mythwelcome[2435]: E CoreContext mythmainwindow.cpp:1309 (detach) Could not find widget to detach
```

This is the xorg.conf on the system:

```
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[0]-0" 0 0
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[0]-0"
    Device     "amdcccle-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

Turning the screen off and will then display the front end, but at some weird resolution. 

I have tried different refresh rates, where I suspect the problems lies, but it's made no difference.

Any tips or help would do my blood pressure and sanity a world of good. Thanks...

---

