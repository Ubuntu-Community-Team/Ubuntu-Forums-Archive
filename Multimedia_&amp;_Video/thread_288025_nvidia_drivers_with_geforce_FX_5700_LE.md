---
title: "nvidia drivers with geforce FX 5700 LE"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by Klaynos on 2006-10-29
I just installed edgy onto a machine with a geforce FX 5700 LE, and installed the nvidia-glx drivers, on enabling them and restarting X it crashed out saying "no device found", I did a diff of files (show below).  As you can see the BusID had changed, so I switched this back and all seems to be working now, does anyone know why this would be?

```

<       Option          "XkbLayout"     "gb"
---
>       Option          "XkbLayout"     "us"
94,96c94,96
<       Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
<       Driver          "nv"
<       BusID           "PCI:1:0:0"
---
>       Identifier      "Generic Video Card"
>       Driver          "nvidia"
>       BusID           "PCI:0:5:0"
108c108
<       Device          "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
---
>       Device          "Generic Video Card"

```

---

### Post by gabrieliscool on 2006-10-29
> **Klaynos said:**
> I just installed edgy onto a machine with a geforce FX 5700 LE, and installed the nvidia-glx drivers, on enabling them and restarting X it crashed out saying "no device found", I did a diff of files (show below).  As you can see the BusID had changed, so I switched this back and all seems to be working now, does anyone know why this would be?

```

<       Option          "XkbLayout"     "gb"
---
>       Option          "XkbLayout"     "us"
94,96c94,96
<       Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
<       Driver          "nv"
<       BusID           "PCI:1:0:0"
---
>       Identifier      "Generic Video Card"
>       Driver          "nvidia"
>       BusID           "PCI:0:5:0"
108c108
<       Device          "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
---
>       Device          "Generic Video Card"

```

so you have two nvidia video cards?

---

### Post by tseliot on 2006-10-29
try this:
```
sudo nvidia-xconfig --no-composite
```

and restart the Xserver

---

### Post by Klaynos on 2006-10-29
> **gabrieliscool said:**
> so you have two nvidia video cards?

No sorry, that's the diff of my xorg.conf files before and after.

---

### Post by raskolnik on 2006-10-29
The same thing happens to me, when I run nvidia-xconfig. I found the problem was the autoconfiguration set the busid incorrectly. Try changing the line...

BusID           "PCI:0:5:0"

to...

BusID           "PCI:1:0:0"

This solved my problem. Hope that helps.

---

### Post by tseliot on 2006-10-30
> **raskolnik said:**
> The same thing happens to me, when I run nvidia-xconfig. I found the problem was the autoconfiguration set the busid incorrectly. Try changing the line...

BusID           "PCI:0:5:0"

to...

BusID           "PCI:1:0:0"

This solved my problem. Hope that helps.
and to find out which BUSID you should put:
```
lspci | grep VGA
```

---

### Post by GnudeNoob on 2006-10-30
> **raskolnik said:**
> The same thing happens to me, when I run nvidia-xconfig. I found the problem was the autoconfiguration set the busid incorrectly. Try changing the line...

BusID           "PCI:0:5:0"

to...

BusID           "PCI:1:0:0"

This solved my problem. Hope that helps.

I had exactly the same problem with a clean install of Edgy Eft on a system with a GeForce 6600, and eventually I worked out exactly the same solution...after going back and forwards from Windows to Ubuntu a few times and wading through heaps of Linux obscurity to work out exactly what was happening...sigh, its only taken me three days to install Ubuntu...hehehehe.

I haven't tried any of tseliot's suggestions as I don't understand them...too brief, no explanation...but most gurus end up needing an interpreter as they forget what its like to be a noob.

---

