---
title: "No OpenGL after 10.04 upgrade?"
date: 2010-05-01
forum: Multimedia Software
---

### Post by kbaum on 2010-05-01
I just upgraded to 10.04 on my Dell optiplex GX280 and now OpenGL isn't working (xbmc and cairo dock won't start).

Here are the (i think) relevant lines from lspci:

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation 82915G Integrated Graphics Controller (rev 04)

What should I do?

---

### Post by AKADAP on 2010-05-01
Thank you for the clue.
Neither google earth, nor mythTV were working for me, and I did not know why.
You mentioned OpenGL not working, and I realized both were using openGL.
MythTV allows me to change the render, so I changed it to something other than openGL, and it no longer caused a segmentation fault.
Now I need to add an update to my bug report...

I'm using an ATI video card, so this problem is not specific to the video driver.

---

### Post by sismo on 2010-05-02
Hi guys, same here:

When I try to use my XBMC I got a pop-up windows claiming:

XBMC needs hardware accelerated OpenGL rendering.  Install an appropriate graphics driver.

Please consult XBMC Wiki for supported hardware [http://xbmc.org/wiki/?title=Supported_hardware](http://xbmc.org/wiki/?title=Supported_hardware)

I hit ctrl-c before clicking OK on the pop-up and obtain:

Traceback (most recent call last):
  File "/usr/share/xbmc/FEH.py", line 170, in <module>
    error("XBMC needs hardware accelerated OpenGL rendering.\nInstall an appropriate graphics driver.\n\nPlease consult XBMC Wiki for supported hardware\nhttp://xbmc.org/wiki/?title=Supported_hardware")
  File "/usr/share/xbmc/FEH.py", line 29, in error
    createQt(errorLine)
  File "/usr/share/xbmc/FEH.py", line 63, in createQt
    app.exec_loop()


also I did a dmesg and got:
[ 3842.552941] glxinfo[3403]: segfault at 4 ip 001c5ef6 sp bffed5e0 error 4 in libGL.so.1.2[160000+a7000]

Hopefully someone can figure it out, because it looks like it's related to the opengl.

Thanks
Regards

---

### Post by poo_22 on 2010-05-02
same problem. intel graphics. everything worked fine in 9.04

---

### Post by dementur on 2010-05-05
root@shuttle01:~# lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

 Same problem here. I'm not too familiar with the xserver so please do post suggestions and/or what I can run to gather more information.

 Also note, worked fine on my nvidia machine, its just a problem on my shuttle with onboard intel.
nvidia card is (01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1))

---

### Post by sfranky on 2010-05-05
same here...i have an nvidia 7300gt, installed the driver through envy..right after i upgraded my system, x doesn't work..i get a tiny message saying the hardware accelerated opengl thingy..
anyone?!

---

### Post by blz84 on 2010-05-05
Same here :/ 

I updated to 10.04, I did not get window borders - first I thought it is a problem with compiz. Then with ati drivers, I uninstalled all ati drivers, installed the ones from ATI site (10.4),  I get proper resolution now, but no opengl.

When I start fglrxinfo I get errors about a bad request and no info about the video card. Catalyst GUI shows info about drivers, but info about OpenGL is empty...



Help!

---

### Post by blz84 on 2010-05-05
ok, that was quick... I started a system update and now I see openGL in Catalyst menu. I still don`t get windows borders and compiz does not seem to start... I don`t know yet if it is related to OpenGL

---

### Post by dementur on 2010-05-07
..still no love for me. How do I even tell which Xserver is running?

I've gone back to 9.10 for now. Someone let me know when this problem is fixed? Or what information to provide? :\

---

### Post by bionicdude on 2010-05-09
I also have no glx (opengl) after upgrading from 9.10 to 10.04
some info..

```

a@b:/var/log$ uname -a
Linux b 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
a@b:/var/log$ cat Xorg.0.log | grep -i nvidia
(--) PCI:*(0:1:0:0) 10de:0614:19da:3115 nVidia Corporation G92 [GeForce 9800 GT] rev 162, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, 0xf6000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  195.36.15  Fri Mar 12 00:38:50 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) May 09 20:28:05 NVIDIA(0): Enabling RENDER acceleration
(II) May 09 20:28:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 09 20:28:05 NVIDIA(0):     enabled.
(II) May 09 20:28:06 NVIDIA(0): NVIDIA GPU GeForce 9800 GT (G92) at PCI:1:0:0 (GPU-0)
(--) May 09 20:28:06 NVIDIA(0): Memory: 1048576 kBytes
(--) May 09 20:28:06 NVIDIA(0): VideoBIOS: 62.92.89.00.00
(II) May 09 20:28:06 NVIDIA(0): Detected PCI Express Link width: 16X
(--) May 09 20:28:06 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) May 09 20:28:06 NVIDIA(0): Connected display device(s) on GeForce 9800 GT at PCI:1:0:0:
(--) May 09 20:28:06 NVIDIA(0):     ViewSonic VA2213w (CRT-1)
(--) May 09 20:28:06 NVIDIA(0): ViewSonic VA2213w (CRT-1): 400.0 MHz maximum pixel clock
(II) May 09 20:28:06 NVIDIA(0): Assigned Display Device: CRT-1
(==) May 09 20:28:06 NVIDIA(0): 
(==) May 09 20:28:06 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) May 09 20:28:06 NVIDIA(0):     will be used as the requested mode.
(==) May 09 20:28:06 NVIDIA(0): 
(II) May 09 20:28:06 NVIDIA(0): Validated modes:
(II) May 09 20:28:06 NVIDIA(0):     "nvidia-auto-select"
(II) May 09 20:28:06 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) May 09 20:28:06 NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
(--) May 09 20:28:06 NVIDIA(0):     option
(==) May 09 20:28:06 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) May 09 20:28:06 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) May 09 20:28:06 NVIDIA:     access.
(II) May 09 20:28:06 NVIDIA(0): Initialized GPU GART.
(II) May 09 20:28:06 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) May 09 20:28:06 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) May 09 20:28:06 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled

```

---

### Post by mike_perth on 2010-05-10
i'm having this problem too. recently upgraded to 10.04 from 8.04 and it was the worst decision i've ever made with my linux box... for lots of other reasons too. but anyway:

i have a nVidia 7600 GS. worked perfect in 8.04. upgrade to 10.04 w/latest nvidia proprietary drivers, everything very slow in the desktop environment. mythtv unusable without changing the painter to QT from openGL. other openGL apps similarly crippled.

downgraded from nvidia-current (v195 i think) to version 173 via synaptic/"hardware drivers" menu option. i now have "some openGL sometimes". mythtv will open and operate, but closing it causes a white screen that needs an X restart to fix. other openGL apps freeze X on starting (eg glxears). sometimes after restarting X i don't have openGL at all anymore. in such cases i get this from starting mythtv (log file excerpt):

```
X Error: GLXBadDrawable 130
  Extension:    128 (Uknown extension)
  Minor opcode: 5 (Unknown request)
  Resource id:  0x220002f
QGLTempContext: Unable to create GL context.
Unrecognised OpenGL version

```

i can reliably get mythtv to work when it starts up but if i try to close it i'm dead in the water. i have some more testing to do i guess. can anyone tell me how to install the nVidia drivers from the nVidia website in such a way as they are easy to remove? it seems to be a big shell script, i don't like straying from Synaptic if there's no way back cleanly...

the reason i ask is that i wonder if this guy had the same problem:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1468147](http://ohioloco.ubuntuforums.org/showthread.php?t=1468147)

coz when i have no openGL then moving windows around etc is slow (or at least it was with 195).

after i post this i am going to try glxinfo during one of my openGL blackouts (i'm in one now, every five seconds or so i get a screen freeze for one second, and so on... it's infuriating).

---

### Post by mike_perth on 2010-05-10
glxinfo shows an error at the moment but X log file doesn't seem to think anything is wrong...
```

mike@mythbox:~$ glxinfo
name of display: :0.0
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  128 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  26
  Current serial number in output stream:  26
mike@mythbox:~$ cat /var/log/Xorg.0.log | egrep "glx|GLX|idia|7600|openGL|OpenGL"
(--) PCI:*(0:1:0:0) 10de:0392:107d:2a52 nVidia Corporation G73 [GeForce 7600 GS] rev 161, Mem @ 0xf9000000/16777216, 0xd0000000/268435456, 0xf8000000/16777216, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  173.14.22  Sun Nov  8 21:42:44 PST 2009
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(II) Loading extension NV-GLX
(II) Initializing extension GLX
mike@mythbox:~$ 

```

---

### Post by mike_perth on 2010-05-10
BTW i shouldn't have been so hasty above in saying that downgrading nvidia drivers brought some openGL back, i really need to test that properly before shooting my mouth off.

edit: back on 195.36.15 now after experimenting with 195.36.24 (i think) and still have 'some' openGL. glxgears works fine but mythtv is incredibly slow to draw its GUI if i use the openGL painter. likewise XBMC. mythfrontend doesn't give any errors in the log file, nor does XBMC. it's like both apps think openGL is working fine... but in actual fact some part of it is broken. i think it might be something to do with text rendering coz xbmc loads its backgrounds OK until it wants to draw the text in the menu... at which time i'm grinding at about 1 frame per 30 seconds (similar to when i press a navigation key in mythfrontend).

---

### Post by bionicdude on 2010-05-10
well i dropped out to recovery console
init 3 to get to the right level
logged in
sudo ./NVIDIA...(the latest driver from their site)
chose YES when it asked about 32bit compatibility OPENGL stuff
low and behold...I have GLX back

I'm not sure if this will help anyone out there, but thought that i should mention it, just in case it does.

Good luck people..:)

---

### Post by mikeperth on 2010-05-11
> **bionicdude said:**
> well i dropped out to recovery console
init 3 to get to the right level
logged in
sudo ./NVIDIA...(the latest driver from their site)
chose YES when it asked about 32bit compatibility OPENGL stuff
low and behold...I have GLX back
 
I'm not sure if this will help anyone out there, but thought that i should mention it, just in case it does.
 
Good luck people..
 
interesting! thanks dude. what exactly where your symptoms before? your X11 log file you posted was like mine (i.e. no obvious error recorded regarding openGL, unless i'm going blind). So how did you know you had no openGL?
 
i didn't know you needed to drop out to console etc to do the nVidia install. is there an 'official' step-by-step that you followed? i assume you uninstalled the ubuntu nvidia (synaptic) packages before you did the nVidia website script install?
 
thanks
Mike

---

### Post by bionicdude on 2010-05-11
Hey,

I knew that i had an issue for the following reasons:
no compiz
xbmc said it couldn't start because it needed opengl
docky complained that compositing wasn't enabled
glxgears didn't run at all.

To be fair, I don't think that i did uninstall nvidia-current before trying to install the official nvidia binary from their site..i was too anxious to get things back up and running and was carefree.

I didn't follow a guide. I tried to just install it and it warned that there was an X session running.
I dropped out to a recovery console (using grub menu) and tried again. Then it complained that i was running at level 1 and it might not work, so i went to level 3 (init 3) and tried again.

To my surprise and delight, i got lucky.

---

### Post by Sydius on 2010-06-20
bionicdude's steps worked for me, too.  I realized there was a problem when I tried to run an OpenGL game.

---

### Post by sismo on 2010-09-14
> **sismo said:**
> Hi guys, same here:

When I try to use my XBMC I got a pop-up windows claiming:

XBMC needs hardware accelerated OpenGL rendering.  Install an appropriate graphics driver.

Please consult XBMC Wiki for supported hardware [http://xbmc.org/wiki/?title=Supported_hardware](http://xbmc.org/wiki/?title=Supported_hardware)

I hit ctrl-c before clicking OK on the pop-up and obtain:

Traceback (most recent call last):
  File "/usr/share/xbmc/FEH.py", line 170, in <module>
    error("XBMC needs hardware accelerated OpenGL rendering.\nInstall an appropriate graphics driver.\n\nPlease consult XBMC Wiki for supported hardware\nhttp://xbmc.org/wiki/?title=Supported_hardware")
  File "/usr/share/xbmc/FEH.py", line 29, in error
    createQt(errorLine)
  File "/usr/share/xbmc/FEH.py", line 63, in createQt
    app.exec_loop()


also I did a dmesg and got:
[ 3842.552941] glxinfo[3403]: segfault at 4 ip 001c5ef6 sp bffed5e0 error 4 in libGL.so.1.2[160000+a7000]

Hopefully someone can figure it out, because it looks like it's related to the opengl.

Thanks
Regards

Hi all:

I finally have my XBMC running again, and just can't believe that solution was in front of me.

I uninstalled fglrx. [System-->Administration-->Synaptic Package Manager and typed fglrx, advised me about some other fglrx-related packages, click on apply]
Then rebooted my system and done.

This is some additional information in case someone else have a similar system-issue:

lspci output:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

~$ uname -r -v -o
2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 GNU/Linux

~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Laptop is a latitude e6400

some sources that helped me:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555158](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/555158)
[http://ubuntuforums.org/archive/index.php/t-783714.html](http://ubuntuforums.org/archive/index.php/t-783714.html)



Regards

---

