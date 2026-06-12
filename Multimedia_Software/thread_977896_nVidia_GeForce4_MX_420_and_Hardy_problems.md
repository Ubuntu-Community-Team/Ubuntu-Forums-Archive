---
title: "nVidia GeForce4 MX 420 and Hardy problems"
date: 2008-11-10
forum: Multimedia Software
---

### Post by pdc124 on 2008-11-10
Little sister's WinXP computer  has failed and Ive jumped in and offered them Hardy Heron for free - so far theyve accepted. 

the problem is with the screen display - periodically it goes haywire with windows moving of their own volition and taskbar icons flashing . it needs switching off when this happens , and then switching on again . I 'think' ive  installed  the nvidia  driver  from the restricted repository)  (sorry new to ubuntu - didnt have the time to put together  gentoo system _

if i cant get this fixed, they'll go and buy a machine with Vista on it, as the kids have to have a working  machine

hardware 

01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

/etc/X11/xorg.conf

andrew@desktop:~$ cat  /etc/X11/xorg.conf | gep -v '#'
-bash: gep: command not found
andrew@desktop:~$
andrew@desktop:~$ cat  /etc/X11/xorg.conf | grep -v '#'

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection
andrew@desktop:~$    

and this happens  in Xorg log 
```

<snipped a bit>
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
[config/hal] couldn't initialise context: (null) ((null))
(II) NVIDIA(0): Setting mode "1024x768_70"
(II) 3rd Button detected: disabling emulate3Button
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
mieqEnequeue: out-of-order valuator event; dropping.
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late
tossed event which came in late

```
andrew@desktop:~$ lsmod | grep nv
nvidia               4718832  22
i2c_core               24832  1 nvidia
agpgart                34760  2 nvidia,intel_agp
andrew@desktop:~$

---

### Post by pdc124 on 2008-11-12
thisis getting urgent to try and come up with a solution that leaves them with a working machine - otherwise  it will  be a new machine with Vista on it. 

can i downgrade ( or upgrade)  from Hardy Heron  to try and find a fix ? 

Ive got command line access through a reverse SSH  tunnel

---

### Post by WSmart on 2008-11-12
The older Nvidia cards, the legacy drivers, have an issue with the new xorg 1.5 and Jockey restricted driver manger.   There's a new driver in the Intreprid proposed repository.

---

### Post by pdc124 on 2008-11-12
so how do i get the new driver ? ( im new to ubuntu , Im afraid) or downgrade the current one ( ?? to nv ).

---

### Post by pdc124 on 2008-11-15
sorry to hassle - thiis is getting quite urgent.

how do i downgrade the system  or how do i configure X to use a different driver ( thats already on the system) eg nv rather than nvidia . 

they dont need fancy graphics , just a stable usable system

---

### Post by Yellow Pasque on 2008-11-15
> **pdc124 said:**
> so how do i get the new driver ? ( im new to ubuntu , Im afraid) or downgrade the current one ( ?? to nv ).
Enable the proposed repo.
```
kdesu kate /etc/apt/sources.list
```
Add this line to the end of the file:
```
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed universe main multiverse restricted
```
Save. Quit. Now you can get the updated driver through update manager.

---

