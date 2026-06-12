---
title: "mplayer cant play fullscreen with ati"
date: 2008-08-19
forum: Multimedia Software
---

### Post by aisar190 on 2008-08-19
hello everypne....:)
i used ati hd3850 gfx....very hard fot me to installed the driver....but i manage tp installed it...but mplayer wont go to fullscreen...if i change the setting to open gl...it can be play in fullscreen but lots of flickering.....if i used x11...it will stay at normaal size even if i already change it to fullscreen....please someone....can you help me ?....im out of solution here.....

regards,
aisar

---

### Post by VSh on 2008-08-19
Scaling for x11 driver in mplayer will work if you use the options -fs -zoom from command line. But you don't have hw acceleration in this case.

Do you use fglrx? For hw acceleration try to add

```
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "on"
```

to xorg.conf in your video device section.

---

### Post by aisar190 on 2008-08-19
> **VSh said:**
> Scaling for x11 driver in mplayer will work if you use the options -fs -zoom from command line. But you don't have hw acceleration in this case.

Do you use fglrx? For hw acceleration try to add

```
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "on"
```

to xorg.conf in your video device section.

how do i enter and do this ?...im quite new to ubuntu...can you please explain

---

### Post by aisar190 on 2008-08-19
> **VSh said:**
> Scaling for x11 driver in mplayer will work if you use the options -fs -zoom from command line. But you don't have hw acceleration in this case.

Do you use fglrx? For hw acceleration try to add

```
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "on"
```

to xorg.conf in your video device section.

after i've done this...and initialise it...i found out the xorg.conf is change to

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:1:0:0"
EndSection

what happen to the ? 

Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "on"

---

### Post by aisar190 on 2008-08-19
is there anyone that have any idea on this problem.....i have no solution at all...the video stilll wont go to fullscreen....please someone...

---

### Post by shirilover on 2008-08-20
You'll need to use sudo to edit that file, i.e. 
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by VSh on 2008-08-20
The procedure is (everything in the terminal):

1) Make backup of your working xorg.conf:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.orig
```

2) Change xorg.conf:
```
sudo nano xorg.conf
```
Add
```
Option "XAANoOffscreenPixmaps" "on"
Option "VideoOverlay" "off"
Option "OpenGLOverlay" "off"
Option "TexturedVideo" "on"
Option "Textured2D" "on"
Option "TexturedXrender" "off"
Option "UseFastTLS" "1"
Option "BackingStore" "on"
```
under Section "Device".

3) Update ati's "shadow" config:
```
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```

4) Restart and pray.

If something goes wrong, X can't start, etc, restore xorg.conf from your backup:
```
cd /etc/X11
sudo cp xorg.conf.orig xorg.conf
sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
```
and try to add options one by one.

NOTE: fglrx's video overlay conflicts with Composite, so the video will be flickering terribly windowed, but will be OK in full screen.

---

