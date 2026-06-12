---
title: "nvidia 7600 GS problem"
date: 2009-07-03
forum: Multimedia Software
---

### Post by vitotol on 2009-07-03
hello guys i just put in my computer an nvidia 7600 GS and ubuntu start with  really low level resolution and i get a message tha my card can be detected... i installed the nvidia drivers but i got nothing... is there any way to make ubuntu recognize my card or i should put the old one back???

---

### Post by ajgreeny on 2009-07-03
How did you install the nvidia driver for the card?

---

### Post by vitotol on 2009-07-03
> **ajgreeny said:**
> How did you install the nvidia driver for the card?

i downloaded them from nvidia site. i also tried from Administration/Hardware Drivers but when i restart i always get the ubuntu didn't recognize your card message

is there a chance ubuntu don't support that card. on this machine i also have a partition with Debian Lenny. if i try to boot this distro, when x server starts my monitor shows an "out of range" message.

---

### Post by dirty5855 on 2009-07-03
I have a PNY 7600GS. It works just fine.
dualboot with vista. How about you?

---

### Post by vitotol on 2009-07-03
the lspci gives me this:
VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)

i also have an xp partition for football manager :)
and it works fine, no problem.

---

### Post by khelben1979 on 2009-07-03
Did you check at the nVidia website if your card is supported by the driver?

---

### Post by vitotol on 2009-07-03
it supposed to be supported, i don't know ... i just put my geforce 4200 and the resolution it's ok. i'm with the free drivers so i go to the system>administration>hardware drivers but there's no drivers there anymore :mad:

---

### Post by vitotol on 2009-07-04
when i'm running nvidia installer i get a warning that the libglx.so can't be found.

if i hit glx info i get:
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
```

and glxgear
```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

---

### Post by vitotol on 2009-07-06
well this is the xorg.conf
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

can anyone help me, i just don't want to reinstall ubuntu...

---

### Post by Cope57 on 2009-07-06
```
# dpkg-reconfigure xserver-xorg
```

OR as a normal user:
```
$ sudo dpkg-reconfigure xserver-xorg
```
Just follow on screen questions and you should able to restore or reconfigure to previous state.

> Please see Chapter 3 of the [README]("http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/README/chapter-03.html") or run **man nvidia-xconfig** for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the [README]("http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/README/index.html"). [~ NVIDIA]("http://www.nvidia.com")

---

### Post by Cope57 on 2009-07-06
Just found a link with pictures and what not to help you out.

[How to fix your computer's graphics with dpkg-reconfigure]("http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure")

Hope this helps your situation.

---

### Post by vitotol on 2009-07-06
helpful links

---

### Post by vitotol on 2009-07-08
hey guys, the only way that nvidia drivers worked for me, except the Administration> Hardware Drivers way, is this ->
[http://desiato.tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html]("http://desiato.tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html")

i followed it's instructions in my debian partition, i hope it works for ubuntu too.

---

