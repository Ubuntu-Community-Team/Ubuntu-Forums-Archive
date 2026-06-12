---
title: "Visual Effects removes my title bars???"
date: 2008-05-03
forum: Multimedia Software
---

### Post by gear_head on 2008-05-03
Just upgraded to 8.04 (Hardy)
I seem to have the nvidia driver properly installed as I get this "nvidia" splash screen just before the login pops up.

But When I go into System->Preferences->Appearance and activate visual effects, the title bars on all open windows disappear. I tried rebooting to no avail. The titlebars return when I turn off visual effects.

Any Idea what's going on here?

---

### Post by comandrei on 2008-05-03
try running emerald --replace & from a terminal

---

### Post by gear_head on 2008-05-03
> **comandrei said:**
> try running emerald --replace & from a terminal

...and then what?

This just kinda pauses and doesn't seem to do anything.

---

### Post by joselin on 2008-05-03
Do 
```
compiz --replace &
```
in a terminal window and post the output.

Regards

---

### Post by gear_head on 2008-05-03
> **joselin said:**
> Do 
```
compiz --replace &
```
in a terminal window and post the output.

Regards

```
jason@home-bass:~$ compiz --replace &
Checking for Xgl: [1] 6225
jason@home-bass:~$ not present. 
Detected PCI ID for VGA: 00:09.0 0300: 10de:0172 (rev a3) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

```

---

### Post by KaliVoid on 2008-05-03
Hi
i had the same problem

add :
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

to your xorg.conf in Section "Device" & ctrl+alt+Bckspace to start gdm

this is my Section "Device" :
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440"
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
EndSection

---

### Post by joselin on 2008-05-03
Try changing the Defaultdepth directive to 24 instead of 32.

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia..."
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

```

And add the following to your /etc/X11/xorg.conf:
```
Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True" 
```

Regards

---

### Post by joselin on 2008-05-03
Forget to say that you must restart your X server after doing it.

Regards

---

### Post by gear_head on 2008-05-03
Cool, that got it. thanks guys!

---

