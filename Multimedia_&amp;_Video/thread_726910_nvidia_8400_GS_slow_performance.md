---
title: "nvidia 8400 GS slow performance"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by jcarlosn on 2008-03-17
Hi, I have installed ubuntu 7.10 (amd64, is a 64bit processor) in my new computer, is the first operating system installed on this pc.

Everything works fine, but the graphic card is not working correctly, when playing teewars and similar games that runs fine with my nvidia 6400 at the same resolution, i get very low fps, and the game becomes unplayable.

I have the nvidia driver installed from the restricted driver manager.

I have no composite enabled. (no compiz, no beryl etc)

¿What can be wrong?

Some information about the system:

joca@thanatos:~$ dmesg | grep agp
[   19.317393] agpgart: Detected AGP bridge 0
[   19.317396] agpgart: Aperture pointing to RAM
[   19.317458] agpgart: Aperture from AGP @ c0000000 size 256 MB
[   19.324342] agpgart: AGP aperture is 256M @ 0xc0000000
[   19.854226] Linux agpgart interface v0.102 (c) Dave Jones
joca@thanatos:~$ lspci | grep -i nvidia
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
joca@thanatos:~$ lsmod | grep -i agp
via_agp                13056  0 
joca@thanatos:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
[....]
joca@thanatos:~$ xrandr
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0*    51.0     52.0  
[...]

The section device, screen and monitor from my xorg.conf:

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8400 GS]"
        Driver          "nvidia"
        Busid           "PCI:2:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8400 GS]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

And the cpu information:

joca@thanatos:~$ cat /proc/cpuinfo | grep model
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 6400+
model           : 67
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 6400+

memory in the system:

joca@thanatos:~$ free
             total       used       free     shared    buffers     cached
Mem:       4051460    1286516    2764944          0      33292     704992
-/+ buffers/cache:     548232    3503228
Swap:            0          0          0


And the results of glxgears:

15891 frames in 5.0 seconds = 3178.162 FPS
16117 frames in 5.0 seconds = 3223.253 FPS
16208 frames in 5.0 seconds = 3241.436 FPS
15767 frames in 5.0 seconds = 3153.385 FPS

Thanks in advance.

---

### Post by Ub1476 on 2008-03-17
The 8* cards from nvidia were rather new when Ubuntu 7.10 was released, so the driver you are using is almost 6 months old.. I suggest you uninstall it through RDM, then download [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), which will install and configure the latest driver from nvidia for you. 

In most cases, Envy can be used in a GUI

```
envy -g #graphical installer
```

but should the need arise...

```
envy -t #text-mode installer
```

---

### Post by jcarlosn on 2008-03-17
Thanks you very much.

The glxgears fps is the same, using the new driver installed with envy (thanks to Alberto Milone for this amazing application) but the games works fine now.

---

### Post by jcarlosn on 2008-03-17
Thanks for the help, but my final question is: it is normal to get only 3000 (+ - 100) fps in glxgears using a 8400 gs card?

---

### Post by luopio on 2008-05-07
I get around 3100, so it's the same. Running 8.04 here. I was wondering about the jerkyness in compiz that happens when effects are run after a while of innactivity (seems like the card goes into a powersaving mode or something)

---

