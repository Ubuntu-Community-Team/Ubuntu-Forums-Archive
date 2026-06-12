---
title: "OpenGL and MultiGPU"
date: 2013-04-03
forum: Multimedia Software
---

### Post by sumodds on 2013-04-03
We are trying to setup a server with Multiple Tesla M2050 to run with OpenGL. 

  The current setup is as follows : Ubuntu 12.04 with NVidia Drivers.  We have setup the xorg.conf with separate devices identified by BUS ID. Now we have tied an X server each with display which in turn is tied  to each device and our code is attached to each of these X servers. But  somehow only one X session seems to work out alright. The other one  produces garbled output and while watching it from nvidia-smi, we notice  that when the garbled output is being produced the GPU's are not at all  used. Could someone verify that our setup seems reasonable? The other thing  we noticed was that, it was only the first X server that was started is  the one that has the issue.
      
> Section "ServerLayout"
    Identifier     "gpu0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerLayout"
    Identifier     "gpu1"
    Screen      0  "Screen1" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
    Identifier     "Card0"
    Driver         "nvidia"
    BusID          "PCI:0:3:0"
EndSection

Section "Device"
    Identifier     "Card1"
    Driver         "nvidia"
    BusID          "PCI:0:4:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Card1"
    Monitor        "Monitor1"
    SubSection     "Display"
        Viewport    0 0
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       4
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       8
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       15
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       16
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
    EndSubSection
EndSection



Now, when we ran a single X server pointing to either of these ServerLayouts, it works fine.  The issue is when I run two X servers at the same exact time one pointing to one ServerLayout and one to the other. Anything trying to use the first one that was started will always have issues.  Both x servers are started as so: 
> openvt -fw -- su -c "startx -- ${DISPLAY} -logverbose 20 -config xorg.${LAYOUT}.conf -layout ${LAYOUT}" xuser  where for one X server, DISPLAY=:0 LAYOUT=gpu0  and the other is DISPLAY=:1 LAYOUT=gpu1  If the X server is started first for :0 the :1, any rendering using OpenGL I try to do on :0 will result in either freezing, rendering fuzz, or rendering a black screen.  If these instances supported SLI, this wouldn't be an issue, but unfortunately, they don't.  Any help or direction on this matter would be much appreciated as I haven't found a great way to debug what is going on or whether the issue lies in X or the nvidia drivers (310.40).

---

