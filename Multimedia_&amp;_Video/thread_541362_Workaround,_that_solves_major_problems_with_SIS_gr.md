---
title: "Workaround, that solves major problems with SIS graphics adapters"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by kissg1988 on 2007-09-02
I found a workaround, that solves a lot of known problems with graphics chips from SIS (maybe some other ones, too).
I have a SiS630 chipset in my notebook and I experienced major issues when playing flash videos or starting any DirectX applications with Wine.
The trick is easy, you just have to disable DRI in the xorg.conf file. This way, you won't have 3D acceleration, but flash videos will play flawlessly, and you'll be able to use DirectX apps with Wine.
I emphasize, this isn't a fix, just a workaround, but I found it very useful.

1. Open xorg.conf with a text editor:

```
sudo vi /etc/X11/xorg.conf
```

2. Look for a line that reads Load "DRI" and put a hash mark in front of it, so the "Module" section will look like this:

```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection
```

3. Next, find the Device section for your graphics adapter and add an option, that disables DRI (this is needed to completely disable direct rendering):

```
Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
        Option "DRI" "off"
EndSection
```

4. Save the file and exit from the editor.

5. Restart the X server by pressing the Ctrl+Alt+Backspace keys together.

Once X is started up, try to play some flash vids or start some DirectX apps with Wine to see, whether this workaround helped you or not.

---

