---
title: "Nivida driver..one issue"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by GQed76 on 2006-12-21
Everytime i reboot, i have to go to applications, systerm tools, NVIDIA X Server settings and choose the correct resolution 1680X1050.

Any ideas why

---

### Post by Cene on 2006-12-22
Problem seems to be in your xorg.conf.

First, let's back up our xorg.conf (the cool way :cool:):
```
sudo cat /etc/X11/xorg.conf > /etc/X11/xorg.conf.backup
```

Then, open your xorg.conf
In GNOME:
```
gksudo gedit /etc/X11/xorg.conf
```
In KDE:
```
kdesu kate /etc/X11/xorg.conf
```
Or text-based:
```
sudo nano /etc/X11/xorg.conf
```

Then look up for the section what defines the resolutions you use. It should look like this (the numbers may vary, I copied this one from my xorg.conf):
```

        SubSection "Display"
                Depth           24
                Modes           "2560x1024" "1024x768" "800x600" "1280x480"
        EndSubSection

```

Set the resolution you want to use to "Modes" line before any other resolution.

After it, save the file, shutdown all your open programs and restart X (ctrl + alt + backspace).

If you screw up something and the screen won't show up correctly, press ctrl + alt + F1 and do the following:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

and you should be fine.
Hope this helps. :)

---

### Post by tseliot on 2006-12-22
You can do that or simply launch nvidia-settings with sudo:
```
sudo nvidia-settings
```

In this way your settings will be changed permanently

---

