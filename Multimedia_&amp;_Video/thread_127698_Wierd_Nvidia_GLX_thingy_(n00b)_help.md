---
title: "Wierd Nvidia GLX thingy (n00b) help"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by Andreas T on 2006-02-09
Hello, first post here :)
Really like Ubuntu but I have a problem. 
Ran the great "automatix" relieved that I finally got the Nvidia driver installed.. Or did I? It now says Nvidia Geforce 6800GT, which is the right one.. 
I'm not able to run 3D apps...

Tried to find the answer here without any progress. 

this is my way through the jungle =)   :


```
$ sudo nvidia-glx-config enable

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
```


hmm so I tried /etc/X11/xorg.conf to change, have accessed this before

```
this is what I got this time:
~$ /etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Åtkomst nekas (access denied)
```

hmmm what now? No permission??

Tried

```
~$ sudo apt-get install nvidia-glx
Läser paketlistor... Finished
Bygger beroendeträd... Färdig
nvidia-glx är redan den senaste versionen. (already latest version)
0 upgraded 0 new installations 0 to remove och 5 not upgraded
```

ok no progress here..

lets throw in something else that I found in the forums:

```

~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```


soo, like I said; I'm a complete n00b so I don't know what to do or if the things I wrote above were relevant but you may get some info from it.

I hope someone will help me :) It's quite annoying not to be able to run 3D apps.

edit: ah.. stupid.. accessed the xorg.conf, ehat did I think of before?? anyways:

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

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true" 
EndSection

whats wrong??




HAPPY EDIT:
Fixed it! Changed "nv" to "nvidia" great!

Live long and prosper

---

### Post by LordBug on 2006-02-10
Even though you solved it (good for you!), I'd suggest reading a bit more on the nVidia drivers and what modules should and should not be loading.  I know at least one of those you listed should be removed (though I can never remember which one(s)).

---

### Post by Andreas T on 2006-02-10
Hmm okay, thanks for the advice.

---

### Post by Bretls on 2006-02-14
It's the DRI module. 
```
Section "Module"

    Load	   "GLcore"

    Load           "i2c"

    Load           "bitmap"

    Load           "ddc"

    Load           "extmod"

    Load           "freetype"

    Load           "glx"

    Load           "int10"

    Load           "type1"

    Load           "vbe"

EndSection


```

---

