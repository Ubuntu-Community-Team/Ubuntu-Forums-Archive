---
title: "VESA driver, disappearing virtual console"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by Peter1308 on 2006-09-04
Hello everybody,

I'm using the VESA driver and have the problem, that after I switch 2 times to a virtual console it will not be displayed anymore (but luckily I can always switch back to the GUI). The only odd thing I could find out was that in the Xorg.0.log I have the following message:

(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 6.99.99.904, module version = 1.0.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.8

The odd thing beeing, that it says it is compiled for 6.99.99.904 where as all other modules are compiled for 7.0.0, which should be the correct version according to the header of the log file:

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux pmost-linux 2.6.15-26-686 #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006 i686
Build Date: 16 March 2006

Is this correct or is there something wrong with my X.org installation?
I've attached my xorg.conf file if this helps (I had to rename it to upload). If the complete log file would be helpful, then let me know.

Thanks for any help

Peter

---

### Post by tseliot on 2006-09-04
Try changing the driver to "vga" or "fbdev".

But please do it by typing:
```
sudo dpkg-reconfigure xserver-xorg
```

then select the driver and press ENTER whenever you don't know the answer to the questions.

---

### Post by Peter1308 on 2006-09-04
Hello tseliot,

I've tried it and the XServer wouldn't even start! The interesting part of the log file should be:

(II) Setting vga for screen 0.
(**) FBDEV(0): Depth 24, (--) framebuffer bpp 24
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: VGA16 VGA (video memory: 64kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):  mode "1280x1024" test failed
(II) FBDEV(0):  mode "1024x768" test failed
(II) FBDEV(0):  mode "800x600" test failed
(II) FBDEV(0):  mode "640x480" test failed
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 640x400 (pitch 640)
(**) FBDEV(0):  Built-in mode "current": 25.2 MHz, 31.5 kHz, 69.9 Hz
(II) FBDEV(0): Modeline "current"   25.18  640 664 760 800  400 409 411 450 -hsync -vsync -csync
(==) FBDEV(0): DPI set to (75, 75)
(EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/bin/X(Xfree+0x21) [0x81969fa]
3: /usr/bin/X(xf86DeleteMode+0x46) [0x80c1b27]
4: /usr/bin/X(xf86DeleteScreen+0x78) [0x80bbfe1]
5: /usr/bin/X(InitOutput+0xa14) [0x809e454]
6: /usr/bin/X(main+0x292) [0x806deee]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d77ea2]
8: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

Any other tipps? Could my suspicion be true, that it is also the wrong version, because the log file says also:

(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 6.99.99.904, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8

Again the mysterious version number :-k 

Peter

---

### Post by tseliot on 2006-09-04
> **Peter1308 said:**
> Hello tseliot,

I've tried it and the XServer wouldn't even start! The interesting part of the log file should be:

(II) Setting vga for screen 0.
(**) FBDEV(0): Depth 24, (--) framebuffer bpp 24
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: VGA16 VGA (video memory: 64kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):  mode "1280x1024" test failed
(II) FBDEV(0):  mode "1024x768" test failed
(II) FBDEV(0):  mode "800x600" test failed
(II) FBDEV(0):  mode "640x480" test failed
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 640x400 (pitch 640)
(**) FBDEV(0):  Built-in mode "current": 25.2 MHz, 31.5 kHz, 69.9 Hz
(II) FBDEV(0): Modeline "current"   25.18  640 664 760 800  400 409 411 450 -hsync -vsync -csync
(==) FBDEV(0): DPI set to (75, 75)
(EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/bin/X(Xfree+0x21) [0x81969fa]
3: /usr/bin/X(xf86DeleteMode+0x46) [0x80c1b27]
4: /usr/bin/X(xf86DeleteScreen+0x78) [0x80bbfe1]
5: /usr/bin/X(InitOutput+0xa14) [0x809e454]
6: /usr/bin/X(main+0x292) [0x806deee]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d77ea2]
8: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

Any other tipps? Could my suspicion be true, that it is also the wrong version, because the log file says also:

(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 6.99.99.904, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8

Again the mysterious version number :-k 

Peter

I don't see any problem with the version.

Anyhow, did you try the vga driver?

---

### Post by tseliot on 2006-09-04
> **Peter1308 said:**
> Hello tseliot,

I've tried it and the XServer wouldn't even start! The interesting part of the log file should be:

(II) Setting vga for screen 0.
(**) FBDEV(0): Depth 24, (--) framebuffer bpp 24
(==) FBDEV(0): RGB weight 888
(==) FBDEV(0): Default visual is TrueColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: VGA16 VGA (video memory: 64kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0):  mode "1280x1024" test failed
(II) FBDEV(0):  mode "1024x768" test failed
(II) FBDEV(0):  mode "800x600" test failed
(II) FBDEV(0):  mode "640x480" test failed
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 640x400 (pitch 640)
(**) FBDEV(0):  Built-in mode "current": 25.2 MHz, 31.5 kHz, 69.9 Hz
(II) FBDEV(0): Modeline "current"   25.18  640 664 760 800  400 409 411 450 -hsync -vsync -csync
(==) FBDEV(0): DPI set to (75, 75)
(EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x86) [0x80b4ab6]
1: [0xffffe420]
2: /usr/bin/X(Xfree+0x21) [0x81969fa]
3: /usr/bin/X(xf86DeleteMode+0x46) [0x80c1b27]
4: /usr/bin/X(xf86DeleteScreen+0x78) [0x80bbfe1]
5: /usr/bin/X(InitOutput+0xa14) [0x809e454]
6: /usr/bin/X(main+0x292) [0x806deee]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7d77ea2]
8: /usr/bin/X(FontFileCompleteXLFD+0x85) [0x806d641]

Fatal server error:
Caught signal 11.  Server aborting

Any other tipps? Could my suspicion be true, that it is also the wrong version, because the log file says also:

(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 6.99.99.904, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8

Again the mysterious version number :-k 

Peter

I don't see any problem with the version.

Anyhow, did you try the vga driver?

btw what is the model of your card?
post the output of "lspci -v"

---

### Post by Peter1308 on 2006-09-04
Isn't it strange, that almost all drivers are "compiled for 7.0.0" and those that don't work (at least those that I've tried) are "compiled for 6.99.99.904"? I'm myself a developer and when I'm reading something like this, it makes me wonder.

BTW: I have two PC's (one at work and on at home) which have the same problem with the VESA driver, but different graphic cards! For now I can only give you the info for my home pc: GeForce 6800GS 256MB/DDR3 AGP 8X. I've attached the output from lspci.
Tomorrow morning I will post the output from my pc at work.

Thanks for the help!

Peter

---

### Post by tseliot on 2006-09-04
> **Peter1308 said:**
> Isn't it strange, that almost all drivers are "compiled for 7.0.0" and those that don't work (at least those that I've tried) are "compiled for 6.99.99.904"? I'm myself a developer and when I'm reading something like this, it makes me wonder.

BTW: I have two PC's (one at work and on at home) which have the same problem with the VESA driver, but different graphic cards! For now I can only give you the info for my home pc: GeForce 6800GS 256MB/DDR3 AGP 8X. I've attached the output from lspci.
Tomorrow morning I will post the output from my pc at work.

Thanks for the help!

Peter

Why don't you install the "nvidia" driver?

You can follow Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by Peter1308 on 2006-09-04
> Why don't you install the "nvidia" driver?

You can follow Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Because the nvidia driver support was broken after the last kernel update and I only found out today, why it was broken and how to fix it. So I just got it working again a couple of minutes ago :D So for now the virtual console switching is working again for my home pc, but this leaves the problem with my pc at work.
Tomorrow I post the details of my pc at work.

Peter

PS: For those who are wondering (and searching) how it was broken: The repository for the security updates of the restricted moduls was disabled and so the kernel was updated but not the corresponding restricted moduls and hence the nvidia drivers.:(

---

### Post by Peter1308 on 2006-09-05
Hello again,

> btw what is the model of your card?
post the output of "lspci -v"


here is the output with lspci from my pc at work.

Peter

---

### Post by tseliot on 2006-09-05
> **Peter1308 said:**
> PS: For those who are wondering (and searching) how it was broken: The repository for the security updates of the restricted moduls was disabled and so the kernel was updated but not the corresponding restricted moduls and hence the nvidia drivers.:(

I suggest you to install linux-386 (or k7, etc. according to your architecture) as it is a dummy package which will always update your kernel together with its restricted modules (automatically).

But of course the repositories must be enabled (as you did)

---

### Post by tseliot on 2006-09-05
> **Peter1308 said:**
> Hello again,



here is the output with lspci from my pc at work.

Peter

It's a VIA card.

Therefore I suggest you to try using the "via" driver

---

### Post by Peter1308 on 2006-09-05
> It's a VIA card.

Therefore I suggest you to try using the "via" driver

I just did and the x-server didn't start. I attached the log file for your info.

> Anyhow, did you try the vga driver?

I also tried the VGA driver but it kept complaining about not supporting the color depth and so I abandoned it, because I would like to have some colors in my GUI ;) And if I remember correctly, then VGA only supports a resolution  of 640x400 which would make the GUI also less joyfull ;) 

Peter

---

### Post by tseliot on 2006-09-05
> **Peter1308 said:**
> I just did and the x-server didn't start. I attached the log file for your info.



I also tried the VGA driver but it kept complaining about not supporting the color depth and so I abandoned it, because I would like to have some colors in my GUI ;) And if I remember correctly, then VGA only supports a resolution  of 640x400 which would make the GUI also less joyfull ;) 

Peter
Try with 16 as colour depth.

---

### Post by Peter1308 on 2006-09-05
> **tseliot said:**
> Try with 16 as colour depth.

Sorry to maybe ask the obvious, but do you mean I should try it with the VIA or with the VGA driver?

But one question remains, even if I get the VIA driver working: Shouldn't the  switching to a virtual console also be working with the VESA driver? Why isn't it working? Is there some other way of finding out why the switch fails ?

Peter

---

### Post by tseliot on 2006-09-05
> **Peter1308 said:**
> Sorry to maybe ask the obvious, but do you mean I should try it with the VIA or with the VGA driver?

use VGA then set the DefaultDepth to 16 in your xorg.conf

---

### Post by Peter1308 on 2006-09-05
> **tseliot said:**
> use VGA then set the DefaultDepth to 16 in your xorg.conf

ColorDepth 16 and 15 didn't work, but the depth of 8 did kind of work. But as I suspected it only supports 640x400, which is not much fun to work with. I attached the log file.

I don't know whether this little detail is important, but when I switch to the virtual console the second time, all I can see is a blinking cursor.

In case you didn't see the editing of my previous post:
"But one question remains, even if I get the VIA driver working: Shouldn't the switching to a virtual console also be working with the VESA driver? Why isn't it working? Is there some other way of finding out why the switch fails ?"

Peter

---

### Post by tseliot on 2006-09-05
> **Peter1308 said:**
> ColorDepth 16 and 15 didn't work, but the depth of 8 did kind of work. But as I suspected it only supports 640x400, which is not much fun to work with. I attached the log file.

I don't know whether this little detail is important, but when I switch to the virtual console the second time, all I can see is a blinking cursor.

In case you didn't see the editing of my previous post:
"But one question remains, even if I get the VIA driver working: Shouldn't the switching to a virtual console also be working with the VESA driver? Why isn't it working? Is there some other way of finding out why the switch fails ?"

Peter
I don't know what can be causing that problem.

What happens if you set the driver to "vesa" and use 16 as colour depth?

---

