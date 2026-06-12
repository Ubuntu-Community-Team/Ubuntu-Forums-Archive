---
title: "Can't get nvidia drivers to work on dapper (using k7's kernel)"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by dangerous666 on 2006-06-04
I've just installed kubuntu dapper and, as usual, installed k7's kernel, uninstalled the 386 one, installed the k7's kernel headers... procedures i've done since warty. So i tried to install the latest nvidia driver (i've also tried older versions), and the installation occurs normally... The installer says that it was successfully installed, got the xorg.conf file modified by nvidia's installer, and when I think that everything's all right, tried to reload the X server and just got the kubuntu bootspash screen... no nvidia's logo at all... Trying a startx command give some error messages, like "glx not loaded", "nvidia not loaded"... I "modprobed" nvidia module, with no errors... but the driver isn't loaded... Running lsmod I can see the nvidia module as loaded..

I have also tried a tutorial found in wiki... which procedure was to decompress the driver and install it specifying some paths... Got the same...

Could anybady help-me please?

---

### Post by finally on 2006-06-05
I had very similar problems (if not exactly the same).
Fixed it by creating the following symlinks:

```

sudo ln -s /usr/X11R6/lib/modules/drivers/nvidia_drv.o usr/lib/xorg/modules/drivers/nvidia_drv.o
sudo ln -s /usr/X11R6/lib/modules/drivers/nvidia_drv.so /usr/lib/xorg/modules/drivers/nvidia_drv.so
sudo ln -s /usr/X11R6/lib/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so

```

---

### Post by tseliot on 2006-06-05
1) Can you post the model of your graphic card?
2) a quick fix:
Boot in Recovery mode

then type:
```
sudo nano -w /etc/X11/xorg.conf
```

and set the driver to "nv" in the Section Device of the file.

CTRL+X to exit (save the file)

then type:
```
reboot
```

---

### Post by nouse66 on 2006-06-05
[QUOTE=finally]I had very similar problems (if not exactly the same).
Fixed it by creating the following symlinks:

```

sudo ln -s /usr/X11R6/lib/modules/drivers/nvidia_drv.o usr/lib/xorg/modules/drivers/nvidia_drv.o
sudo ln -s /usr/X11R6/lib/modules/drivers/nvidia_drv.so /usr/lib/xorg/modules/drivers/nvidia_drv.so
sudo ln -s /usr/X11R6/lib/modules/extensions/libglx.so /usr/lib/xorg/modules/extensions/libglx.so

```[/QUOTE]

thanks, that fixed it for me

---

