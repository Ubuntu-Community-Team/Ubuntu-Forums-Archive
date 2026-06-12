---
title: "i915gm hardware acceleration"
date: 2005-12-17
forum: Multimedia &amp; Video
---

### Post by CitizenKane on 2005-12-17
I seem to be having some problems with the i915gm chipset hardware acceleration in ubuntu breezy and I have no idea what is causing it.  Warcraft 3's (under Cedega 5) main window runs less than a frame per second and Scorched 3D just dies after a little while.  Otherwise, the computer has performed without problems.  I wish I had more info but I haven't tried it under other versions/distros.  My only lead is this thread [http://ubuntuforums.org/showthread.php?t=93416&highlight=915](http://ubuntuforums.org/showthread.php?t=93416&highlight=915).

I have attatched:
[LIST]
[*]dmesg
[*]glxinfo
[*]xorg.conf
[/LIST]
in the form of text files.  If any one needs any other information I will do what I can.  If I can get any help i would appreciate it greatly.

---

### Post by kairu0 on 2005-12-18
Yikes! One frame per second!

Anyway, your post reminded me that I didn't have stellar 3d performance on my card (915gm). Planetpenguin-racer was unplayable.

After a little xorg.conf tweaking, I now get fair planetpenguin-racer performance (about 29fps on the best graphics settings at 1280x800). All I did was add:

```

Load     "drm"

```

to my xorg.conf in the module section. I noticed that you don't have it in yours. Please add it. If I'm not mistaken, it is the module that bridges the dri driver with your video card's memory.

P.S. You'll have to kill X (or just reboot) for it to take effect.

---

### Post by anil_robo on 2005-12-18
I have intel i915GM too, and can't get hardware acceleration on wine. I want to play Diablo on Ubuntu so that I can get rid of windows for ever. I am attaching my system output as text files. Isn't there something like "autoconfigurator" for graphics hardware in Ubuntu?
[ATTACH]4629[/ATTACH] [ATTACH]4630[/ATTACH] [ATTACH]4631[/ATTACH]

---

### Post by CitizenKane on 2005-12-18
I added
```

Load "drm"

```
to the module section in my xorg.conf.  As far as I can tell this made no difference at all.  For reference, here is my modified module section.

```

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load    "drm"
EndSection

```

If anyone else has any more ideas that would be awesome!

---

### Post by kairu0 on 2005-12-18
I'm attaching my xorg.conf. Remember, I use the same chipset as you and only the Breezy video driver. Your problem is probably somewhere in the modules or the modelines.

By the way, I ran scorched3d and got 60fps.

---

### Post by CitizenKane on 2005-12-18
I have kind of run up agaisnt a wall.  I enabled loading of all the modules that you had kairu0.  Otherwise, my xorg.conf is pretty much the same as yours.  The only thing that differs is the modeline in the monitor section which I have no idea how to configure or if it is even important.  Nonetheless, thanks for the help.

---

### Post by kairu0 on 2005-12-19
When you run glxgears, do the gears roll smoothly or jerkedly?

---

### Post by anil_robo on 2005-12-19
[quote=kairu0]When you run glxgears, do the gears roll smoothly or jerkedly?[/quote]
When I run glxgears, they run smoothly except a seemingly unnoticeable jerk every 4 seconds. :confused:

---

### Post by kairu0 on 2005-12-19
[QUOTE=anil_robo]When I run glxgears, they run smoothly except a seemingly unnoticeable jerk every 4 seconds. :confused:[/QUOTE]

Type this in a console:

```
cat /var/log/Xorg.0.log|grep dri
```

Do the words "failed" or "version xxxx is needed" appear?

For the record, I think my glxgears was jerking every 4 seconds or so when I ran Hoary and dri wasn't working.

---

### Post by anil_robo on 2005-12-21
[quote=kairu0]Type this in a console:

```
cat /var/log/Xorg.0.log|grep dri
``` 
Do the words "failed" or "version xxxx is needed" appear?

For the record, I think my glxgears was jerking every 4 seconds or so when I ran Hoary and dri wasn't working.[/quote]

the above command results in the following output (no errors):
```

akumar@akumar:~$ cat /var/log/Xorg.0.log|grep dri
        X.Org XInput driver : 0.4
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
        ABI class: X.Org XInput driver, version 0.4
        ABI class: X.Org XInput driver, version 0.4
        ABI class: XFree86 XInput driver, version 0.3
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [dri] visual configs initialized
(II) Synaptics touchpad driver version 0.13.6
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [dri] visual configs initialized
akumar@akumar:~$

```
Also, I booted through the LiveCD and copied its xorg.conf file to the hard drive. Now glxgears run abxolutely smooth! Maybe I messed up with xorg.conf after following some how-to's mentioned in these forums! :D

---

