---
title: "Nvidia FX 5200, No go"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by Tierce on 2006-10-04
Hi there,

I've been having some difficulty getting my Nvidia Geforce FX 5200 card to work with OpenGL. I have Gnome running fine, but as to using Blender, I get
```
Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window

```

I have tried both nvidia-glx, and nvidia-glx-legacy with Synaptic.
I got told on runing 'sudo nvidia-glx config enable' that I needed to change 'nv' to 'nvidia.' I did. I even ran the overide command to change the MD5sums. I re-boot X and it's good I have a backup of the X.org conf file since I get told that, "cannot load nvidia kernal module!" Or something like that.

I have:
>linux-restricted-modules-2.6.15-23-amd64-generic
>linux-image-2.6.15-23-amd64-generic
installed.

My system is:
Ubuntu Dapper
AMD 3200+ 64bit
512 MB RAM
Motherboard: ASUS A8V
NVIDIA GeForce FX 5200 128MB AGP8X


So, any help or advice would be appreciated. Or, your settings you used on your PC, those lucky people who installed it without a hitch. :p

---

### Post by hanzomon4 on 2006-10-05
Check to make sure you installed the nvidia drivers correctly. Check method 1 of this guide [Latest Nvidia Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")


Now if you did all that try this...
First open your xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

Next find the "Module" section... press ctrl+f and paste "Module"

Now add this line to the module section ```
Load       "glx"
```

This is what mine looks like ```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load          "dri"
    Load           "extmod"
    Load           "freetype"
    [COLOR="Red"]**Load           "glx"**[/COLOR]
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
EndSection

```

Then restart X "ctrl+alt+backspace"

---

### Post by Tierce on 2006-10-08
Thanks a lot. That got it working.

:-D :-D :-D :-D :-D :-D 

Cheers.

---

