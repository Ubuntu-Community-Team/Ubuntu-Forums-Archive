---
title: "No direct rendering after upgrading to fglrx 8.33.6"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by heruan on 2007-02-15
After upgrading linux-restricted-modules to 2.6.20-6 and xorg-driver-fglrx to 8.33.6 on feisty, I cannot get direct rendering to work.

/var/log/Xorg.0.log:
```

...
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 128 MB
(EE) fglrx(0): [pcie] Failed to gather memory of size 131072Kb for PCIe. Error (-1000)
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(EE) fglrx(0): GART is not initialized, disabling DRI
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
...

```

---

### Post by Telarmago on 2007-02-17
I have the exact same problem. I'm thinking about reformatting and installing the older drivers from the Ubuntu apt-get repositories...

---

### Post by dmatrix on 2007-02-19
Exact same problem on a clean install of herd4.

damn these ati drivers, why did my nvidia card have to die, :(

---

### Post by ograndedienne on 2007-03-25
Just for the record, which CPU do you have?
i've the same probem, with HP nc6400 laptop with Radeon X1300 and Core 2 Duo .

i was trying disabling agpgart module (so fglrx use its own), but i can't because it's used.. :/

Other ideas?

Does it work DRI with previous packaged driver version?

O(n)

---

### Post by ograndedienne on 2007-03-25
Just for the record, which CPU do you have?
i've the same probem, with HP nc6400 laptop with Radeon X1300 and Core 2 Duo .

i was trying disabling agpgart module (so fglrx use its own), but i can't because it's used.. :/

Other ideas?

Does it work DRI with previous packaged driver version?

O(n)

---

### Post by spaceghoti on 2007-03-26
I found that the upgrade of fglrx creating a duplication error.  I found the solution here:  [http://www.thinkwiki.org/wiki/Problems_with_fglrx#Known_Troubles_and_Solutions](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Known_Troubles_and_Solutions)

I hope this helps people.

---

### Post by ograndedienne on 2007-03-26
i resolved simply installing ubuntu packaged version of fglrx. it's version 8.38.8 .

Thanks anyway.


i don't know why last version has "Unable to gather memory" error; i guess it's a problem of PCIe and fglrx mixed driver...but i don't know :p :confused: 

Valerio aka O(n)

---

### Post by quick_dudley on 2007-03-26
I'm getting the same problem (will check the log to see if it's exactly the same) already using the ubuntu packaged version of fglrx.

---

### Post by ograndedienne on 2007-03-27
Have you set overlay type to Xv ?
Add this options in Device section

```

Option "VideoOverlay" "on"
Option "OpenGLOverlay" "on"

```

Valerio aka O(n)

---

### Post by quick_dudley on 2007-03-27
I had set overlay type to Xv, and in xorg.conf the xv overlay was on but opengl overlay was off. Have now fixed that.
However: glxinfo still says directrender is off and opengl vendor is mesa3d. The Xv stuff all uses my hardware acceleration.
This is all quite mystifying since I actually had direct rendering working a while ago until I changed my user password. Reinstalling my o/s and fglrx (using the exact same terminal commands as the first time) doesn't seem to have done anything.

---

### Post by quick_dudley on 2007-04-01
Here's the solution that actually worked:

add to the end of /etc/X11/xorg.conf
```

Section "Extensions"
        Option    "Composite"     "false"
EndSection


```
now works fine

---

