---
title: "ATI Driver problem 8.16.20"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by Téragone on 2005-10-13
Hello,

After I just made a fresh install of Breezy AMD64, I try to install the xorg-driver-fglrx ATI driver.

During reboot the X server doesn't start, I had this error int the xorg log :

Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Any Idea ?

ATI 9700 Pro
AMD 64 3000

---

### Post by jiahanhao on 2005-10-13
in your xorg.conf, you must comment out the line in the modules section that loads the int10 module...

---

### Post by Téragone on 2005-10-13
Thanks,

I try it. X server start but I got this error :

einstein:/etc/X11$ fglrxinfo
libGL error: drmMap of framebuffer failed
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)



display: :0.0  screen: 1
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by mlomker on 2005-10-13
> OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)


If you see anything about Mesa then it isn't working.  Did you install all of the pieces in the [how-to?]("http://ubuntuforums.org/showthread.php?t=75378")

If so, then I'd try it again and use the **install --reinstall** switch.  If that doesn't work then let me know and we'll do a more complete removal.

---

### Post by Téragone on 2005-10-13
Thanks for your reply.

I have done the reinstall and rebooted. Nothing change.

In hoary, I was using the AMD64-K8 kernel not the AMD-64-generic, did you think that it may affect the ati driver ?

David

P.S. I don't mind to reinstall from scratch.

---

### Post by mlomker on 2005-10-13
Instructions for removing ATI drivers and installing Breezy's.  

Let's try this:

```

sudo apt-get remove fglrx-6-8-0 #*If you did the alien/RPM install*
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)

```

Reboot (restricted modules remain in memory until reboot).  You might want to use 'rescue' mode from grub to do the remainder.  The other option is to run **sudo dpkg-reconfigure xserver-xorg** to create an xorg.conf file for the 'ati' driver before you can go graphical again...and then again after reboot to go back to fglrx.

```

sudo find / -iname '*fglrx*' -exec rm '{}' -r ';'
sudo apt-get install fglrx-control
sudo apt-get install linux-restricted-modules-$(uname -r)

```

I'd restart again for good measure, but you could probably just **startx** from the prompt.  With any luck, **fglrxinfo** will be displaying ATI instead of Mesa.  


Edit: Modified for future references.

---

### Post by jlx on 2005-10-13
Now I have 3D acceleration. This is what I did:
-install all the packages as in post ATI Howto
-dpkg-reconfigure xserver-xorg (don't use fglrxconfig)
-edit xorg.conf and change ati to fglrx in Driver

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

When I used fglrxconfig the Xs didn't start and the scrren went black and I had to restart.
Hope it helps.

---

### Post by Téragone on 2005-10-13
In the last line, I think that is install not remove ?

---

### Post by mlomker on 2005-10-13
[QUOTE=Téragone]In the last line, I think that is install not remove ?[/QUOTE]

hehe.  cut & paste.

---

### Post by Téragone on 2005-10-13
New problem:

(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *

---

### Post by mlomker on 2005-10-13
> 
(EE) fglrx(0): DRIScreenInit failed!


That seems like a common error.  I had a section about it in my [Hoary how-to]("http://www.ubuntuforums.org/showthread.php?p=348911") toward the end.  One member had offered a replacement libdri.a file that fixed the issue for him, but I can't vouch for it.

The file is a part of the xserver-xorg-core package.  I found some other posts that suggest it is a generic error.

Have you looked through the rest of the Xorg.0.log file?

---

### Post by Téragone on 2005-10-13
Back to this problem:

[http://ubuntuforums.org/showpost.php?p=408362&postcount=3](http://ubuntuforums.org/showpost.php?p=408362&postcount=3)

---

### Post by Téragone on 2005-10-14
I just find this bug about my problem

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17614](https://bugzilla.ubuntu.com/show_bug.cgi?id=17614)

I will wait for update before doing anything else.

Thank you very much for your help mlomker

---

### Post by ilans on 2005-10-14
Hi

I followed the How-To instructions several times and still "suffering" from
No 3D acceleration.

Attached PART from the file /var/log/Xorg.0.log where you can see the problem:
***************************************************************************************
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-9-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xff820000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EBUSY"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c8a000 at 0xb7b62000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
***************************************************************************************

In addition my output to:  fglrxinfo command is:
***************************************************************************
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
****************************************************************************
I.E. the mesa3d is still exist!!!

I tried several times to do:
sudo apt-get install --reinstall fglrx-control
sudo apt-get install --reinstall xorg-driver-fglrx
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r)
sudo fglrxconfig

I read that fglrxconfig is not preffered so I tried to run too :
dpkg-reconfigure xserver-xorg 
but... It didn't help !!!

---

### Post by jlx on 2005-10-14
Did you change after try dpkg-reconfigure xserver-xorg in xorg.conf Driver "ati" to Driver "fglrx"?
I did it that way and now I have 3D acceleration.

---

### Post by ilans on 2005-10-14
[QUOTE=jlx]Did you change after try dpkg-reconfigure xserver-xorg in xorg.conf Driver "ati" to Driver "fglrx"?
I did it that way and now I have 3D acceleration.[/QUOTE]

Yes, But it didn't helped too :(

---

### Post by SilverTab on 2005-10-14
ilans: 

I get similar results...here's part of my log:

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bfb000 at 0xb7ab8000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


You get an xf86_EBUSY error while I get xf86_EINVAL.... :(

Can you tell me what you get when you type: cat /proc/mtrr  

I only get 1 line:
reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=1

which is my ram....no video memory! ... :(

---

### Post by pwarren on 2005-10-14
just another me too.

Athlon 64 3800+, Gigabyte GA-K8NF-9, ATI Radeon X800 XL.

Ubuntu Breezy clean install.
followed the instructions at:
[HOW-TO: ATI Radeon driver (fglrx)]("http://www.ubuntuforums.org/showthread.php?t=65276"),


fglrxinfo:
```

libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

LIBGL_DEBUG=verbose fglrxinfo:
```

libGL: XF86DRIGetClientDriverName: 8.16.20 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.16.20 fglrx (screen 0)
drmOpenByBusid: busid is PCI:5:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:5:0:0
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

relevent parts of /var/log/Xorg.0.log
```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:5:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x00777000
(II) fglrx(0): [drm] mapped SAREA 0x00777000 to 0x2aaaaab45000
(II) fglrx(0): [drm] framebuffer handle = 0xd0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-9-amd64-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xe1000000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x008f4000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
```

Hope someone comes up with a solution to this :)

Cheers
Paul

---

### Post by Téragone on 2005-10-14
SilverTab : I think you have another problem. I will be surprise if you have 984064 MB of ram in your PC. It's near 948 GB.:???:

---

### Post by SilverTab on 2005-10-14
[QUOTE=Téragone]SilverTab : I think you have another problem. I will be surprise if you have 984064 MB of ram in your PC. It's near 948 GB.:???:[/QUOTE]


damn, you have a pretty valid point!....

I always read it fast and thought it was 984064KB  (I have 1gig of ram)....


mmmmm...I wonder what to do now LOL...Like I needed a new problem... :P

---

### Post by SilverTab on 2005-10-14
Weird, in system monitor, (and everywhere I check)... I see 1gb of ram....

---

### Post by Téragone on 2005-10-14
I have stop working on the Ati driver problem. As I write in a previous post they are a bug registered about that :

[https://bugzilla.ubuntu.com/show_bug.cgi?id=17614](https://bugzilla.ubuntu.com/show_bug.cgi?id=17614)

Wait and See

---

### Post by cbudden on 2005-10-14
Have any of you with the ATI driver installed been sucessful in getting hibernation to work?

---

### Post by ilans on 2005-10-14
[QUOTE=SilverTab]ilans: 

I
Can you tell me what you get when you type: cat /proc/mtrr  

I only get 1 line:
reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=1

which is my ram....no video memory! ... :([/QUOTE]

cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1


But I think that I know what the problem is:
I run ::
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

So the problem is that my ATI card is not recognize BY THE KERNEL.
I have ATI RADEON 9550 but all the scripts that I run 
in order to config xorg.conf  "recognize" it as 9600

---

### Post by SilverTab on 2005-10-14
[QUOTE=ilans]cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1


But I think that I know what the problem is:
I run ::
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

So the problem is that my ATI card is not recognize BY THE KERNEL.
I have ATI RADEON 9550 but all the scripts that I run 
in order to config xorg.conf  "recognize" it as 9600[/QUOTE]

I have the same card as you! And I get the same thing:
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173


seems like our problems are exactly the same!... :???:

---

### Post by archiesteel on 2005-10-14
I believe this got broken with the latest xorg upgrade...seems to me everything was working great before this.

I know it's not the actual module because using the ati installer also gives problems (GL apps complain that libGL.so.1 is missing, while it is present), as it used to work great before the latest xorg upgrade.

---

### Post by krak on 2005-10-14
everything works fine thx for tutorial !!
i had only to run fglrxconfig

---

### Post by archiesteel on 2005-10-14
[QUOTE=SilverTab]I have the same card as you! And I get the same thing:
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173


seems like our problems are exactly the same!... :???:[/QUOTE]

I have similar problems and my ATI card (well, laptop chipset) isn't recognized as well:

```
elie@anaxana:~$ lspci | grep ATI
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
```

I have an ATI RADEON® XPRESS 200M IGP with 128MB (laptop motherboard) with an AMD64 system, for what it's worth...

---

### Post by mlomker on 2005-10-14
> Ubuntu Breezy clean install.
followed the instructions at:
[HOW-TO: ATI Radeon driver (fglrx)]("http://www.ubuntuforums.org/showthread.php?t=65276"),


Those instructions were for Hoary...too many things have changed in Breezy.  The built-in drivers can be installed using the 1st post of this thread.  That *does* work on my laptop.  YMMV, as always.

Have you tried [removing everything]("http://www.ubuntuforums.org/showpost.php?p=408876&postcount=6") before adding it back (the find/rm command)?

---

### Post by mlomker on 2005-10-14
> libGL.so.1 is missing, while it is present), as it used to work great before the latest xorg upgrade.

I couldn't get around that problem on my upgraded amd64 Hoary, so I went with a clean 32-bit install this morning.  What kernel are you running?

Take a look at the ldconfig parts of my [8.18.6 install instructions]("http://ubuntuforums.org/showthread.php?p=411503").  Like I said...could never figure it out on my upgraded box, though.

---

### Post by archiesteel on 2005-10-14
[QUOTE=mlomker]I couldn't get around that problem on my upgraded amd64 Hoary, so I went with a clean 32-bit install this morning. What kernel are you running? Take a look at the ldconfig parts of my [8.18.6 install instructions]("http://ubuntuforums.org/showthread.php?p=411503"). Like I said...could never figure it out on my upgraded box, though.[/QUOTE]

Sorry, I should have been clearer. I am running an amd64 laptop as well, using the official breezy 64-bit: 

```
elie@anaxana:/usr/lib$ uname -a Linux anaxana 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux
```

I also have a 32-bit chroot for some stuff, such as watching trailers on apple.com...I installed the 32-bit version of the libraries from the ati installer in the chroot and I get good 3D acceleration with glxgears - but not fgl_glxgears... So it seems to me that the kernel driver is working correctly, as are the 32-bit libraries from ati.

Note that the libGL.so.1 problem is only when using the ati installer script downloaded directly from the ati web site. I did previously follow your instructions for the 8.18.6 drivers, and it installed cleanly. I didn't get a libGL.so.1 error, however I still get Mesa listed when I check with fglrxinfo, and 3D performance is very bad.

In other words, the 64-bit libraries installed by the ati installer script don't seem to work with GL apps, which don't link to them, even after tweaking the /etc/ld.so.conf file (which I tried as well after reading about it in your howto).

Here is the result of the 64-bit fglrxinfo (from breezy packages, but I had the same message using the aliened ati rpm): 

```
elie@anaxana:~$ fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

Here is the result of the 32-bit fglrxinfo from the ati installer (installed in a ia32 chroot):

```
elie@anaxana:/usr/lib$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
```

---

### Post by mlomker on 2005-10-14
> In other words, the 64-bit libraries installed by the ati installer script don't seem to work with GL apps, which don't link to them, even after tweaking the /etc/ld.so.conf file (which I tried as well after reading about it in your howto).


You've figured out a bit more than I did.  I didn't have a chroot, so I couldn't get them to do anything.

Every time I used **ldd** against one of the openGL programs I found that there was no link at all for libGL.so.1.  It's almost like ATI's 64-bit file isn't recognized by Breezy at all, despite being installed.  It actually makes me wonder if it's a bug in Ubuntu's code somewhere.  I've heard reports from other 64-bit linux users that have it working on their distro.

---

### Post by archiesteel on 2005-10-15
[QUOTE=mlomker]You've figured out a bit more than I did.  I didn't have a chroot, so I couldn't get them to do anything.[/QUOTE]

chroots are neat. I just recently found out about them...very useful when you run a 64-bit distro (considering some things don't have 64-bit versions, such as Flash).

> It's almost like ATI's 64-bit file isn't recognized by Breezy at all, despite being installed.

I have the same feelings exactly.

---

### Post by Téragone on 2005-10-15
Is it normal that libGL.a is not replace by the installation of xorg-driver-fglrx package ?

---

### Post by wombat20 on 2005-10-18
[QUOTE=mlomker]
```

sudo find / -iname '*fglrx*' -exec rm '{}' -r ';'

```
[/QUOTE]

This worked for me once.  Then I fiddled with my xorg.conf to get my mouse working and *poof!* X won't start.  

So I go through your routine above (as it worked before) and SOMEHOW the line I quoted managed to wreck my ENTIRE HD!!!!  I first noticed when apt-get didn't work, then shutdown wasn't recognised.  'ls' not recognised..... oh this isn't good.

It turns out even my mounted windows drives have been shafted - no files!  WTF?  Did I type something wrong there this time?

Now i've got to reinstall Windows followed by Ubuntu and all the software... I think I have my data backed up somewhere.... I THINK.  :confused: 

Once I get Ubuntu working again - I'M NOT GONNA TOUCH ANYTHING! :(

---

### Post by mlomker on 2005-10-18
It shouldn't have done anything to windows.  We used that command on Hoary to get rid of the old junk but it shouldn't be needed on Breezy.  You can easily modify the command to just give you a list of what it's going to do by removing the deletion part of the command.

```

find / -iname '*fglrx*' 

```

---

### Post by carbsk on 2005-10-22
hey everybody, I just got a new machine, it's a toshiba L25-S119, and I tried to install the ubuntu new version, but, the problem is with tha video card, witch is a ATI RADEON XPRESS 200M, and I've been locking for a driver to have a graphic mode, if someone know where I can get it, please reply me...
thanks...
CARBSK

---

### Post by mlomker on 2005-10-22
[QUOTE=carbsk]I've been locking for a driver to have a graphic mode, if someone know where I can get it, [/QUOTE]

[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

---

