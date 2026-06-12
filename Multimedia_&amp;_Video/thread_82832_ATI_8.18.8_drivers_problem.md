---
title: "ATI 8.18.8 drivers problem"
date: 2005-10-27
forum: Multimedia &amp; Video
---

### Post by Kensi on 2005-10-27
(My card: X800 Pro)

The latest ATI drivers appear to be 8.18.8 on the ATI site, and it states it contains some OpenGL improvements, so I decided to get the ati-driver-installer-8.18.8-i386.run installer and install them.

Everything went fine, I did the automatic installation, then ran fglrxconfig to create the new xorg.conf.

The problem is, that there appears to be no acceleration, glxgears runs very slow, as does planetpenguin-racer (the 2 OpenGL apps I tried).

My xorg.conf file seems right, with the Driver set to fglrx etc, anyone know what could be the problem?

I should mention, that I do not seem to have an fglrxinfo program anywhere after installing the drivers.

Edit: Ok, I found the fglrxinfo program (why does Places->Search for Files... and searching in the filesystem not show it up?)

This is the output:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

so something clearly went wrong, how do I change my opengl from mesa to the ati drivers opengl?

---

### Post by mlomker on 2005-10-27
We had a [how-to]("http://ubuntuforums.org/showthread.php?t=78466") for 8.18.6 that the developer and I worked on.  

If your fglrxinfo is in the wrong place then they must not have properly patched it for Ubuntu.  I'd recommend installing the 8.18.6, which we know works.  The Ubuntu developer might have to write a new patch to fix the .8 before the paths will be correct.

---

### Post by Wally68 on 2005-10-31
I have the same problem as Kensi. My card is an Asus Radeon 9550.

```
wally@ubuntu:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

wally@ubuntu:/etc/X11$ dmesg | grep fglrx
[4294742.008000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294742.024000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294742.024000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294742.056000] [fglrx:firegl_unlock] *ERROR* Process 9466 using kernel context 0
[4295184.740000] [fglrx:firegl_unlock] *ERROR* Process 10569 using kernel context 0
```

I used the installer to make breezy packages following the [howto]("http://ubuntuforums.org/showthread.php?t=78466"). When  I got to the section to select the distro, the window was way to large to display, so I killed the window. This left me still in the installer, but curses based. There is an option there to enter the installation directory. which I left alone, thinking the default [/] should be correct (even though it shouldn't be) If the problem Kensi had finding fglrxinfo was related to the path being wrong, could this also be the problem with the driver? If so, what would be the correct install path?  Or where can I get 8.18.6? I had the best 3d acceleration I've ever gotten using 8.18.6 with hoary.

Edit: on reviewing my post, I notice that the module loaded is fglrx8.16.20. Makes no sense to me. I had problems with that one and hoary, I don't think I installed that. I'll check it out, and remove xorg-driver-fglrx and fglrx-control, and the restricted modules. Then I'll try again.

---

### Post by mlomker on 2005-10-31
>  restricted modules. Then I'll try again.

Yup, it's in the restricted modules.  You'll get that error if you try to load two different versions of the driver at the same time.  You might want to search for fglrx.ko and make sure you have the right one.

```

mlomker@mlomkernote:/$ sudo updatedb
Password:
mlomker@mlomkernote:/$ locate fglrx.ko
/lib/modules/2.6.12-9-k7/misc/fglrx.ko
mlomker@mlomkernote:/$ modinfo fglrx
filename:       /lib/modules/2.6.12-9-k7/misc/fglrx.ko
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
vermagic:       2.6.12-9-k7 K7 gcc-3.4
depends:        agpgart
parm:           firegl:s

```

---

### Post by Wally68 on 2005-10-31
Yes, it would appear that I have two versions of fglrx.ko installed.

```
wally@ubuntu:/etc/X11$ locate fglrx.ko
/lib/modules/2.6.12-9-386/misc/fglrx.ko
/lib/modules/2.6.12-9-386/volatile/fglrx.ko
```

```
wally@ubuntu:/etc/X11$ modinfo fglrx
filename:       /lib/modules/2.6.12-9-386/volatile/fglrx.ko
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:        agpgart
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
parm:           firegl:s
```

I am assuming that I need to remove everything to do with fglrx and start from scratch.
Thanks for the speedy reply mlonker.

---

### Post by mlomker on 2005-10-31
> I am assuming that I need to remove everything to do with fglrx and start from scratch.


You actually just need to remove the linux-restricted-modules package.  The one in /volatile is from that package.

---

### Post by Wally68 on 2005-10-31
Bingo! I removed linux-resticted-modules and all is well. I thought I didn't have it because apt complained 'linux-restricted-modules' wasn't installed. But linux-resticted-modules-2.6.12-9-386 did when I searched using synaptic. Took me a while to reply 'cause I got lost in a silent game of chromium. Now to make the sound work.

Thanks,
Wally

---

### Post by mlomker on 2005-10-31
Glad it worked out.  The **sudo apt-get remove linux-restricted-modules-$(uname -r)** command from the how-to would have removed it.  I'm not sure why that didn't work for you.

---

### Post by Cuppa-Chino on 2005-10-31
Hooray got this bit to work instead of glxgears lingering in the low 300's now:

[INDENT]13430 frames in 5.0 seconds = 2685.854 FPS
13210 frames in 5.0 seconds = 2641.946 FPS
13303 frames in 5.0 seconds = 2660.489 FPS
13306 frames in 5.0 seconds = 2661.032 FPS[/INDENT]

That seems a massive improvement, can this be right though? P4 2.4Ghz Radeon 9500... - on the other hand the gears are really not that hard to draw...

Now all that I need to manage is to get the card *softmodded* to a radeon 9700 :arrow: [http://ubuntuforums.org/showthread.php?t=84680](http://ubuntuforums.org/showthread.php?t=84680)

---

### Post by yyagol on 2005-10-31
[SIZE="5"]mlomker[/SIZE]
Well it didnot work out at all for me...i did the new **How-To** and still
the old problem is ther and my screen is all bright:
```
XXX@ubuntu:~$ sudo updatedb
Password:
yyagol@ubuntu:~$ locate fglrx.ko
/lib/modules/2.6.12-9-386/misc/fglrx.ko
XXX@ubuntu:~$ modinfo fglrx
filename:       /lib/modules/2.6.12-9-386/misc/fglrx.ko
author:         Fire GL - ATI Research GmbH, Germany
description:    ATI Fire GL
license:        Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY
vermagic:       2.6.12-9-386 386 gcc-3.4
depends:        agpgart
parm:           firegl:s
XXX@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
XXX$$ dmesg | grep fglrx
[4294703.133000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294703.138000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294703.138000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4294703.153000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294703.154000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294703.154000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294703.154000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294703.154000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[4294703.154000] [fglrx:firegl_unlock] *ERROR* Process 8737 using kernel context 0

```

```
$ lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

```
my freind  got the same card with difrent arch and got the same problem
is it all about luck ?:???:

---

### Post by niko_ on 2005-11-01
yyagol try this, get into root (sudo -s -H) and add:

> Option "UseInternalAGPGART" "no"

to /etc/X11/xorg.conf under Section "Device".

Also edit your /boot/grub/menu.lst and append:

> video=vesafb:nomtrr

to your kernel.

good luck!

---

