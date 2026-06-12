---
title: "GeForce 3 + Repo drivers = No GLX?"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by GIBson3 on 2006-06-18
Ok so this system is nearly identicle to the one I run at work.  the major difference between this and work (minus about 400MHz) is that this system was a fresh install of 6.06, where as work was 5.10 upgraded to 6.06. as of now (I'v tried both NVidis-glx and NVidia-glx-legacy) when trying for 3d accel I get an error.  I then tried "glxinfo" and this is what I get...

```

sean@Gibian:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```



[SIZE="5"][COLOR="DarkOrange"][System info][/COLOR][/SIZE]

```

sean@Gibian:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 1
cpu MHz         : 602.349
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1205.91

sean@Gibian:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
GCC version:  gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
sean@Gibian:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Not Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000007:0x00000000
sean@Gibian:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     PCI device 1106:0691
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000207:0x00000000
sean@Gibian:~$



```

---

### Post by tseliot on 2006-06-18
[QUOTE=GIBson3]Ok so this system is nearly identicle to the one I run at work.  the major difference between this and work (minus about 400MHz) is that this system was a fresh install of 6.06, where as work was 5.10 upgraded to 6.06. as of now (I'v tried both NVidis-glx and NVidia-glx-legacy) when trying for 3d accel I get an error.  I then tried "glxinfo" and this is what I get...

```

sean@Gibian:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```



[SIZE="5"][COLOR="DarkOrange"][System info][/COLOR][/SIZE]

```

sean@Gibian:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 1
cpu MHz         : 602.349
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1205.91

sean@Gibian:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
GCC version:  gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
sean@Gibian:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Not Supported
SBA:             Not Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000007:0x00000000
sean@Gibian:~$ cat /proc/driver/nvidia/agp/host-bridge
Host Bridge:     PCI device 1106:0691
Fast Writes:     Not Supported
SBA:             Supported
AGP Rates:       4x 2x 1x
Registers:       0x1f000207:0x00000000
sean@Gibian:~$



```[/QUOTE]
Can you post the model of your graphic card?

---

### Post by GIBson3 on 2006-06-18
[QUOTE=tseliot]Can you post the model of your graphic card?[/QUOTE]

oops didn't coppy high enough up >.<

```
sean@Gibian:/proc/driver/nvidia/cards$ cat 0
Model:           GeForce3
IRQ:             11
Video BIOS:      ??.??.??.??.??
Card Type:       AGP
sean@Gibian:/proc/driver/nvidia/cards$

```

it's just the vanilla 3, not a ti500/ti200   (64mb)

---

### Post by GIBson3 on 2006-06-19
here is the actual card [[Elsa Gladiac 920]("http://www.elsa.com/EN/Products/detail.asp?newsid=221")]. as a quick note mine is the non-tv out version.

---

### Post by tseliot on 2006-06-20
You should not use driver 7174.

Please try my guide or my script and get driver 8762:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by GIBson3 on 2006-06-20
[QUOTE=tseliot]You should not use driver 7174.

Please try my guide or my script and get driver 8762:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")[/QUOTE]

Hehe I've used the 8762 with the same results, I'm currently on my system at work and Have tried much the same, and with much better results (both the 7174 and the 8*'s (both the repo's and the current .run) have worked successfully.

At this point I'm wondering if it has to do with the Via Chipset in my home box.

```

sean@edge:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 10
cpu MHz         : 996.844
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1995.21

sean@edge:~$ cat /proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
GCC version:  gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
sean@edge:~$ cat /proc/driver/nvidia/cards/0
Model:           GeForce3
IRQ:             11
Video BIOS:      03.20.00.10.00
Card Type:       AGP
DMA Size:        32 bits
DMA Mask:        0xffffffff
sean@edge:~$

```

Note that the Card actually has all the info on this box, verses next to none on my home system.  ](*,) 

When the home box was running Debian the 8762 drivers from the nv website worked like a champ...  hence my confusion

---

### Post by tseliot on 2006-06-20
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by GIBson3 on 2006-06-20
[QUOTE=tseliot]Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )[/QUOTE]


mmm Xserver logging, I haven't done that since slackware 3.6 :D  when I get home tonight I'll bring it all up

I've also sent myself the xorg.conf from this system just to see if maybe a setting got foo.bar'd

---

### Post by GIBson3 on 2006-06-21
well it is working beautifully now.

I switched it back to "nv" booted up, went to tty1, and shut down gdm, I did a sudo vi /etc/X11/xorg.conf  and switched the "nv" back to "nvidia" started with verbose an logverbose, and it booted X with no errors. I rebooted the system, and it continued to work, I was successful in playing quake 3 and enemy territory.

Thank you for all your help :D

---

