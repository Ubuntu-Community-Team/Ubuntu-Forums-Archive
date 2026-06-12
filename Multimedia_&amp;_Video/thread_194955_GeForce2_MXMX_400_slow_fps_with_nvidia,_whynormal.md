---
title: "GeForce2 MX/MX 400 slow fps with nvidia, why/normal?"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by towsonu2003 on 2006-06-12
I have a "GeForce2 MX/MX 400" (64 MB) and I'm using the nvidia-glx (not legacy as per nvidia's readme file) from the repos as the driver. However, the fps in average is around 350 (which seems very low, especially reading a couple of comments about this card via google). Can anyone help me understand if this is normal, and if it isn't, what I can do? There is a general sluggishnes in the desktop that I think is related to this (cpu: Intel(R) Celeron(R) CPU 1.70GHz, memory: 385M, swap: rarely used 490M). 

Here is what nvidia says about this card: [http://www.nvidia.com/page/geforce2mx.html](http://www.nvidia.com/page/geforce2mx.html)

I don't see any errors in Xorg.0.log and here is my xorg.conf
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
#       Load    "dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "tr"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "CPD-E200E"
    HorizSync       30.0 - 85.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "CPD-E200E"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

And here is the detailed lspci:
```

0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 185
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Expansion ROM at ed000000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 2.0

```

Fps originally was around 135 and I got it to 350 via Googling, but it doesn't go higher... Any help, especially from those who use this card, is sooo welcome :)

---

### Post by tseliot on 2006-06-12
I guess you can't expect an impressive performance from your card (just like I can't with my card ;)  )

Anyhow, can you post the output of the following commands?

```
dmesg | grep NVIDIA
```


```
glxinfo | grep direct
```


```
cat /proc/driver/nvidia/agp/status
```

---

### Post by towsonu2003 on 2006-06-12
yes, I guess I shouldn't expect much, but I donno what to expect :) Thanks for the reply though:[QUOTE=tseliot]
```
dmesg | grep NVIDIA
```[/quote]
```
[4294693.111000] nvidia: module license 'NVIDIA' taints kernel.
[4294693.121000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006

```
[QUOTE=tseliot]
```
glxinfo | grep direct
```[/quote]
```
direct rendering: Yes
```

[QUOTE=tseliot]
```
cat /proc/driver/nvidia/agp/status
```[/QUOTE]
```
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled

```

---

### Post by towsonu2003 on 2006-06-15
bumping

---

### Post by tseliot on 2006-06-15
Try enabling Fastwrites:
[http://www.ubuntuforums.org/showthread.php?t=140989]("http://www.ubuntuforums.org/showthread.php?t=140989")

---

