---
title: "Cannot get High Screen resolution"
date: 2011-07-31
forum: Multimedia Software
---

### Post by arun.manuel14 on 2011-07-31
Hey , I know this is probably a stupid question , but I started using Ubuntu 11.04 . My screen resolution on windows was 1600x900
But on ubuntu (even after installing proprietary drivers) the highest I can get is 1024x768 . 
I tried using xandr but couldn't work it out . My xandr info

 "

Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0

 "

When i tried adding a new mode using the command
" xrandr --addmode VGA 1600×900 "

I got the following error

" 
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA"

"

Now I'm not sure what VGA refers to , but Im using a vga port to connect my monitor
Also I'm using only one monitor.

It would be really great if someone could help me out. 

Thanks. :)

---

### Post by realzippy on 2011-07-31
[I]Screen 0: minimum 320 x 240, current 1024 x 768, [COLOR="Red"]maximum 1024 x 768[/COLOR]
**default** connected 1024x768+0+0 [/I]


You had to type "default" instead of VGA or something.
But this won't work,because of *maximum 1024 x 768*.
Which driver do you use?

---

### Post by CatKiller on 2011-07-31
> **arun.manuel14 said:**
> Also I'm using only one monitor.

It might help if you said what that monitor was...

---

### Post by arun.manuel14 on 2011-07-31
Samsung 20" wide screen model number 2033

I dont have an additional gpu , I use the one on the motherboard which Nvidia Geforce 7025/nforce 630a

---

### Post by realzippy on 2011-07-31
Search for the correct HorizSync and VertRefresh   
values for your monitor model (internet/manual) and edit the file *xorg.conf* with those values (in the "Monitor" section).
To edit run:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by realzippy on 2011-07-31
Try:

Horizontal 30-81 
Vertical   56-75

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Try:

Horizontal 30-81 
Vertical   56-75

I edited xorg with those values under monitor. Now what am i supposed to do?!

---

### Post by realzippy on 2011-07-31
HorizSync       30.0 - 81.0
VertRefresh     56.0 - 75.0


then reboot or restart X server.
New resolutions will be available then.

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> HorizSync       30.0 - 81.0
VertRefresh     56.0 - 75.0


then reboot or restart X server.
New resolutions will be available then.

Hey! It worked! I got higher resolutions , but there was no option for 1600x900 , how do i add that?

---

### Post by realzippy on 2011-07-31
Do you use nvidia-settings for your resolution?

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Do you use nvidia-settings for your resolution?

Yes , I went to sysetem setting > Nvidia xserver setting

After the adjustments that you asked me to make , i got much higher resolutions than what my montior can handle . But no exact 1600x900

Right now im running 1440x900

---

### Post by realzippy on 2011-07-31
That 's odd.
What does xrandr say?

**Edit:**
*After the adjustments that you asked me to make , i got much higher resolutions than what my montior can handle*

..this is not good.I got the values from your monitor's manual,also those are very common for 20" panels.
Can you post your xorg.conf file ?

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> That 's odd.
What does xrandr say?

This is what xrandr says 

"

 xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1920 x 1080
default connected 1440x900+0+0 0mm x 0mm
   1024x768       50.0     51.0     52.0     90.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   680x384        67.0     68.0  
   640x512        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0  
   576x432        75.0     76.0     77.0     78.0  
   512x384        79.0     80.0     81.0  
   416x312        82.0  
   400x300        83.0     84.0     85.0     86.0  
   320x240        87.0     88.0     89.0  
   1440x900       90.0     91.0* 
   1920x1080      50.0  
   1600x1024      90.0 

"

---

### Post by realzippy on 2011-07-31
Run

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

```
xrandr --addmode default "1600x900_60.00"
```

```
xrandr -s 1600x900_60
```

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Run

```
xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```


I couldn't run that ! When I tried it said

"

 Failed to get size of gamma for output default

 "

---

### Post by realzippy on 2011-07-31
..can you please paste what your terminal shows?
Means,the command and the "answer"...


Edit:

..and use code tags when posting terminal content please...

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> ..can you please paste what your terminal shows?
Means,the command and the "answer"...
"


arun@ubuntu:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
arun@ubuntu:~$ 

"


an image , if it helps

[IMG]http://i52.tinypic.com/1zxsl1v.png[/IMG]

---

### Post by realzippy on 2011-07-31
That 's ok. Ignore the "gamma" error and go on with the 2 other commands:

```
xrandr --addmode default "1600x900_60.00"
```

```
xrandr -s 1600x900_60
```

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> That 's ok. Ignore the "gamma" error and go on with the 2 other commands:

```
xrandr --addmode default "1600x900_60.00"
```

```
xrandr -s 1600x900_60
```


Still nothing! :(

arun@ubuntu:~$ xrandr --newmode "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  154 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19
[B]arun@ubuntu:~$ xrandr --addmode default "1600x900_60.00"
xrandr: Failed to get size of gamma for output default
arun@ubuntu:~$ xrandr -s 1600x900_60
Failed to change the screen configuration!
arun@ubuntu:~$[/B]

---

### Post by realzippy on 2011-07-31
Please show again
 ```
xrandr -q
```

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Please show again
 ```
xrandr -q
```

arun@ubuntu:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1024x768       50.0     51.0     52.0     90.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   680x384        67.0     68.0  
   640x512        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0  
   576x432        75.0     76.0     77.0     78.0  
   512x384        79.0     80.0     81.0  
   416x312        82.0  
   400x300        83.0     84.0     85.0     86.0  
   320x240        87.0     88.0     89.0  
   1440x900       90.0* 
arun@ubuntu:~$



[IMG]http://i53.tinypic.com/1gt4yg.png[/IMG]

---

### Post by CatKiller on 2011-07-31
> **realzippy said:**
> ..and use code tags when posting terminal content please...
++

---

### Post by arun.manuel14 on 2011-07-31
> **CatKiller said:**
> ++

Sorry about that , Im new here . I'll make sure to do that next time!

---

### Post by realzippy on 2011-07-31
Please stop those screenshots,it is a waste of space.
I already edited post #16,please have a look.

I noticed that the screen maximum xrandr reports decreased
to 1440x900 from 1920x1080 in post #13 ...so
1600x900 isn't possible.
Go to nvidia-settings,choose a lower resolution (the one from the "beginning"),reboot.
Then again run *xrandr -q*...and do not log out or reboot then.

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Please stop those screenshots,it is a waste of space.
I already edited post #16,please have a look.

I noticed that the screen maximum xrandr reports decreased
to 1440x900 from 1920x1080 in post #13 ...so
1600x900 isn't possible.
Go to nvidia-settings,choose a lower resolution (the one from the "beginning"),reboot.
Then again run *xrandr -q*...and do not log out or reboot then.


I did that (went back to 1024x768 saved it and reboot)
xrandr report 

```
arun@ubuntu:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1440 x 900
default connected 1024x768+0+0 0mm x 0mm
   1440x900       50.0  
   1024x768       51.0     58.0     59.0     97.0* 
   1360x768       52.0     53.0  
   1152x864       54.0     55.0     56.0     57.0  
   960x600        60.0  
   960x540        61.0  
   840x525        62.0     63.0     64.0  
   832x624        65.0  
   800x600        66.0     67.0     68.0     69.0     70.0     71.0  
   800x512        72.0  
   720x450        73.0  
   680x384        74.0     75.0  
   640x512        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0  
   576x432        82.0     83.0     84.0     85.0  
   512x384        86.0     87.0     88.0  
   416x312        89.0  
   400x300        90.0     91.0     92.0     93.0  
   320x240        94.0     95.0     96.0  
arun@ubuntu:~$ 

```

But when I go to nvidia settings it still has the 1920x1200 option!

---

### Post by CatKiller on 2011-07-31
Also. the contents of /var/log/Xorg.0.log might say why the mode you want isn't being made available.

---

### Post by arun.manuel14 on 2011-07-31
> **CatKiller said:**
> Also. the contents of /var/log/Xorg.0.log might say why the mode you want isn't being made available.

There's a lot of stuff in there , I cant find it , would you like me to post it?

Also before @realzippy started helping me out , i googled and messed around with my xorg.conf , could that be the reason?

---

### Post by realzippy on 2011-07-31
Yes,you can post the Xorg.0.log ...
Guess the driver cannot read monitor's EDID   (as usual  ;-) )
Run

```
sudo nvidia-bug-report.sh
```

then attach the created file (it is created in your home folder).
It contains the X log files and your xorg.conf and other stuff...

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Yes,you can post the Xorg.0.log ...
Guess the driver cannot read monitor's EDID   (as usual  ;-) )
Run

```
sudo nvidia-bug-report.sh
```

then attach the created file (it is created in your home folder).



This is my Xorg.0.log

```
[    12.088] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    12.088] X Protocol Version 11, Revision 0
[    12.088] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    12.088] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    12.088] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=1EFC69DDFC69AFA7 loop=/ubuntu/disks/root.disk ro quiet splash
[    12.088] Build Date: 19 April 2011  03:40:45PM
[    12.088] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    12.088] Current version of pixman: 0.20.2
[    12.088] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.088] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.088] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  1 00:17:48 2011
[    12.088] (==) Using config file: "/etc/X11/xorg.conf"
[    12.088] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.093] (==) ServerLayout "Layout0"
[    12.093] (**) |-->Screen "Screen0" (0)
[    12.093] (**) |   |-->Monitor "Monitor0"
[    12.093] (**) |   |-->Device "Device0"
[    12.093] (**) |-->Input Device "Keyboard0"
[    12.093] (**) |-->Input Device "Mouse0"
[    12.093] (**) Option "Xinerama" "0"
[    12.093] (==) Automatically adding devices
[    12.093] (==) Automatically enabling devices
[    12.093] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.093] 	Entry deleted from font path.
[    12.093] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.093] 	Entry deleted from font path.
[    12.093] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.093] 	Entry deleted from font path.
[    12.093] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.093] 	Entry deleted from font path.
[    12.093] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.093] 	Entry deleted from font path.
[    12.093] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.093] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.093] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    12.093] (WW) Disabling Keyboard0
[    12.093] (WW) Disabling Mouse0
[    12.093] (II) Loader magic: 0x7e0280
[    12.093] (II) Module ABI versions:
[    12.093] 	X.Org ANSI C Emulation: 0.4
[    12.093] 	X.Org Video Driver: 10.0
[    12.093] 	X.Org XInput driver : 12.3
[    12.093] 	X.Org Server Extension : 5.0
[    12.094] (--) PCI:*(0:0:13:0) 10de:03d6:1043:83a4 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
[    12.094] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.094] (II) LoadModule: "extmod"
[    12.120] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.120] (II) Module extmod: vendor="X.Org Foundation"
[    12.120] 	compiled for 1.10.1, module version = 1.0.0
[    12.120] 	Module class: X.Org Server Extension
[    12.120] 	ABI class: X.Org Server Extension, version 5.0
[    12.120] (II) Loading extension MIT-SCREEN-SAVER
[    12.120] (II) Loading extension XFree86-VidModeExtension
[    12.120] (II) Loading extension XFree86-DGA
[    12.120] (II) Loading extension DPMS
[    12.120] (II) Loading extension XVideo
[    12.120] (II) Loading extension XVideo-MotionCompensation
[    12.120] (II) Loading extension X-Resource
[    12.120] (II) LoadModule: "dbe"
[    12.121] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.121] (II) Module dbe: vendor="X.Org Foundation"
[    12.121] 	compiled for 1.10.1, module version = 1.0.0
[    12.121] 	Module class: X.Org Server Extension
[    12.121] 	ABI class: X.Org Server Extension, version 5.0
[    12.121] (II) Loading extension DOUBLE-BUFFER
[    12.121] (II) LoadModule: "glx"
[    12.121] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    12.460] (II) Module glx: vendor="NVIDIA Corporation"
[    12.469] 	compiled for 4.0.2, module version = 1.0.0
[    12.469] 	Module class: X.Org Server Extension
[    12.469] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    12.469] (II) Loading extension GLX
[    12.469] (II) LoadModule: "record"
[    12.469] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.469] (II) Module record: vendor="X.Org Foundation"
[    12.469] 	compiled for 1.10.1, module version = 1.13.0
[    12.469] 	Module class: X.Org Server Extension
[    12.469] 	ABI class: X.Org Server Extension, version 5.0
[    12.469] (II) Loading extension RECORD
[    12.469] (II) LoadModule: "dri"
[    12.469] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.469] (II) Module dri: vendor="X.Org Foundation"
[    12.469] 	compiled for 1.10.1, module version = 1.0.0
[    12.469] 	ABI class: X.Org Server Extension, version 5.0
[    12.469] (II) Loading extension XFree86-DRI
[    12.469] (II) LoadModule: "dri2"
[    12.470] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.470] (II) Module dri2: vendor="X.Org Foundation"
[    12.470] 	compiled for 1.10.1, module version = 1.2.0
[    12.470] 	ABI class: X.Org Server Extension, version 5.0
[    12.470] (II) Loading extension DRI2
[    12.470] (II) LoadModule: "nvidia"
[    12.470] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    12.538] (II) Module nvidia: vendor="NVIDIA Corporation"
[    12.539] 	compiled for 4.0.2, module version = 1.0.0
[    12.539] 	Module class: X.Org Video Driver
[    12.556] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    12.556] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.556] (++) using VT number 7

[    12.581] (II) Loading sub module "fb"
[    12.581] (II) LoadModule: "fb"
[    12.581] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.582] (II) Module fb: vendor="X.Org Foundation"
[    12.582] 	compiled for 1.10.1, module version = 1.0.0
[    12.582] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.582] (II) Loading sub module "wfb"
[    12.582] (II) LoadModule: "wfb"
[    12.582] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.589] (II) Module wfb: vendor="X.Org Foundation"
[    12.589] 	compiled for 1.10.1, module version = 1.0.0
[    12.589] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.589] (II) Loading sub module "ramdac"
[    12.589] (II) LoadModule: "ramdac"
[    12.589] (II) Module "ramdac" already built-in
[    12.589] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    12.589] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.589] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.591] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    12.591] (==) NVIDIA(0): RGB weight 888
[    12.591] (==) NVIDIA(0): Default visual is TrueColor
[    12.591] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.591] (**) NVIDIA(0): Option "TwinView" "0"
[    12.591] (**) NVIDIA(0): Option "MetaModes" "1440x900 +0+0"
[    12.591] (**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "CRT-0"
[    12.927] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    12.928] (II) NVIDIA(0): NVIDIA GPU GeForce 7025 / nForce 630a (C61) at PCI:0:13:0
[    12.928] (II) NVIDIA(0):     (GPU-0)
[    12.928] (--) NVIDIA(0): Memory: 524288 kBytes
[    12.928] (--) NVIDIA(0): VideoBIOS: 05.61.32.28.00
[    12.928] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    12.928] (--) NVIDIA(0): Connected display device(s) on GeForce 7025 / nForce 630a at
[    12.928] (--) NVIDIA(0):     PCI:0:13:0
[    12.928] (--) NVIDIA(0):     CRT-0
[    12.928] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    12.929] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    12.929] (II) NVIDIA(0): Validated modes:
[    12.929] (II) NVIDIA(0):     "1440x900+0+0"
[    12.929] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    12.930] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    12.930] (WW) NVIDIA(0):     from CRT-0's EDID.
[    12.930] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    12.930] (--) Depth 24 pixmap format is 32 bpp
[    12.933] (II) NVIDIA(0): Setting mode "1440x900+0+0"
[    13.013] (II) Loading extension NV-GLX
[    13.043] (==) NVIDIA(0): Disabling shared memory pixmaps
[    13.043] (==) NVIDIA(0): Backing store disabled
[    13.043] (==) NVIDIA(0): Silken mouse enabled
[    13.043] (**) NVIDIA(0): DPMS enabled
[    13.043] (II) Loading extension NV-CONTROL
[    13.043] (II) Loading extension XINERAMA
[    13.043] (II) Loading sub module "dri2"
[    13.043] (II) LoadModule: "dri2"
[    13.044] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.044] (II) Module dri2: vendor="X.Org Foundation"
[    13.044] 	compiled for 1.10.1, module version = 1.2.0
[    13.044] 	ABI class: X.Org Server Extension, version 5.0
[    13.044] (II) NVIDIA(0): [DRI2] Setup complete
[    13.044] (==) RandR enabled
[    13.044] (II) Initializing built-in extension Generic Event Extension
[    13.044] (II) Initializing built-in extension SHAPE
[    13.044] (II) Initializing built-in extension MIT-SHM
[    13.044] (II) Initializing built-in extension XInputExtension
[    13.044] (II) Initializing built-in extension XTEST
[    13.044] (II) Initializing built-in extension BIG-REQUESTS
[    13.044] (II) Initializing built-in extension SYNC
[    13.044] (II) Initializing built-in extension XKEYBOARD
[    13.044] (II) Initializing built-in extension XC-MISC
[    13.044] (II) Initializing built-in extension SECURITY
[    13.044] (II) Initializing built-in extension XINERAMA
[    13.044] (II) Initializing built-in extension XFIXES
[    13.044] (II) Initializing built-in extension RENDER
[    13.044] (II) Initializing built-in extension RANDR
[    13.044] (II) Initializing built-in extension COMPOSITE
[    13.044] (II) Initializing built-in extension DAMAGE
[    13.044] (II) Initializing built-in extension GESTURE
[    13.045] (II) Initializing extension GLX
[    13.082] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.088] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.088] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.088] (II) LoadModule: "evdev"
[    13.089] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.089] (II) Module evdev: vendor="X.Org Foundation"
[    13.089] 	compiled for 1.10.0.902, module version = 2.6.0
[    13.089] 	Module class: X.Org XInput Driver
[    13.089] 	ABI class: X.Org XInput driver, version 12.3
[    13.089] (II) Using input driver 'evdev' for 'Power Button'
[    13.089] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.089] (**) Power Button: always reports core events
[    13.089] (**) Power Button: Device: "/dev/input/event1"
[    13.089] (--) Power Button: Found keys
[    13.089] (II) Power Button: Configuring as keyboard
[    13.089] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.089] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.089] (**) Option "xkb_rules" "evdev"
[    13.089] (**) Option "xkb_model" "pc105"
[    13.089] (**) Option "xkb_layout" "us"
[    13.091] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.091] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.091] (II) Using input driver 'evdev' for 'Power Button'
[    13.091] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.091] (**) Power Button: always reports core events
[    13.091] (**) Power Button: Device: "/dev/input/event0"
[    13.091] (--) Power Button: Found keys
[    13.091] (II) Power Button: Configuring as keyboard
[    13.091] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.091] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.091] (**) Option "xkb_rules" "evdev"
[    13.091] (**) Option "xkb_model" "pc105"
[    13.091] (**) Option "xkb_layout" "us"
[    13.093] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event4)
[    13.093] (II) No input driver/identifier specified (ignoring)
[    13.095] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.095] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.095] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.095] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.095] (**) AT Translated Set 2 keyboard: always reports core events
[    13.095] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.096] (--) AT Translated Set 2 keyboard: Found keys
[    13.096] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.096] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.096] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.096] (**) Option "xkb_rules" "evdev"
[    13.096] (**) Option "xkb_model" "pc105"
[    13.096] (**) Option "xkb_layout" "us"
[    13.096] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    13.096] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    13.096] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    13.096] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.096] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    13.096] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    13.100] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    13.100] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    13.100] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    13.100] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    13.100] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    13.100] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    13.100] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    13.100] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.100] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    13.100] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    13.100] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    13.100] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    13.100] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    13.100] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    13.100] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    13.100] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    13.100] (II) No input driver/identifier specified (ignoring)
[    13.752] (II) NVIDIA(0): Setting mode "1360x768"
[    87.378] (II) NVIDIA(0): Setting mode "CRT-0:1024x768@1024x768+0+0"
[   374.600] (II) NVIDIA(0): Setting mode "1360x768"
[   374.901] (II) NVIDIA(0): Setting mode "CRT-0:1920x1200@1920x1200+0+0"
[   381.830] (II) NVIDIA(0): Setting mode "CRT-0:1024x768@1024x768+0+0"
[   970.219] (II) NVIDIA(0): Setting mode "1440x900+0+0"
```



Nvidia bug report attached

---

### Post by realzippy on 2011-07-31
[    12.927] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0

Seems to be the old EDID problem.

Ok,suggest to create new xorg.conf:

Run:

```
sudo nvidia-xconfig
```

Then reboot.
Probably it rebootes in 1024x768.
Do not start nvidia-settings or the "Monitors" GUI then.
Run 
```
xrandr -q
```
..and post the output.

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> [    12.927] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0

Seems to be the old EDID problem.
```

```
Ok,suggest to create new xorg.conf:

Run:

```
sudo nvidia-xconfig
```

Then reboot.
Probably it rebootes in 1024x768.
Do not start nvidia-settings or the "Monitors" GUI then.
Run 
```
xrandr -q
```
..and post the output.

I did what you asked , and yes it rebooted in 1024x768 .
I ran the code and this is what i got
```
arun@ubuntu:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   680x384        67.0     68.0  
   640x512        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0  
   576x432        75.0     76.0     77.0     78.0  
   512x384        79.0     80.0     81.0  
   416x312        82.0  
   400x300        83.0     84.0     85.0     86.0  
   320x240        87.0     88.0     89.0  
arun@ubuntu:~$ 


```

---

### Post by CatKiller on 2011-07-31
> **arun.manuel14 said:**
> Also before @realzippy started helping me out , i googled and messed around with my xorg.conf , could that be the reason?

Could be :)

I'll be honest with you; I don't like metamodes. Never have done. And when I learned about this stuff because my monitor gave inaccurate EDID information, it was all done by xorg.conf. I find the new automatic methods a bit opaque, and I've not had to deal with them that much because I subsequently got a monitor that behaves nicely. So this is a reflection of my own biases.

With that out of the way, I would personally change xorg.conf around a bit.

```
Section "Monitor"
    Identifier     "Monitor0"
[B]    HorizSync       30-81
    VertRefresh     56-75[/B]
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
**     Option        "ModeDebug"            "True"**
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
[B]    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes        "1600x900"
    EndSubSection[/B]
EndSection

```Explicitly putting in the mode should mean that X at least tries it. ModeDebug should give us more information on why it fails. If it doesn't work, either the log or the output of nvidia-bug-report might give us more clues.

EDIT: I see you've generated a new xorg.conf while I was typing that. The important bits are in bold. The names and so on aren't that important, provided they're consistent where they are used.

---

### Post by arun.manuel14 on 2011-07-31
> **CatKiller said:**
> Could be :)

Explicitly putting in the mode should mean that X at least tries it. ModeDebug should give us more information on why it fails. If it doesn't work, either the log or the output of nvidia-bug-report might give us more clues.

EDIT: I see you've generated a new xorg.conf while I was typing that. The important bits are in bold. The names and so on aren't that important, provided they're consistent where they are used.

Uh , so do you want me to edit my xorg.conf in accordance with the highlighted ones that you posted?

---

### Post by CatKiller on 2011-07-31
> **arun.manuel14 said:**
> Uh , so do you want me to edit my xorg.conf in accordance with the highlighted ones that you posted?

Yep. Might help :) Won't make it worse.

---

### Post by arun.manuel14 on 2011-07-31
> **CatKiller said:**
> Could be :)
Explicitly putting in the mode should mean that X at least tries it.

This is what my xorg.conf looks like right now (without the chages you asked me to make)

```
Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"

# Removed Option "metamodes" "1600x900_60 +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "1440x900 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


After i make the changes it should look

```
Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    **Option        "ModeDebug"            "True"**
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"

# Removed Option "metamodes" "1600x900_60 +0+0"
# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "1440x900 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    **DefaultDepth    24**
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768 +0+0"
    [B]SubSection     "Display"
        Depth       24
        Modes        "1600x900"[/B]
    EndSubSection
EndSection

```

Like this?

---

### Post by CatKiller on 2011-07-31
> **arun.manuel14 said:**
> Like this?

Not quite. Take out the metamode and TwinView stuff. Your old xorg.conf was included in the nvidia-bug-report output you posted earlier.

---

### Post by CatKiller on 2011-07-31
> **realzippy said:**
> Seems to be the old EDID problem.

At least we've got to the point where monitor manufacturers have worked out how to do this for most of their new monitors. The spec's what, 15 years old? 20? It's shocking that this was ever a problem.

---

### Post by arun.manuel14 on 2011-07-31
> **CatKiller said:**
> Not quite. Take out the metamode and TwinView stuff. Your old xorg.conf was included in the nvidia-bug-report output you posted earlier.


Still nothing!
Rebooted in 1024x768 . 

xrandr report (after editing xorg.conf)


```
arun@ubuntu:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   680x384        67.0     68.0  
   640x512        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0  
   576x432        75.0     76.0     77.0     78.0  
   512x384        79.0     80.0     81.0  
   416x312        82.0  
   400x300        83.0     84.0     85.0     86.0  
   320x240        87.0     88.0     89.0  
arun@ubuntu:~$ 

```


But my Nvidia X Driver settings still shows 1920x1200 option

---

### Post by realzippy on 2011-07-31
Please show current running xorg.conf...

---

### Post by CatKiller on 2011-07-31
What does the X.org log have to say about why it didn't pick the mode you specified?

EDIT:

> **arun.manuel14 said:**
> Rebooted in 1024x768 . 

That's to be expected. You've manually chosen 1024x768 as your resolution, so it will stay like that till you pick a different one, even if a higher resolution is available. The login screen will probably be the highest-available resolution, though.

Also, you probably don't need to reboot. Logging out should be sufficient to restart X.

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> Please show current running xorg.conf...

current xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
     Option        "ModeDebug"            "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"


    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes        "1600x900"
    EndSubSection
EndSection
```

---

### Post by arun.manuel14 on 2011-07-31
> **CatKiller said:**
> What does the X.org log have to say about why it didn't pick the mode you specified?

EDIT:



That's to be expected. You've manually chosen 1024x768 as your resolution, so it will stay like that till you pick a different one, even if a higher resolution is available. The login screen will probably be the highest-available resolution, though.

Also, you probably don't need to reboot. Logging out should be sufficient to restart X.
 
x.org log

```
[    12.363] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    12.363] X Protocol Version 11, Revision 0
[    12.363] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    12.363] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    12.363] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=1EFC69DDFC69AFA7 loop=/ubuntu/disks/root.disk ro quiet splash
[    12.363] Build Date: 19 April 2011  03:40:45PM
[    12.363] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    12.363] Current version of pixman: 0.20.2
[    12.363] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.363] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.363] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  1 01:49:39 2011
[    12.363] (==) Using config file: "/etc/X11/xorg.conf"
[    12.363] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.364] (==) ServerLayout "Layout0"
[    12.364] (**) |-->Screen "Screen0" (0)
[    12.364] (**) |   |-->Monitor "Monitor0"
[    12.364] (**) |   |-->Device "Device0"
[    12.364] (**) |-->Input Device "Keyboard0"
[    12.364] (**) |-->Input Device "Mouse0"
[    12.364] (**) Option "Xinerama" "0"
[    12.364] (==) Automatically adding devices
[    12.364] (==) Automatically enabling devices
[    12.364] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.364] 	Entry deleted from font path.
[    12.364] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.364] 	Entry deleted from font path.
[    12.364] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.364] 	Entry deleted from font path.
[    12.364] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.364] 	Entry deleted from font path.
[    12.364] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.364] 	Entry deleted from font path.
[    12.364] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.364] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.364] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    12.364] (WW) Disabling Keyboard0
[    12.364] (WW) Disabling Mouse0
[    12.364] (II) Loader magic: 0x7e0280
[    12.364] (II) Module ABI versions:
[    12.364] 	X.Org ANSI C Emulation: 0.4
[    12.364] 	X.Org Video Driver: 10.0
[    12.364] 	X.Org XInput driver : 12.3
[    12.364] 	X.Org Server Extension : 5.0
[    12.365] (--) PCI:*(0:0:13:0) 10de:03d6:1043:83a4 rev 162, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, BIOS @ 0x????????/131072
[    12.365] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.365] (II) LoadModule: "extmod"
[    12.387] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.387] (II) Module extmod: vendor="X.Org Foundation"
[    12.387] 	compiled for 1.10.1, module version = 1.0.0
[    12.387] 	Module class: X.Org Server Extension
[    12.387] 	ABI class: X.Org Server Extension, version 5.0
[    12.387] (II) Loading extension MIT-SCREEN-SAVER
[    12.387] (II) Loading extension XFree86-VidModeExtension
[    12.387] (II) Loading extension XFree86-DGA
[    12.387] (II) Loading extension DPMS
[    12.387] (II) Loading extension XVideo
[    12.387] (II) Loading extension XVideo-MotionCompensation
[    12.387] (II) Loading extension X-Resource
[    12.387] (II) LoadModule: "dbe"
[    12.387] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.387] (II) Module dbe: vendor="X.Org Foundation"
[    12.387] 	compiled for 1.10.1, module version = 1.0.0
[    12.387] 	Module class: X.Org Server Extension
[    12.387] 	ABI class: X.Org Server Extension, version 5.0
[    12.387] (II) Loading extension DOUBLE-BUFFER
[    12.387] (II) LoadModule: "glx"
[    12.387] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    12.726] (II) Module glx: vendor="NVIDIA Corporation"
[    12.735] 	compiled for 4.0.2, module version = 1.0.0
[    12.735] 	Module class: X.Org Server Extension
[    12.735] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    12.735] (II) Loading extension GLX
[    12.735] (II) LoadModule: "record"
[    12.735] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.735] (II) Module record: vendor="X.Org Foundation"
[    12.735] 	compiled for 1.10.1, module version = 1.13.0
[    12.735] 	Module class: X.Org Server Extension
[    12.735] 	ABI class: X.Org Server Extension, version 5.0
[    12.735] (II) Loading extension RECORD
[    12.735] (II) LoadModule: "dri"
[    12.736] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.736] (II) Module dri: vendor="X.Org Foundation"
[    12.736] 	compiled for 1.10.1, module version = 1.0.0
[    12.736] 	ABI class: X.Org Server Extension, version 5.0
[    12.736] (II) Loading extension XFree86-DRI
[    12.736] (II) LoadModule: "dri2"
[    12.736] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.736] (II) Module dri2: vendor="X.Org Foundation"
[    12.736] 	compiled for 1.10.1, module version = 1.2.0
[    12.736] 	ABI class: X.Org Server Extension, version 5.0
[    12.736] (II) Loading extension DRI2
[    12.736] (II) LoadModule: "nvidia"
[    12.736] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    12.804] (II) Module nvidia: vendor="NVIDIA Corporation"
[    12.805] 	compiled for 4.0.2, module version = 1.0.0
[    12.805] 	Module class: X.Org Video Driver
[    12.823] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    12.823] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.823] (++) using VT number 7

[    12.847] (II) Loading sub module "fb"
[    12.848] (II) LoadModule: "fb"
[    12.848] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.848] (II) Module fb: vendor="X.Org Foundation"
[    12.848] 	compiled for 1.10.1, module version = 1.0.0
[    12.848] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.848] (II) Loading sub module "wfb"
[    12.848] (II) LoadModule: "wfb"
[    12.848] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.855] (II) Module wfb: vendor="X.Org Foundation"
[    12.855] 	compiled for 1.10.1, module version = 1.0.0
[    12.855] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.855] (II) Loading sub module "ramdac"
[    12.855] (II) LoadModule: "ramdac"
[    12.855] (II) Module "ramdac" already built-in
[    12.856] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    12.856] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.856] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.857] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    12.857] (==) NVIDIA(0): RGB weight 888
[    12.857] (==) NVIDIA(0): Default visual is TrueColor
[    12.857] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.857] (**) NVIDIA(0): Option "ModeDebug" "True"
[    13.194] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    13.194] (II) NVIDIA(0): NVIDIA GPU GeForce 7025 / nForce 630a (C61) at PCI:0:13:0
[    13.194] (II) NVIDIA(0):     (GPU-0)
[    13.194] (--) NVIDIA(0): Memory: 524288 kBytes
[    13.194] (--) NVIDIA(0): VideoBIOS: 05.61.32.28.00
[    13.194] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    13.194] (--) NVIDIA(0): Connected display device(s) on GeForce 7025 / nForce 630a at
[    13.194] (--) NVIDIA(0):     PCI:0:13:0
[    13.194] (--) NVIDIA(0):     CRT-0
[    13.194] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    13.194] (--) NVIDIA(0): 
[    13.194] (--) NVIDIA(0): --- EDID for CRT-0 ---
[    13.194] (--) NVIDIA(0): 
[    13.194] (--) NVIDIA(0): No EDID Available.
[    13.194] (--) NVIDIA(0): 
[    13.195] (--) NVIDIA(0): --- End of EDID for CRT-0 ---
[    13.195] (--) NVIDIA(0): 
[    13.195] (II) NVIDIA(0): Frequency information for CRT-0:
[    13.195] (II) NVIDIA(0):   HorizSync   : 30.000-81.000 kHz
[    13.195] (II) NVIDIA(0):   VertRefresh : 56.000-75.000 Hz
[    13.195] (II) NVIDIA(0):     (HorizSync from HorizSync in X Config Monitor section)
[    13.195] (II) NVIDIA(0):     (VertRefresh from VertRefresh in X Config Monitor
[    13.195] (II) NVIDIA(0):     section)
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0): --- Building ModePool for CRT-0 ---
[    13.195] (II) NVIDIA(0):   Validating Mode "640x350":
[    13.195] (II) NVIDIA(0):     640 x 350 @ 85 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  350,  382
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
[    13.195] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.195] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "320x175":
[    13.195] (II) NVIDIA(0):     320 x 175 @ 85 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  320,  336
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  175,  191
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
[    13.195] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.195] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
[    13.195] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "640x400":
[    13.195] (II) NVIDIA(0):     640 x 400 @ 85 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.195] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "320x200":
[    13.195] (II) NVIDIA(0):     320 x 200 @ 85 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  320,  336
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  200,  200
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.195] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
[    13.195] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "720x400":
[    13.195] (II) NVIDIA(0):     720 x 400 @ 85 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  720,  756
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.195] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "360x200":
[    13.195] (II) NVIDIA(0):     360 x 200 @ 85 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  360,  378
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  200,  200
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.195] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.195] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.195] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.195] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  480,  490
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.195] (II) NVIDIA(0):     Mode is valid.
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "320x240":
[    13.195] (II) NVIDIA(0):     320 x 240 @ 60 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  320,  328
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  240,  245
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.195] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.195] (II) NVIDIA(0):     Mode is valid.
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.195] (II) NVIDIA(0):     640 x 480 @ 73 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
[    13.195] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    13.195] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
[    13.195] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.195] (II) NVIDIA(0):     Mode is valid.
[    13.195] (II) NVIDIA(0): 
[    13.195] (II) NVIDIA(0):   Validating Mode "320x240":
[    13.195] (II) NVIDIA(0):     320 x 240 @ 73 Hz
[    13.195] (II) NVIDIA(0):     Mode Source: X Server
[    13.195] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    13.195] (II) NVIDIA(0):       HRes, HSyncStart :  320,  332
[    13.195] (II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  240,  244
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
[    13.196] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.196] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.196] (II) NVIDIA(0):     640 x 480 @ 75 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
[    13.196] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "320x240":
[    13.196] (II) NVIDIA(0):     320 x 240 @ 75 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  320,  328
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  240,  240
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
[    13.196] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.196] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.196] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  640,  696
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
[    13.196] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.196] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.196] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "320x240":
[    13.196] (II) NVIDIA(0):     320 x 240 @ 85 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  320,  348
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  240,  240
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
[    13.196] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.196] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.196] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
[    13.196] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.196] (II) NVIDIA(0):     800 x 600 @ 56 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  800,  824
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "400x300":
[    13.196] (II) NVIDIA(0):     400 x 300 @ 56 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  400,  412
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.196] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "400x300":
[    13.196] (II) NVIDIA(0):     400 x 300 @ 60 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  400,  420
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.196] (II) NVIDIA(0):     800 x 600 @ 72 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  800,  856
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  600,  637
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "400x300":
[    13.196] (II) NVIDIA(0):     400 x 300 @ 72 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  400,  428
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  300,  318
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.196] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.196] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[    13.196] (II) NVIDIA(0):     Mode Source: X Server
[    13.196] (II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
[    13.196] (II) NVIDIA(0):       HRes, HSyncStart :  800,  816
[    13.196] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
[    13.196] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.196] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
[    13.196] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.196] (II) NVIDIA(0):     Mode is valid.
[    13.196] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "400x300":
[    13.197] (II) NVIDIA(0):     400 x 300 @ 75 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  400,  408
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.197] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.197] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "400x300":
[    13.197] (II) NVIDIA(0):     400 x 300 @ 85 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  400,  416
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  300,  300
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.197] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
[    13.197] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "1024x768i":
[    13.197] (II) NVIDIA(0):     1024 x 768 @ 87 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (II) NVIDIA(0):       Extra            : Interlace
[    13.197] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
[    13.197] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "512x384i":
[    13.197] (II) NVIDIA(0):     512 x 384 @ 87 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  512,  516
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (II) NVIDIA(0):       Extra            : Interlace DoubleScan
[    13.197] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
[    13.197] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.197] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    13.197] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "512x384":
[    13.197] (II) NVIDIA(0):     512 x 384 @ 60 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  512,  524
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
[    13.197] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.197] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.197] (II) NVIDIA(0):     1024 x 768 @ 70 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    13.197] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "512x384":
[    13.197] (II) NVIDIA(0):     512 x 384 @ 70 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  512,  524
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
[    13.197] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.197] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.197] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "512x384":
[    13.197] (II) NVIDIA(0):     512 x 384 @ 75 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.197] (II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
[    13.197] (II) NVIDIA(0):       HRes, HSyncStart :  512,  520
[    13.197] (II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
[    13.197] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[    13.197] (II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
[    13.197] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.197] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.197] (II) NVIDIA(0):     Mode is valid.
[    13.197] (II) NVIDIA(0): 
[    13.197] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.197] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[    13.197] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.198] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "512x384":
[    13.198] (II) NVIDIA(0):     512 x 384 @ 85 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart :  512,  536
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  384,  384
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.198] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.198] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.198] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.198] (II) NVIDIA(0):     576 x 432 @ 75 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "1280x960":
[    13.198] (II) NVIDIA(0):     1280 x 960 @ 60 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.198] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart :  640,  688
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  480,  480
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "1280x960":
[    13.198] (II) NVIDIA(0):     1280 x 960 @ 85 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
[    13.198] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.198] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  480,  480
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.198] (WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
[    13.198] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    13.198] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "640x512":
[    13.198] (II) NVIDIA(0):     640 x 512 @ 60 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    13.198] (II) NVIDIA(0):     1280 x 1024 @ 75 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    13.198] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.198] (II) NVIDIA(0):     Mode is valid.
[    13.198] (II) NVIDIA(0): 
[    13.198] (II) NVIDIA(0):   Validating Mode "640x512":
[    13.198] (II) NVIDIA(0):     640 x 512 @ 75 Hz
[    13.198] (II) NVIDIA(0):     Mode Source: X Server
[    13.198] (II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
[    13.198] (II) NVIDIA(0):       HRes, HSyncStart :  640,  648
[    13.198] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
[    13.198] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    13.198] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.199] (II) NVIDIA(0):     Mode is valid.
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    13.199] (II) NVIDIA(0):     1280 x 1024 @ 85 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
[    13.199] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "640x512":
[    13.199] (II) NVIDIA(0):     640 x 512 @ 85 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
[    13.199] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.199] (II) NVIDIA(0):     1600 x 1200 @ 60 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):     Mode is valid.
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.199] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.199] (II) NVIDIA(0):     Mode is valid.
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.199] (II) NVIDIA(0):     1600 x 1200 @ 65 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):     Mode is valid.
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.199] (II) NVIDIA(0):     800 x 600 @ 65 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.199] (II) NVIDIA(0):     Mode is valid.
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.199] (II) NVIDIA(0):     1600 x 1200 @ 70 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
[    13.199] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.199] (II) NVIDIA(0):     800 x 600 @ 70 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
[    13.199] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.199] (II) NVIDIA(0):     1600 x 1200 @ 75 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[    13.199] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.199] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[    13.199] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.199] (II) NVIDIA(0): 
[    13.199] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.199] (II) NVIDIA(0):     1600 x 1200 @ 85 Hz
[    13.199] (II) NVIDIA(0):     Mode Source: X Server
[    13.199] (II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
[    13.199] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.199] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.199] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.199] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.199] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.199] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.200] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart :  600,  600
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
[    13.200] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.200] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    13.200] (II) NVIDIA(0):     1792 x 1344 @ 60 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "896x672":
[    13.200] (II) NVIDIA(0):     896 x 672 @ 60 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart :  896,  960
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart :  672,  672
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    13.200] (II) NVIDIA(0):     1792 x 1344 @ 75 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "896x672":
[    13.200] (II) NVIDIA(0):     896 x 672 @ 75 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart :  896,  944
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart :  672,  672
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    13.200] (II) NVIDIA(0):     1856 x 1392 @ 60 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "928x696":
[    13.200] (II) NVIDIA(0):     928 x 696 @ 60 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart :  928,  976
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart :  696,  696
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    13.200] (II) NVIDIA(0):     1856 x 1392 @ 75 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "928x696":
[    13.200] (II) NVIDIA(0):     928 x 696 @ 75 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart :  928,  992
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart :  696,  696
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    13.200] (II) NVIDIA(0):     1920 x 1440 @ 60 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
[    13.200] (II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
[    13.200] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    13.200] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    13.200] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.200] (WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
[    13.200] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.200] (II) NVIDIA(0): 
[    13.200] (II) NVIDIA(0):   Validating Mode "960x720":
[    13.200] (II) NVIDIA(0):     960 x 720 @ 60 Hz
[    13.200] (II) NVIDIA(0):     Mode Source: X Server
[    13.200] (II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
[    13.200] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.201] (WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
[    13.201] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    13.201] (II) NVIDIA(0):     1920 x 1440 @ 75 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[    13.201] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "960x720":
[    13.201] (II) NVIDIA(0):     960 x 720 @ 75 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.201] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[    13.201] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "832x624":
[    13.201] (II) NVIDIA(0):     832 x 624 @ 75 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart :  832,  864
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  624,  625
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "416x312":
[    13.201] (II) NVIDIA(0):     416 x 312 @ 75 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart :  416,  432
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  312,  312
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.201] (II) NVIDIA(0):     1152 x 864 @ 60 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.201] (II) NVIDIA(0):     576 x 432 @ 60 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.201] (II) NVIDIA(0):     1152 x 864 @ 70 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.201] (II) NVIDIA(0):     576 x 432 @ 70 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.201] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.201] (II) NVIDIA(0):     576 x 432 @ 75 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.201] (II) NVIDIA(0):     Mode is valid.
[    13.201] (II) NVIDIA(0): 
[    13.201] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.201] (II) NVIDIA(0):     1152 x 864 @ 85 Hz
[    13.201] (II) NVIDIA(0):     Mode Source: X Server
[    13.201] (II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
[    13.201] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
[    13.201] (II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
[    13.201] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.201] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
[    13.201] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.201] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.201] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.201] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.202] (II) NVIDIA(0):     576 x 432 @ 85 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart :  576,  612
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
[    13.202] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.202] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.202] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.202] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.202] (II) NVIDIA(0):     1152 x 864 @ 85 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
[    13.202] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.202] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.202] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.202] (II) NVIDIA(0):     576 x 432 @ 85 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart :  576,  608
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
[    13.202] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.202] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.202] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
[    13.202] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.202] (II) NVIDIA(0):     1152 x 864 @ 100 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
[    13.202] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.202] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
[    13.202] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "576x432":
[    13.202] (II) NVIDIA(0):     576 x 432 @ 100 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart :  576,  616
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  432,  432
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
[    13.202] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.202] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.202] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
[    13.202] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "1360x768":
[    13.202] (II) NVIDIA(0):     1360 x 768 @ 60 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
[    13.202] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.202] (II) NVIDIA(0):     Mode is valid.
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "680x384":
[    13.202] (II) NVIDIA(0):     680 x 384 @ 60 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart :  680,  704
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
[    13.202] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.202] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.202] (II) NVIDIA(0):     Mode is valid.
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "1360x768":
[    13.202] (II) NVIDIA(0):     1360 x 768 @ 60 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
[    13.202] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.202] (II) NVIDIA(0):     Mode is valid.
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "680x384":
[    13.202] (II) NVIDIA(0):     680 x 384 @ 60 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart :  680,  716
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  384,  385
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
[    13.202] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.202] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.202] (II) NVIDIA(0):     Mode is valid.
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    13.202] (II) NVIDIA(0):     1400 x 1050 @ 60 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
[    13.202] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.202] (II) NVIDIA(0):     Mode is valid.
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "700x525":
[    13.202] (II) NVIDIA(0):     700 x 525 @ 60 Hz
[    13.202] (II) NVIDIA(0):     Mode Source: X Server
[    13.202] (II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
[    13.202] (II) NVIDIA(0):       HRes, HSyncStart :  700,  744
[    13.202] (II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
[    13.202] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.202] (II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
[    13.202] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.202] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.202] (WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
[    13.202] (WW) NVIDIA(0):     8.
[    13.202] (II) NVIDIA(0): 
[    13.202] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    13.202] (II) NVIDIA(0):     1400 x 1050 @ 70 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
[    13.203] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "700x525":
[    13.203] (II) NVIDIA(0):     700 x 525 @ 70 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart :  700,  748
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  525,  525
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
[    13.203] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.203] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.203] (WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
[    13.203] (WW) NVIDIA(0):     8.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    13.203] (II) NVIDIA(0):     1400 x 1050 @ 75 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
[    13.203] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "700x525":
[    13.203] (II) NVIDIA(0):     700 x 525 @ 75 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart :  700,  732
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
[    13.203] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.203] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.203] (WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
[    13.203] (WW) NVIDIA(0):     8.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "1400x1050":
[    13.203] (II) NVIDIA(0):     1400 x 1050 @ 85 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
[    13.203] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.203] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[    13.203] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "700x525":
[    13.203] (II) NVIDIA(0):     700 x 525 @ 85 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart :  700,  752
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  525,  525
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
[    13.203] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.203] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.203] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[    13.203] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "1440x900":
[    13.203] (II) NVIDIA(0):     1440 x 900 @ 60 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  900,  903
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
[    13.203] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "720x450":
[    13.203] (II) NVIDIA(0):     720 x 450 @ 60 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart :  720,  760
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  450,  451
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
[    13.203] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.203] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "1600x1024":
[    13.203] (II) NVIDIA(0):     1600 x 1024 @ 60 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
[    13.203] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "800x512":
[    13.203] (II) NVIDIA(0):     800 x 512 @ 60 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart :  800,  800
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  512,  512
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
[    13.203] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.203] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    13.203] (II) NVIDIA(0):     1680 x 1050 @ 60 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
[    13.203] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.203] (II) NVIDIA(0):     Mode is valid.
[    13.203] (II) NVIDIA(0): 
[    13.203] (II) NVIDIA(0):   Validating Mode "840x525":
[    13.203] (II) NVIDIA(0):     840 x 525 @ 60 Hz
[    13.203] (II) NVIDIA(0):     Mode Source: X Server
[    13.203] (II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
[    13.203] (II) NVIDIA(0):       HRes, HSyncStart :  840,  864
[    13.203] (II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
[    13.203] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.203] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
[    13.204] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.204] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    13.204] (II) NVIDIA(0):     1680 x 1050 @ 60 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "840x525":
[    13.204] (II) NVIDIA(0):     840 x 525 @ 60 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart :  840,  892
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    13.204] (II) NVIDIA(0):     1680 x 1050 @ 70 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "840x525":
[    13.204] (II) NVIDIA(0):     840 x 525 @ 70 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart :  840,  900
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    13.204] (II) NVIDIA(0):     1680 x 1050 @ 75 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
[    13.204] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "840x525":
[    13.204] (II) NVIDIA(0):     840 x 525 @ 75 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart :  840,  900
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.204] (WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
[    13.204] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "1680x1050":
[    13.204] (II) NVIDIA(0):     1680 x 1050 @ 85 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
[    13.204] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "840x525":
[    13.204] (II) NVIDIA(0):     840 x 525 @ 85 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart :  840,  904
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart :  525,  526
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
[    13.204] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.204] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.204] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
[    13.204] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "1920x1080":
[    13.204] (II) NVIDIA(0):     1920 x 1080 @ 60 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
[    13.204] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "960x540":
[    13.204] (II) NVIDIA(0):     960 x 540 @ 60 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart :  960,  984
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart :  540,  541
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
[    13.204] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.204] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "1920x1200":
[    13.204] (II) NVIDIA(0):     1920 x 1200 @ 60 Hz
[    13.204] (II) NVIDIA(0):     Mode Source: X Server
[    13.204] (II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
[    13.204] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
[    13.204] (II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
[    13.204] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
[    13.204] (II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
[    13.204] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.204] (II) NVIDIA(0):     Mode is valid.
[    13.204] (II) NVIDIA(0): 
[    13.204] (II) NVIDIA(0):   Validating Mode "960x600":
[    13.205] (II) NVIDIA(0):     960 x 600 @ 60 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart :  960,  984
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
[    13.205] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.205] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.205] (II) NVIDIA(0):     Mode is valid.
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    13.205] (II) NVIDIA(0):     1920 x 1440 @ 85 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "960x720":
[    13.205] (II) NVIDIA(0):     960 x 720 @ 85 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  720,  720
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (128.5 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "2048x1536":
[    13.205] (II) NVIDIA(0):     2048 x 1536 @ 60 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.205] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "2048x1536":
[    13.205] (II) NVIDIA(0):     2048 x 1536 @ 75 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.205] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (120.2 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "2048x1536":
[    13.205] (II) NVIDIA(0):     2048 x 1536 @ 85 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
[    13.205] (WW) NVIDIA(0):     Display Device (Max: 350.0 MHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.205] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: X Server
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (II) NVIDIA(0):       Extra            : DoubleScan
[    13.205] (WW) NVIDIA(0):     Mode is rejected: HorizSync (137.0 kHz) out of range
[    13.205] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "640x350":
[    13.205] (II) NVIDIA(0):     640 x 350 @ 85 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: VESA
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  350,  382
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
[    13.205] (II) NVIDIA(0):       H/V Polarity     : +/-
[    13.205] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.205] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "640x400":
[    13.205] (II) NVIDIA(0):     640 x 400 @ 85 Hz
[    13.205] (II) NVIDIA(0):     Mode Source: VESA
[    13.205] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.205] (II) NVIDIA(0):       HRes, HSyncStart :  640,  672
[    13.205] (II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
[    13.205] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    13.205] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
[    13.205] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.205] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.205] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.205] (II) NVIDIA(0): 
[    13.205] (II) NVIDIA(0):   Validating Mode "720x400":
[    13.205] (II) NVIDIA(0):     720 x 400 @ 85 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  720,  756
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  400,  401
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
[    13.206] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.206] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.206] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.206] (II) NVIDIA(0):     640 x 480 @ 60 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  480,  490
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
[    13.206] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.206] (II) NVIDIA(0):     640 x 480 @ 73 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  640,  664
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  480,  489
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
[    13.206] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.206] (II) NVIDIA(0):     640 x 480 @ 75 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  640,  656
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
[    13.206] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "640x480":
[    13.206] (II) NVIDIA(0):     640 x 480 @ 85 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  640,  696
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  480,  481
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
[    13.206] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.206] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.206] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.206] (II) NVIDIA(0):     800 x 600 @ 56 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  800,  824
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
[    13.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.206] (II) NVIDIA(0):     800 x 600 @ 60 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  800,  840
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
[    13.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.206] (II) NVIDIA(0):     800 x 600 @ 72 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  800,  856
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  600,  637
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
[    13.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.206] (II) NVIDIA(0):     800 x 600 @ 75 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  800,  816
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
[    13.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "800x600":
[    13.206] (II) NVIDIA(0):     800 x 600 @ 85 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart :  800,  832
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  600,  601
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
[    13.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.206] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
[    13.206] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.206] (II) NVIDIA(0):     1024 x 768 @ 87 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  768,  768
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
[    13.206] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.206] (II) NVIDIA(0):       Extra            : Interlace
[    13.206] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
[    13.206] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.206] (II) NVIDIA(0):     1024 x 768 @ 60 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.206] (II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
[    13.206] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    13.206] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
[    13.206] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    13.206] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    13.206] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.206] (II) NVIDIA(0):     Mode is valid.
[    13.206] (II) NVIDIA(0): 
[    13.206] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.206] (II) NVIDIA(0):     1024 x 768 @ 70 Hz
[    13.206] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart :  768,  771
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
[    13.207] (II) NVIDIA(0):       H/V Polarity     : -/-
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.207] (II) NVIDIA(0):     1024 x 768 @ 75 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1024x768":
[    13.207] (II) NVIDIA(0):     1024 x 768 @ 85 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart :  768,  769
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
[    13.207] (WW) NVIDIA(0):     (56.000-75.000 Hz).
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1152x864":
[    13.207] (II) NVIDIA(0):     1152 x 864 @ 75 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart :  864,  865
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1280x960":
[    13.207] (II) NVIDIA(0):     1280 x 960 @ 60 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1280x960":
[    13.207] (II) NVIDIA(0):     1280 x 960 @ 85 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart :  960,  961
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
[    13.207] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    13.207] (II) NVIDIA(0):     1280 x 1024 @ 60 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    13.207] (II) NVIDIA(0):     1280 x 1024 @ 75 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1280x1024":
[    13.207] (II) NVIDIA(0):     1280 x 1024 @ 85 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
[    13.207] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.207] (II) NVIDIA(0):     1600 x 1200 @ 60 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.207] (II) NVIDIA(0):     1600 x 1200 @ 65 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (II) NVIDIA(0):     Mode is valid.
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.207] (II) NVIDIA(0):     1600 x 1200 @ 70 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.207] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.207] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.207] (WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
[    13.207] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.207] (II) NVIDIA(0): 
[    13.207] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.207] (II) NVIDIA(0):     1600 x 1200 @ 75 Hz
[    13.207] (II) NVIDIA(0):     Mode Source: VESA
[    13.207] (II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
[    13.207] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.207] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.207] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.208] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1600x1200":
[    13.208] (II) NVIDIA(0):     1600 x 1200 @ 85 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
[    13.208] (II) NVIDIA(0):       H/V Polarity     : +/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    13.208] (II) NVIDIA(0):     1792 x 1344 @ 60 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
[    13.208] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1792x1344":
[    13.208] (II) NVIDIA(0):     1792 x 1344 @ 75 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
[    13.208] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    13.208] (II) NVIDIA(0):     1856 x 1392 @ 60 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
[    13.208] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1856x1392":
[    13.208] (II) NVIDIA(0):     1856 x 1392 @ 75 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
[    13.208] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    13.208] (II) NVIDIA(0):     1920 x 1440 @ 60 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    13.208] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0):   Validating Mode "1920x1440":
[    13.208] (II) NVIDIA(0):     1920 x 1440 @ 75 Hz
[    13.208] (II) NVIDIA(0):     Mode Source: VESA
[    13.208] (II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
[    13.208] (II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
[    13.208] (II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
[    13.208] (II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
[    13.208] (II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
[    13.208] (II) NVIDIA(0):       H/V Polarity     : -/+
[    13.208] (WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
[    13.208] (WW) NVIDIA(0):     (30.000-81.000 kHz).
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0): --- Done building ModePool for CRT-0 ---
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0): 
[    13.208] (II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
[    13.208] (II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1920x1200"          : 1920 x 1200 @  60.0 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1920x1200_60"       : 1920 x 1200 @  60.0 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1920x1080"          : 1920 x 1080 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1920x1080_60"       : 1920 x 1080 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050"          : 1680 x 1050 @  69.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050_70"       : 1680 x 1050 @  69.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050_60"       : 1680 x 1050 @  60.0 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050_60_0"     : 1680 x 1050 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1600x1200"          : 1600 x 1200 @  65.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1600x1200_65"       : 1600 x 1200 @  65.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1600x1200_60"       : 1600 x 1200 @  60.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.2 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1600x1024_60"       : 1600 x 1024 @  60.2 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1440x900"           : 1440 x  900 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  74.8 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1400x1050_75"       : 1400 x 1050 @  74.8 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1400x1050_70"       : 1400 x 1050 @  70.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1400x1050_60"       : 1400 x 1050 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x1024_75"       : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1152x864"           : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1152x864_75"        : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1152x864_75_0"      : 1152 x  864 @  75.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1152x864_70"        : 1152 x  864 @  70.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1152x864_60"        : 1152 x  864 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1024x768"           : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "960x600d60"         :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "960x540"            :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "960x540d60"         :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525"            :  840 x  525 @  69.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525d70"         :  840 x  525 @  69.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525d60_0"       :  840 x  525 @  59.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "832x624"            :  832 x  624 @  74.6 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.6 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600"            :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600d65"         :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x512"            :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "720x450"            :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "720x450d60"         :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "680x384"            :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "680x384d60"         :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "680x384d60_0"       :  680 x  384 @  59.8 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x512"            :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x512d75"         :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): --- End of ModePool for CRT-0: ---
[    13.209] (II) NVIDIA(0): 
[    13.209] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    13.209] (WW) NVIDIA(0): No valid modes for "1600x900"; removing.
[    13.209] (WW) NVIDIA(0): 
[    13.209] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    13.209] (WW) NVIDIA(0):     "nvidia-auto-select".
[    13.209] (WW) NVIDIA(0): 
[    13.209] (II) NVIDIA(0): Validated modes:
[    13.209] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    13.210] (II) NVIDIA(0): 
[    13.210] (II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
[    13.210] (II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
[    13.210] (II) NVIDIA(0): 
[    13.210] (II) NVIDIA(0): "1024x768_70"  : 1024 x  768 @  70.1 Hz 
[    13.210] (II) NVIDIA(0): "1024x768_60"  : 1024 x  768 @  60.0 Hz 
[    13.210] (II) NVIDIA(0): "960x600"      :  960 x  600 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "960x540"      :  960 x  540 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "840x525"      :  840 x  525 @  69.9 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "840x525d60"   :  840 x  525 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "840x525d60_0" :  840 x  525 @  59.9 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "832x624"      :  832 x  624 @  74.6 Hz 
[    13.210] (II) NVIDIA(0): "800x600"      :  800 x  600 @  65.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "800x600d60"   :  800 x  600 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "800x600_75"   :  800 x  600 @  75.0 Hz 
[    13.210] (II) NVIDIA(0): "800x600_72"   :  800 x  600 @  72.2 Hz 
[    13.210] (II) NVIDIA(0): "800x600_60"   :  800 x  600 @  60.3 Hz 
[    13.210] (II) NVIDIA(0): "800x600_56"   :  800 x  600 @  56.2 Hz 
[    13.210] (II) NVIDIA(0): "800x512"      :  800 x  512 @  60.2 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "720x450"      :  720 x  450 @  59.9 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "680x384"      :  680 x  384 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "680x384d60_0" :  680 x  384 @  59.8 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "640x512"      :  640 x  512 @  75.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "640x512d60"   :  640 x  512 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "640x480"      :  640 x  480 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "640x480_75"   :  640 x  480 @  75.0 Hz 
[    13.210] (II) NVIDIA(0): "640x480_73"   :  640 x  480 @  72.8 Hz 
[    13.210] (II) NVIDIA(0): "640x480_60"   :  640 x  480 @  59.9 Hz 
[    13.210] (II) NVIDIA(0): "576x432"      :  576 x  432 @  75.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "576x432d75_0" :  576 x  432 @  75.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "576x432d70"   :  576 x  432 @  70.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "576x432d60"   :  576 x  432 @  60.1 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "512x384"      :  512 x  384 @  75.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "512x384d70"   :  512 x  384 @  70.1 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "512x384d60"   :  512 x  384 @  60.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "416x312"      :  416 x  312 @  74.7 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "400x300"      :  400 x  300 @  75.1 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "400x300d72"   :  400 x  300 @  72.2 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "400x300d60"   :  400 x  300 @  60.3 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "400x300d56"   :  400 x  300 @  56.3 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "320x240"      :  320 x  240 @  75.0 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "320x240d73"   :  320 x  240 @  72.8 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): "320x240d60"   :  320 x  240 @  60.1 Hz DoubleScan 
[    13.210] (II) NVIDIA(0): 
[    13.210] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    13.210] (WW) NVIDIA(0):     from CRT-0's EDID.
[    13.210] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    13.211] (--) Depth 24 pixmap format is 32 bpp
[    13.214] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    13.293] (II) Loading extension NV-GLX
[    13.316] (==) NVIDIA(0): Disabling shared memory pixmaps
[    13.316] (==) NVIDIA(0): Backing store disabled
[    13.316] (==) NVIDIA(0): Silken mouse enabled
[    13.316] (**) NVIDIA(0): DPMS enabled
[    13.316] (II) Loading extension NV-CONTROL
[    13.317] (II) Loading extension XINERAMA
[    13.317] (II) Loading sub module "dri2"
[    13.317] (II) LoadModule: "dri2"
[    13.317] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.317] (II) Module dri2: vendor="X.Org Foundation"
[    13.317] 	compiled for 1.10.1, module version = 1.2.0
[    13.317] 	ABI class: X.Org Server Extension, version 5.0
[    13.317] (II) NVIDIA(0): [DRI2] Setup complete
[    13.317] (==) RandR enabled
[    13.317] (II) Initializing built-in extension Generic Event Extension
[    13.317] (II) Initializing built-in extension SHAPE
[    13.317] (II) Initializing built-in extension MIT-SHM
[    13.317] (II) Initializing built-in extension XInputExtension
[    13.317] (II) Initializing built-in extension XTEST
[    13.317] (II) Initializing built-in extension BIG-REQUESTS
[    13.317] (II) Initializing built-in extension SYNC
[    13.317] (II) Initializing built-in extension XKEYBOARD
[    13.317] (II) Initializing built-in extension XC-MISC
[    13.317] (II) Initializing built-in extension SECURITY
[    13.317] (II) Initializing built-in extension XINERAMA
[    13.317] (II) Initializing built-in extension XFIXES
[    13.317] (II) Initializing built-in extension RENDER
[    13.317] (II) Initializing built-in extension RANDR
[    13.317] (II) Initializing built-in extension COMPOSITE
[    13.317] (II) Initializing built-in extension DAMAGE
[    13.317] (II) Initializing built-in extension GESTURE
[    13.319] (II) Initializing extension GLX
[    13.357] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.363] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    13.363] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.363] (II) LoadModule: "evdev"
[    13.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.364] (II) Module evdev: vendor="X.Org Foundation"
[    13.364] 	compiled for 1.10.0.902, module version = 2.6.0
[    13.364] 	Module class: X.Org XInput Driver
[    13.364] 	ABI class: X.Org XInput driver, version 12.3
[    13.364] (II) Using input driver 'evdev' for 'Power Button'
[    13.364] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.364] (**) Power Button: always reports core events
[    13.364] (**) Power Button: Device: "/dev/input/event1"
[    13.364] (--) Power Button: Found keys
[    13.364] (II) Power Button: Configuring as keyboard
[    13.364] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    13.364] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.364] (**) Option "xkb_rules" "evdev"
[    13.364] (**) Option "xkb_model" "pc105"
[    13.364] (**) Option "xkb_layout" "us"
[    13.366] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    13.366] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.366] (II) Using input driver 'evdev' for 'Power Button'
[    13.366] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.366] (**) Power Button: always reports core events
[    13.366] (**) Power Button: Device: "/dev/input/event0"
[    13.366] (--) Power Button: Found keys
[    13.366] (II) Power Button: Configuring as keyboard
[    13.366] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    13.366] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.366] (**) Option "xkb_rules" "evdev"
[    13.366] (**) Option "xkb_model" "pc105"
[    13.366] (**) Option "xkb_layout" "us"
[    13.368] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event4)
[    13.368] (II) No input driver/identifier specified (ignoring)
[    13.370] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    13.370] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.370] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    13.370] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.370] (**) AT Translated Set 2 keyboard: always reports core events
[    13.370] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    13.370] (--) AT Translated Set 2 keyboard: Found keys
[    13.370] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.370] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    13.370] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.370] (**) Option "xkb_rules" "evdev"
[    13.370] (**) Option "xkb_model" "pc105"
[    13.370] (**) Option "xkb_layout" "us"
[    13.371] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event3)
[    13.371] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    13.371] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    13.371] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.371] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    13.371] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event3"
[    13.371] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    13.371] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    13.371] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    13.371] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    13.371] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    13.371] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    13.371] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    13.371] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.371] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[    13.371] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    13.371] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    13.371] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    13.371] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    13.371] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    13.371] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    13.371] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    13.371] (II) No input driver/identifier specified (ignoring)
[   329.118] (II) NVIDIA(0): Setting mode "CRT-0:1600x1024@1600x1024+0+0"
[   344.310] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[   362.742] (II) NVIDIA(0): Setting mode "CRT-0:1440x900@1440x900+0+0"
```

---

### Post by CatKiller on 2011-07-31
See? Opaque. Grrr...

```

[    13.208] (II) NVIDIA(0): --- Modes in ModePool for CRT-0 ---
[    13.208] (II) NVIDIA(0): "nvidia-auto-select" : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1920x1200"          : 1920 x 1200 @  60.0 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1920x1200_60"       : 1920 x 1200 @  60.0 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1920x1080"          : 1920 x 1080 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1920x1080_60"       : 1920 x 1080 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050"          : 1680 x 1050 @  69.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050_70"       : 1680 x 1050 @  69.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050_60"       : 1680 x 1050 @  60.0 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1680x1050_60_0"     : 1680 x 1050 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1600x1200"          : 1600 x 1200 @  65.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1600x1200_65"       : 1600 x 1200 @  65.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1600x1200_60"       : 1600 x 1200 @  60.0 Hz  (from: X Server, VESA)
[    13.208] (II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.2 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1600x1024_60"       : 1600 x 1024 @  60.2 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1440x900"           : 1440 x  900 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  59.9 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  74.8 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1400x1050_75"       : 1400 x 1050 @  74.8 Hz  (from: X Server)
[    13.208] (II) NVIDIA(0): "1400x1050_70"       : 1400 x 1050 @  70.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1400x1050_60"       : 1400 x 1050 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x1024_75"       : 1280 x 1024 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1152x864"           : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1152x864_75"        : 1152 x  864 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1152x864_75_0"      : 1152 x  864 @  75.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1152x864_70"        : 1152 x  864 @  70.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1152x864_60"        : 1152 x  864 @  60.0 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "1024x768"           : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1024x768_75"        : 1024 x  768 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1024x768_70"        : 1024 x  768 @  70.1 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "960x600"            :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "960x600d60"         :  960 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "960x540"            :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "960x540d60"         :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525"            :  840 x  525 @  69.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525d70"         :  840 x  525 @  69.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "840x525d60_0"       :  840 x  525 @  59.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "832x624"            :  832 x  624 @  74.6 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "832x624_75"         :  832 x  624 @  74.6 Hz  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600"            :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600d65"         :  800 x  600 @  65.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600d60"         :  800 x  600 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x600_75"         :  800 x  600 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x600_72"         :  800 x  600 @  72.2 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "800x512"            :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "720x450"            :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "720x450d60"         :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "680x384"            :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "680x384d60"         :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "680x384d60_0"       :  680 x  384 @  59.8 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x512"            :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x512d75"         :  640 x  512 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "640x480_75"         :  640 x  480 @  75.0 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "640x480_73"         :  640 x  480 @  72.8 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
[    13.209] (II) NVIDIA(0): "576x432"            :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d75"         :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d75_0"       :  576 x  432 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d70"         :  576 x  432 @  70.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384"            :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384d75"         :  512 x  384 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384d70"         :  512 x  384 @  70.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "416x312"            :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "416x312d75"         :  416 x  312 @  74.7 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300"            :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d75"         :  400 x  300 @  75.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d72"         :  400 x  300 @  72.2 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240"            :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240d75"         :  320 x  240 @  75.0 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240d73"         :  320 x  240 @  72.8 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
[    13.209] (II) NVIDIA(0): --- End of ModePool for CRT-0: ---
...
[    13.209] (WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
[    13.209] (WW) NVIDIA(0):     "nvidia-auto-select".

```It knows they're valid and then NVidia's driver discards them out of hand. Irritating. At least it adds some of them back later for reasons of its own. Don't know why it didn't try 16x9, though. It's obviously not a VESA mode of your graphics card, but X should have had a stab.

EDIT:

OK, despite the fact that I don't like them, let's try adding a mode in again. Add this to the Monitor Section of your xorg.conf.

```
Modeline "1600x900@60"     120.42  1600 1632 2088 2120    900  918  927  946 +hsync +vsync
```(timings taken from the Windows "driver" for your monitor)
You can probably comment out the Mode line from the Screen Section.

---

### Post by realzippy on 2011-07-31
@ arun.manuel14
 Note catkiller edited post above suggesting modeline...
 
 

@ catkiller
  does the Windows "driver" include the whole EDID ?

  Edit.
  Just unpacked the windows driver...no whole edid, but that modeline.



  

  

I am out,around midnight here.Back tomorrow,have fun..

---

### Post by arun.manuel14 on 2011-07-31
> **realzippy said:**
> @ arun.manuel14
 Note catkiller edited post above suggesting modeline...
 
 

@ catkiller
  does the Windows "driver" include the whole EDID ?



  

  

I am out,around midnight here.Back tomorrow,have fun..



I'm not sure what i'm supposed to do with the code CatKiller provided me with! I copied and pasted it in the terminal and got this !

```
arun@ubuntu:~$ Modeline "1600x900@60"     120.42  1600 1632 2088 2120    900  918  927  946 +hsync +vsync
Modeline: command not found
arun@ubuntu:~$ 

```

---

### Post by realzippy on 2011-08-01
Like this,in the monitor section:


```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"            
    Modeline "1600x900"     120.42  1600 1632 2088 2120    900  918  927  946 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
     Option        "ModeDebug"            "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"


    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes        "1600x900"
    EndSubSection
EndSection
```

---

### Post by BicyclerBoy on 2011-08-01
Might be better to use the name
Modeline "1600x900_60.00"to avoid the "@" symbol & be unique.
You need to use the full mode name in the screen section (unlike xrandr)..
Modes  "1600x900_60.00"


To stop EDID video mode validation.. 
    Option         "UseEDID" "FALSE"

Modeline "1600x900_75.00"  151.25  1600 1704 1872 2144  900 903 908 942 -hsync +vsync
Modeline "1600x900_72.00"  145.00  1600 1704 1872 2144  900 903 908 941 -hsync +vsync
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync

---

### Post by realzippy on 2011-08-01
Edited suggested xorg.conf:

deleted "@60" from modeline.

BTW,don't think this might be a problem,....Catkiller?

---

### Post by realzippy on 2011-08-01
> **BicyclerBoy said:**
> 

To stop EDID video mode validation.. 
    Option         "UseEDID" "FALSE"



..not exactly.To stop mode validation totally it was:
Option      "UseEDID" "false"
Option      "ModeValidation" "NoDFPNativeResolutionCheck,NoVirtualSizeCheck,NoMaxPClkCheck,NoHorizSyncCheck,NoVertRefreshCheck,NoWidthAlignmentCheck,NoExtendedGpuCapabilitiesCheck"


source:
[http://en.gentoo-wiki.com/wiki/Nvidia_HDTV](http://en.gentoo-wiki.com/wiki/Nvidia_HDTV)

---

### Post by realzippy on 2011-08-01
Arun might be pretty confused now.
So I suggest a version of xorg.conf, 
hoping catkiller & bicyclerboy agree:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"            
    Modeline "1600x900_60"     120.42  1600 1632 2088 2120    900  918  927  946 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option        "ModeDebug"            "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
    #Option      "UseEDID" "False"
    #Option      "ModeValidation" "NoDFPNativeResolutionCheck,NoVirtualSizeCheck,NoMaxPClkCheck,NoHorizSyncCheck,NoVertRefreshCheck,NoWidthAlignmentCheck,NoExtendedGpuCapabilitiesCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes        "1600x900_60"
    EndSubSection
EndSection
```

---

### Post by CatKiller on 2011-08-01
> **realzippy said:**
> BTW,don't think this might be a problem,....Catkiller?

No, I don't think it matters.

---

### Post by realzippy on 2011-08-01
@catkiller
You agree to suggested xorg.conf in post #50 ?

---

### Post by CatKiller on 2011-08-01
> **realzippy said:**
> ..not exactly.To stop mode validation totally it was:
Option      "UseEDID" "false"
Option      "ModeValidation" "NoDFPNativeResolutionCheck,NoVirtualSizeCheck,NoMaxPClkCheck,NoHorizSyncCheck,NoVertRefreshCheck,NoWidthAlignmentCheck,NoExtendedGpuCapabilitiesCheck"

UseEDID is used to tell X to use or not use EDID as a source of information. In this case, there is no EDID, so it won't make any difference either way. If the EDID existed but was not accurate, as was the case with my old monitor, this would be useful. But it doesn't.

We want X to do mode validation. We don't want to break the OP's monitor, after all. If we get confirmation in the logs that X has tried the mode and rejected it for a spurious reason, then we can start disabling checks. Until then, they ought to stay in.

At the moment, X is checking the modes that it gets through VESA from the graphics cards and its own internal modes. The results of the checks are all sane based on the information we've specified. It's just that the mode that the OP wants hasn't been checked yet, which is why we've specified it more forcefully than before. With a bit of luck, X will test the mode, find it valid, and pass it on to the NVidia driver to do its own secret mojo to.

Fingers crossed.

---

### Post by realzippy on 2011-08-01
Ok,so I outcommended both in suggested file.

Although the [gentoo guys say]("http://en.gentoo-wiki.com/wiki/Nvidia_HDTV"):

> Warning: In order for the Nvidia binary driver to use custom modelines, you need to disable EDID *and* mode validation.

---

### Post by CatKiller on 2011-08-01
FWIW, I've found out why the driver rejected valid modes over 1024x768: it's a fairly arbitrary sanity check for when there's no EDID. From the driver documentation:

> If the EDID did not provide any detailed timings (or there was no EDID at all), the best valid mode not larger than 1024x768 is used as the "nvidia-auto-select" mode. The 1024x768 limit is imposed here to restrict use of modes that may have been validated, but may be too large to be considered a reasonable default, such as 2048x1536.

Since it still used higher modes later in the process, I don't think this is particularly a problem.

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> Arun might be pretty confused now.
So I suggest a version of xorg.conf, 
hoping catkiller & bicyclerboy agree:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"            
    Modeline "1600x900_60"     120.42  1600 1632 2088 2120    900  918  927  946 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option        "ModeDebug"            "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
    #Option      "UseEDID" "False"
    #Option      "ModeValidation" "NoDFPNativeResolutionCheck,NoVirtualSizeCheck,NoMaxPClkCheck,NoHorizSyncCheck,NoVertRefreshCheck,NoWidthAlignmentCheck,NoExtendedGpuCapabilitiesCheck"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes        "1600x900_60"
    EndSubSection
EndSection
```

Ummm , yeah Im confused ! I think you guys are forgetting that im a n00b and i dont actually understand the technical aspects of this yet . 

So should i change my whole xorg.conf to the one that realzippy posted in #50?(the one quoted)

---

### Post by realzippy on 2011-08-01
Yes.Whole xorg.conf...
And don't worry,we just try to help you.This (your issue) is quite interesting,at least to me.

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> Yes.Whole xorg.conf...
And don't worry,we just try to help you.This (your issue) is quite interesting,at least to me.

I changed my whole xorg.conf to what you asked me to .

It logged in with 1360x768 (previously 1024x768 )
But Nvidia Xserver still isn't giving me an option of 1600x900

BUT , xrandr reports 1600x900 as maximum.
xrandr report -

```
arun@ubuntu:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1600 x 900
default connected 1440x900+0+0 0mm x 0mm
   1600x900       50.0  
   1024x768       51.0     59.0     60.0  
   1440x900       52.0* 
   1360x768       53.0     54.0  
   1152x864       55.0     56.0     57.0     58.0  
   960x600        61.0  
   960x540        62.0  
   840x525        63.0     64.0     65.0  
   832x624        66.0  
   800x600        67.0     68.0     69.0     70.0     71.0     72.0  
   800x512        73.0  
   720x450        74.0  
   680x384        75.0     76.0  
   640x512        77.0     78.0  
   640x480        79.0     80.0     81.0     82.0  
   576x432        83.0     84.0     85.0     86.0  
   512x384        87.0     88.0     89.0  
   416x312        90.0  
   400x300        91.0     92.0     93.0     94.0  
   320x240        95.0     96.0     97.0  
arun@ubuntu:~$ 

```

---

### Post by realzippy on 2011-08-01
what happens when you now run:

```
xrandr -s 1600x900
```

?

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> what happens when you now run:

```
xrandr -s 1600x900
```

?

It worked!!!
its at 1600x900

But there's something wrong , screen seems diff , varying depths in colours (i cant describe it , its like the black is darker in some letters and in others its a little lighter)

Could it be the refresh rate?
My monitor recommends 60hz for 1600x900

---

### Post by realzippy on 2011-08-01
nvidia-settings does not have the 1600x900 resolution?

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> nvidia-settings does not have the 1600x900 resolution?

Yes , Nvidia setting has 1600x900 now . But the problem that i mentioned still persists .

---

### Post by realzippy on 2011-08-01
So there is no difference when setting 1600x900 with nvidia-settings?

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> So there is no difference when setting 1600x900 with nvidia-settings?


After i ran the code , my screen resolution changed to 1600x900 
Its running at 1600x900 right now and nvidia xserver does show 1600x900 as an option now. But the colors seem a little off .



**EDIT:** I switched back to 1440x900 to make sure i wasn't imagining it , at 1440x900 the quality of display is much better than at 1600x900


**EDIT:** I manually checked the info that the monitor gives (using hard keys on the side of the monitor)

 @1440x900
    
       "
         Analog
        55.8kHz 60HZ NP
        1440x900
       "

  @1600x900

       "
         Analog
         56.8kHz 60 Hz pp
       "
    (doesn't mention what resolution im running at )

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> It worked!!!
its at 1600x900

Yay!

> 
But there's something wrong , screen seems diff , varying depths in colours (i cant describe it , its like the black is darker in some letters and in others its a little lighter)

Sub-pixel font rendering is probably something for a different thread :)
> 
Could it be the refresh rate?
My monitor recommends 60hz for 1600x900

You're running at 60Hz, even though it says you're running at 50Hz. There is a reason, but it's terribly dull. I can tell you how to make it report accurately if you like, but you've probably had enough of editing xorg.conf for now. You'll get the correct number from NVidia's tools, if you want to check, or your monitor probably has some kind of information screen that will tell you what you're running at.

---

### Post by arun.manuel14 on 2011-08-01
> **CatKiller said:**
> Yay!


if you want to check, or your monitor probably has some kind of information screen that will tell you what you're running at.

I did , i edited my previous post , please read that.

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> **EDIT:** I switched back to 1440x900 to make sure i wasn't imagining it , at 1440x900 the quality of display is much better than at 1600x900

It's possible that you've got used to the soft-focus effect of running the monitor at a non-native resolution. As something to try, though, you could comment out the ModeLine I gave you and try using the timings that realzippy gave you way back in post 14. Same format as the one that worked, but with the other numbers. We can also try telling X the dimensions of your monitor so that it can calculate the correct DPI for the monitor. That would probably have some effect, too.

---

### Post by arun.manuel14 on 2011-08-01
> **CatKiller said:**
> It's possible that you've got used to the soft-focus effect of running the monitor at a non-native resolution. As something to try, though, you could comment out the ModeLine I gave you and try using the timings that realzippy gave you way back in post 14. Same format as the one that worked, but with the other numbers. We can also try telling X the dimensions of your monitor so that it can calculate the correct DPI for the monitor. That would probably have some effect, too.

I'm sure something's wrong at 1600x900 , because I used that resolution on windows for ages.

I'll give your way a go , so the codes should look 

```
xrandr --newmode "1600x900_60.00"  120.42  1600 1632 2088 2120    900  918  927  946 +hsync +vsync
```


```
xrandr --addmode default "1600x900_60.00"
```

```
xrandr -s 1600x900_60
```


like this , right?

---

### Post by CatKiller on 2011-08-01
To tell X the size of your monitor, it's

```
    DisplaySize    442.8 249.075
``` in the Monitor Section
(numbers from your monitor's manual; if they don't seem right, the first number is the display width in mm, the second is the display height)

[EDIT](443 and 249 are probably sufficient)[/EDIT]

The new Modeline to try, by my reckoning, is 

```
Modeline "1600x900@60"     118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> 
like this , right?

No, in xorg.conf. My previous post should show what it should look like.

---

### Post by CatKiller on 2011-08-01
If you want the driver not to lie about the refresh rate, you can put ```
Option "DynamicTwinView" "False"
``` in either the Device Section or the Screen Section.

This is what it does.

> Option "DynamicTwinView" "boolean"

Enable or disable support for dynamically configuring TwinView on this X screen. When DynamicTwinView is enabled (the default), the refresh rate of a mode (reported through XF86VidMode or XRandR) does not correctly report the refresh rate, but instead is a unique number such that each MetaMode has a different value. This is to guarantee that MetaModes can be uniquely identified by XRandR.
 
When DynamicTwinView is disabled, the refresh rate reported through XRandR will be accurate, but NV-CONTROL clients such as nvidia-settings will not be able to dynamically manipulate the X screen's MetaModes. TwinView can still be configured from the X config file when DynamicTwinView is disabled.
 
Default: DynamicTwinView is enabled.

---

### Post by realzippy on 2011-08-01
To summarise,it would be:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    DisplaySize    443 249
    Option         "DPMS"            
    Modeline "1600x900_60"     118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    Option        "ModeDebug"            "True"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
        Modes        "1600x900_60"
    EndSubSection
EndSection
```

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> To summarise,it would be:



I think it worked! The screen seems to be normal now , i logged in with 1360x768

I tried using nvidia xserver but it said its been disabled(cuz of disabled twinview im assuming)

so i used 
```
xrandr -s 1600x900
```

Now its working fine , BUT my monitor info says its running at 1440x900 :confused: 


but xrandr reports
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   1600x900       60.0* 
   1024x768       75.0     70.0     60.0  
   1440x900       60.0  
   1360x768       60.0  
   1152x864       75.0     70.0     60.0  
   960x600        60.0  
   960x540        60.0  
   840x525        70.0     60.0  
   832x624        75.0  
   800x600        65.0     60.0     75.0     72.0     56.0  
   800x512        60.0  
   720x450        60.0  
   680x384        60.0  
   640x512        75.0     60.0  
   640x480        60.0     75.0     73.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   320x240        75.0     73.0     60.0  
arun@ubuntu:~$ 

```


So i guess i'm good to go right?

---

### Post by realzippy on 2011-08-01
Wait,
you cannot run nvidia-settings?
Start it from terminal,and post output.

```
nvidia-settings

```

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> Wait,

Start it from terminal,and post output.


I ran the code , nvidia settings open but i cant change Xserver display configuration , it says 

 'Unable to load X Server Display Configuration page:

nvidia-settings currently does not support scanout screens (0) that have dynamic twinview disabled. "

code results

```
arun@ubuntu:~$ nvidia-settings

ERROR: Cannot open display 'ubuntu:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/arun/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 36 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 37 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 38 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 39 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 40 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 41 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 42 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 43 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 44 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 45 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 46 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       47 of configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       48 of configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of
       configuration file '/home/arun/.nvidia-settings-rc' (no Display
       connection).

arun@ubuntu:~$ 

```

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> my monitor info says its running at 1440x900 :confused: 

If your monitor thinks that it's running at 1440x900 then it probably is, unless you can definitely spot the extra 160 pixels.

You probably don't also need to specify the mode in the Screen section when you've specified the modeline in the Monitor section, btw. You can probably comment that out if you're feeling tidy.

> **realzippy said:**
> Wait,
you cannot run nvidia-settings?

Yeah, the whole made-up-refresh-rate thing is a horrible hack. NVidia don't think that they can uniquely specify names for all the mode combinations with multiple monitors unless they lie about the refresh rates, so their tools complain if you don't let them do this. They could just stick numbers on the end like everyone else does...

The OP can probably comment that out for now, too, while we're still troubleshooting.

---

### Post by realzippy on 2011-08-01
...then eliminate the twinview stuff  (it is only there to prevent xrandr from lying)..put a # in front of :

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Option "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
        Modes        "1600x900_60"
    EndSubSection
EndSection
```

---

### Post by CatKiller on 2011-08-01
The other bit that I was talking about would make it look like this
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option "DynamicTwinView" "False"
    SubSection     "Display"
        Depth       24
#        Modes        "1600x900_60"
    EndSubSection
EndSection
```

EDIT: Just so that you know what people are talking about, coders will often want to put descriptions or comments about what a particular piece of code or configuration does ("this is the part that flanges the McGuffin," or similar), and you won't want the computer to actually do anything with those bits, so most syntaxes have a way of telling the computer to ignore the rest of the line after a particular symbol since it's a comment for humans not machines. Which means that you can tell the computer to ignore an option by telling it that that option is actually a comment - hence "commenting out". This symbol is often #, although it can be something else with scripts and so on.

It's useful to comment out lines rather than deleting them in case you find out later that you needed the line after all. You don't need to remember exactly what it was, you just remove the comment symbol. It's the same with files; it's often best to rename them to something else rather than deleting them in case you've done something really bad.

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> ...then eliminate the twinview stuff  (it is only there to prevent xrandr from lying)..put a # in front of :



Did that! I think now its working fine . I can access xserver setting and xrandr reports 1600x900 resolution!

Everytime i log in it goes back to 1360x768 , how do i make it permanent?


**EDIT:**> **CatKiller said:**
> The other bit that I was talking about would make it look like ...

I did that too.

---

### Post by realzippy on 2011-08-01
Run 
nvidia-settings
set your 1600x900,hit "apply",then hit:
"SaveToXConfigurationFile"

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> Run 
nvidia-settings
set your 1600x900,hit "apply",then hit:
"SaveToXConfigurationFile"

Didn't work .

---

### Post by realzippy on 2011-08-01
??
But 
```
xrandr -s 1600x900 
```
does work (only for running session)?

So add this command to
System==>Preferences==>StartupApplications

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> Everytime i log in it goes back to 1360x768 , how do i make it permanent?

It's possible that ```
mv ~/.config/monitors.xml ~/.config/monitors.xml.old
``` will help. This is the file that contains a user's preferred resolution. It's possible that it's got stuck. FWIW, you can edit this file by hand - it's pretty straightforward.

Otherwise we can trawl through the logs again and see if there's a reason why it's picking that resolution rather than a better one.

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> ??
But 
```
xrandr -s 1600x900 
```
does work (only for running session)?

So add this command to
System==>Preferences==>StartupApplications

I tried what realzippy asked me to do , it worked!
So i guess there's no need to to run the code that catkiller provided right?

---

### Post by realzippy on 2011-08-01
No,catkiller is right (again).

If monitors.xml exists,and you delete (or rename) it,you might
not need the StartupApplications command I suggested.
Run

```
locate monitors.xml
```


If exists,you should run catkiller's code,and then you could
delete the created startup command "xrandr -s"
It's cleaner.  ;-)

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> I tried what realzippy asked me to do , it worked!

It's not a nice solution, but it is a solution. If you've got everything how you want it, then you don't *need* to tweak it any more. Your call, really :)

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> No,catkiller is right (again).

If monitors.xml exists,and you delete (or rename) it,you might
not need the StartupApplications command I suggested.
Run

```
locate monitors.xml
```


If exists,you should run catkiller's code,and then you could
delete the created startup command "xrandr -s"
It's cleaner.  ;-)

I ran catkiller's code

this is what i got```
arun@ubuntu:~$ mv ~/.config/monitors.xml ~/.config/monitors.xml.old
mv: cannot stat `/home/arun/.config/monitors.xml': No such file or directory
arun@ubuntu:~$ locate monitors.xml
/home/arun/.config/monitors.xml
arun@ubuntu:~$ 


```

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> this is what i got

OK, that's flat-out weird. Would explain why your resolution setting wasn't taking effect, though.

Two approaches; you can see what happens if you try to rename that file in the file manager (.config is in your Home folder and hidden by default, Ctrl-H will show it) or you can brute-force it by sticking *sudo* in front of the move command.

---

### Post by realzippy on 2011-08-01
> **CatKiller said:**
> OK, that's flat-out weird. Would explain why your resolution setting wasn't taking effect, though.

Two approaches; you can see what happens if you try to rename that file in the file manager (.config is in your Home folder and hidden by default, Ctrl-H will show it) or you can brute-force it by sticking *sudo* in front of the move command.

Arrgh.Can reproduce this.
But it is a lie,since
```
mv ~/.config/monitors.xml ~/.config/monitors.xml.old
```
definitely works.
WTF?
Why doesn't
```
locate monitors.xml.old
```
then show me the file ??????

@OP
Catkillers command works.
You could now try to disable the Autostart command...

---

### Post by arun.manuel14 on 2011-08-01
> **CatKiller said:**
> OK, that's flat-out weird. Would explain why your resolution setting wasn't taking effect, though.

Two approaches; you can see what happens if you try to rename that file in the file manager (.config is in your Home folder and hidden by default, Ctrl-H will show it) or you can brute-force it by sticking *sudo* in front of the move command.

Went with brute force, didnt seem to work

```
arun@ubuntu:~$ sudo mv ~/.config/monitors.xml ~/.config/monitors.xml.old
[sudo] password for arun: 
mv: cannot stat `/home/arun/.config/monitors.xml': No such file or directory
arun@ubuntu:~$ 

```

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> 

@OP
Catkillers command works.
You could now try to disable the Autostart command...

I deleted the autostart command . CatKiller's method worked , 
It logged in with 1600x900!!

YAY i think its fixed now! :)

---

### Post by CatKiller on 2011-08-01
> **realzippy said:**
> Why doesn't
```
locate monitors.xml.old
```then show me the file ??????

Locate scans through a database of the locations of files rather than through the files themselves (it's significantly quicker and doesn't hammer the hard drive). Newly created files aren't in the database yet; I think it gets updated on login and at regular intervals. You can do it manually with
```
sudo updatedb
```*locate monitors.xml.old* should return results then.

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> I deleted the autostart command . CatKiller's method worked , 
It logged in with 1600x900!!

YAY i think its fixed now! :)

Sweet!

Don't forget to mark the thread as Solved, so that other people with similar problems can know that a solution lies somewhere in this epic thread :)

---

### Post by arun.manuel14 on 2011-08-01
> **CatKiller said:**
> Sweet!

Don't forget to mark the thread as Solved, so that other people with similar problems can know that a solution lies somewhere in this epic thread :)

Haha , truly epic!

Thanks for your help @ CatKiller and realzippy :)

Before I go off , can you suggest me where I can learn stuff about ubuntu ? I just have one day's experience (hopefully one of many) and would love to learn more!

---

### Post by realzippy on 2011-08-01
> **CatKiller said:**
> ... a solution lies somewhere in this epic thread :)

 :D  Hint :
Solution was adding the modeline and deleting/renaming monitors.xml....
I am not sure about the "Display size".....?
Anyway,
great job Catkiller!
Thanks for your patience arun.manuel14...most ubuntu beginners would have run away.

---

### Post by arun.manuel14 on 2011-08-01
> **realzippy said:**
> :D  Hint :
Solution was adding the modeline and deleting/renaming monitors.xml....
I am not sure about the "Display size".....?
Anyway,
great job Catkiller!
Thanks for your patience arun.manuel14...most ubuntu beginners would have run away.


Thank you! I actually did run away , I tried ubuntu 4 years ago couldnt get used to it and switched back to windows , But of course back then I didnt know about ubuntuforums!

---

### Post by CatKiller on 2011-08-01
> **arun.manuel14 said:**
> Before I go off , can you suggest me where I can learn stuff about ubuntu ?

In my experience, things like this are best. You have a problem to solve or an itch to scratch and dive in. Your research ends up going in all sorts of directions and you end up with a bunch of stuff in your head that's bound to come in handy sooner-or-later. Before too long, you've managed to fill in the gaps and suddenly it all makes some kind of sense.

It doesn't have to be your problem, though. There's a new one here every couple of minutes. Trying to help someone else encourages you to dig that little bit deeper.

For the most part, books and websites and so on either assume too much or are really limited. Or out of date. Hands-on is best. Learn how to back things up so that you don't have to worry about taking the nuclear option and then keep poking your computer till it tells you what you need to know :)

You can read about what a particular command does with **man *command*** and there will often be more documentation for a particular package as a README somewhere in /usr/doc.

Most of all, don't be scared and have fun!

---

### Post by arun.manuel14 on 2011-08-01
> **CatKiller said:**
> 

Most of all, don't be scared and have fun!
Will do and thanks!

---

### Post by CatKiller on 2011-08-01
> **realzippy said:**
> I am not sure about the "Display size".....?

If I had to guess (not having seen the symptoms), the modeline may have corrected timing-related colour problems for the display as a whole. Setting the DisplaySize (and therefore reporting a correct DPI to anything that asks) may have corrected text-specific display problems.

---

