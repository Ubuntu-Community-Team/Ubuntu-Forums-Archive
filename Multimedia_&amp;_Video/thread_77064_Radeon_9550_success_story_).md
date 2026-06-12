---
title: "Radeon 9550 success story :)"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by Pablo_Escobar on 2005-10-16
I experienced the same problems as others using Radeon 9550 and Breezy.
I'm running AMD64 3000+ on 32 bit.

I don't know exectly what I did right, because earlier with fglrxinfo I had Mesa, with only errors popped out. I had my doubts (even thought about installing Fedora - but my hate for yum and love for Ubuntu won).

Some of following steps made something right for me.
I made a fresh install today. I haven't played with fglrx. I installed bunch of stuff (thunderbird, vlc, bmp, and others). I later decided to try one more time with fglrx.
I don't know if this is relevant but before fglrx i installed following packages :
**g++-3.4** and **g++-4.0**.
The i  **synapticed xorg-driver-fglrx** and **fglrx-control**.
I rebooted after install.
Then I changed in xorg.conf in Device Section "ati" for "fglrx". Saved the file. Kept my fingers crossed. CRTL-ALT-BACKSPACE and voila. 
Here's how my system looks like :
> pablo@ubuntu:~$ fgl_glxgears
1932 frames in 5.0 seconds = 386.400 FPS
1998 frames in 5.0 seconds = 399.600 FPS
   
> pablo@ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
9507 frames in 5.0 seconds = 1901.319 FPS
9458 frames in 5.0 seconds = 1891.598 FPS
9399 frames in 5.0 seconds = 1879.752 FPS
9398 frames in 5.0 seconds = 1879.484 FPS
9398 frames in 5.0 seconds = 1879.509 FPS

**The most important bit**
> pablo@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


Maybe someone will find it usefull (g++- libraries part). No major updates were available in synaptic, so the fix was my part.
Maybe someone will try it and report back if it helped him.

ATI users, keep Your heads up :)

---

### Post by ilans on 2005-10-16
Hello Pablo:
I have either ATI RADEON 9550 (Which recognize as 9600 ???)
can you please send the output of  lspci command  and the DEVICE module in xorg.conf:

here are my (I think that the kernel don't recognize my card):
CODE:
*******************************************************************************
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173


Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
EndSection

AS YOU CAN SEE THE CARD IS NOT RECOGNIZE CORRECTLY

---

### Post by Pablo_Escobar on 2005-10-16
lspci |grep ATI also in my case tells Unknown device, but all works well (3d acceleration). Heh, don't know what's the case.

---

### Post by mlomker on 2005-10-16
Pablo, do me a big favor and give me the output of this command:

```

ldd /usr/bin/glxinfo

```

I think you might be onto something with the missing library idea.  I install a lot of 'extra' stuff on my machine to compile things so maybe that's why I haven't had any problems with the drivers.

---

### Post by Pablo_Escobar on 2005-10-16
Here You are mlomker.
I hope You get more of this than me :) I'm still learning :)

> pablo@ubuntu:~$ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7f13000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e9d000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e73000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e51000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d23000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c63000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c56000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c44000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c40000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b5a000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b4f000)
        /lib/ld-linux.so.2 (0xb7fbf000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b4c000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b48000)


---

### Post by mlomker on 2005-10-16
> I hope You get more of this than me

Your output matches mine.  We are definitely onto something.  Now to figure out which packages to install.

Stay tuned.

---

### Post by ilans on 2005-10-16
Why my ldd /usr/bin/glxinfo output is different ?

ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7eed000)   <========
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e77000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e4d000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e2b000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cfd000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c3d000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c30000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c1e000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c1a000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b34000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b29000)
        /lib/ld-linux.so.2 (0xb7fa0000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b26000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b22000)

---

### Post by mlomker on 2005-10-16
[QUOTE=ilans]Why my ldd /usr/bin/glxinfo output is different ?
[/QUOTE]

I don't see any obvious differences.  They are just listed in a different order.  Do your drivers work?

I'm also *not* a programmer.  This is new territory for me but these libraries were the key to getting my machine working, so I'm assuming there might be some clues here.

---

### Post by ilans on 2005-10-16
[QUOTE=mlomker]I don't see any obvious differences.  They are just listed in a different order.  Do your drivers work?
[/QUOTE]

My driver is not working :( 
I saw a difference in this line:
libGL.so.1 => /usr/X11R6/lib/libGL.so.1

Pablo line:
 libGL.so.1 => /usr/lib/libGL.so.1

I wonder if it is regarding to my previous driver (8.18.6)
I remove all the new driver definition (8.18.6)
and install the original driver 8.16.20. in addition I install g++ 4.0 
and g++ 3.4.
I think that the different line in a "memory" from my old driver :confused:

---

### Post by SilverTab on 2005-10-16
[QUOTE=ilans]My driver is not working :( 
I saw a difference in this line:
libGL.so.1 => /usr/X11R6/lib/libGL.so.1

Pablo line:
 libGL.so.1 => /usr/lib/libGL.so.1

I wonder if it is regarding to my previous driver (8.18.6)
I remove all the new driver definition (8.18.6)
and install the original driver 8.16.20. in addition I install g++ 4.0 
and g++ 3.4.
I think that the different line in a "memory" from my old driver :confused:[/QUOTE]

I have the same problem with the 9550, here's my output:
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7f30000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7eba000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e90000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e6e000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d40000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c80000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c73000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c61000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c5d000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b77000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b6c000)
        /lib/ld-linux.so.2 (0xb7fdd000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b69000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b65000)

---

### Post by mlomker on 2005-10-16
> My driver is not working :( 
I saw a difference in this line:
libGL.so.1 => /usr/X11R6/lib/libGL.so.1


Thanks for pointing that out.  That's interesting, because my 8.18.6 install has to point to the one that you're referring to for it to work.  

Try this:
```

sudo rm /etc/ld.so.conf
sudo ldconfig

```

---

### Post by ilans on 2005-10-16
[QUOTE=mlomker]
Try this:
```

sudo rm /etc/ld.so.conf
sudo ldconfig

```[/QUOTE]

O.K. now I have the same definition as Pablo , but
still get Mesa 3D, and not a clue of 3D acceleration :( 

I hope that the people in Ubuntu is reading this forum, and will release a 
fix to the video drivers

---

### Post by mlomker on 2005-10-16
> Stay tuned.

The bad news is that all of the packages that are linked to are included on a default Breezy installation.

SilverTab, do you have a /etc/ld.so.conf file?  If so, what is in it?

---

### Post by SilverTab on 2005-10-16
[QUOTE=mlomker]The bad news is that all of the packages that are linked to are included on a default Breezy installation.

SilverTab, do you have a /etc/ld.so.conf file?  If so, what is in it?[/QUOTE]


yup, here's the content of the file:


/usr/local/lib


(Note: There are really 2 linefeed before the actual /usr/local/lib  line)

---

### Post by mlomker on 2005-10-16
> O.K. now I have the same definition as Pablo , but
still get Mesa 3D, and not a clue of 3D acceleration :( 


The developers don't read the forums.  What we can do is try to narrow problems down and file accurate bug reports at the Bugzilla link at the top of the page.

Try this for me:

```

sudo updatedb
locate libGL.so.1.2

```

Then do an **ls -l /path/to/file/libGL.so.1.2** for each file and post the results.

---

### Post by SilverTab on 2005-10-16
Here are my results:
 locate libGL.so.1.2
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/libGL.so.1.2
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/X11R6/lib/libGL.so.1.2

and each of the ls -l for these results:
```
ls -l /usr/lib/i686/mmx/cmov/libGL.so.1.2
-rw-r--r--  1 root root 403432 2005-09-23 05:34 /usr/lib/i686/mmx/cmov/libGL.so.1.2
```
```

ls -l /usr/lib/libGL.so.1.2
lrwxrwxrwx  1 root root 25 2005-10-13 22:53 /usr/lib/libGL.so.1.2 -> ../X11R6/lib/libGL.so.1.2

```
```

ls -l /usr/lib/fglrx/libGL.so.1.2.xlibmesa
-rw-r--r--  1 root root 407720 2005-09-23 05:34 /usr/lib/fglrx/libGL.so.1.2.xlibmesa

```

```
ls -l /usr/X11R6/lib/libGL.so.1.2
-rw-r--r--  1 root root 634628 2005-10-11 13:17 /usr/X11R6/lib/libGL.so.1.2

```

---

### Post by ilans on 2005-10-16
I have different result:

***********************************************
locate libGL.so.1.2
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/libGL.so.1.2
/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa.dpkg-tmp
/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/X11R6/lib/libGL.so.1.2
/usr/X11R6/lib/FGL.renamed.libGL.so.1.2

ls -l /usr/lib/i686/mmx/cmov/libGL.so.1.2
-rw-r--r--  1 root root 403432 2005-09-23 12:34 /usr/lib/i686/mmx/cmov/libGL.so. 1.2

ls -l /usr/lib/fglrx/libGL.so.1.2.xlibmesa
-rw-r--r--  1 root root 407720 2005-09-23 12:34 /usr/lib/fglrx/libGL.so.1.2.xlib mesa

ls -l /usr/lib/libGL.so.1.2
lrwxrwxrwx  1 root root 25 2005-10-16 14:39 /usr/lib/libGL.so.1.2 -> ../X11R6/li b/libGL.so.1.2

ls -l /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa.dpkg-tmp
-rwxr-xr-x  1 root root 773466 2005-10-11 19:49 /usr/X11R6/lib/fglrx/libGL.so.1. 2.xlibmesa.dpkg-tmp

ls -l /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
-rwxr-xr-x  1 root root 773466 2005-10-11 19:49 /usr/X11R6/lib/fglrx/libGL.so.1. 2.xlibmesa

ls -l /usr/X11R6/lib/libGL.so.1.2
-rw-r--r--  1 root root 634628 2005-10-11 19:17 /usr/X11R6/lib/libGL.so.1.2

ls -l /usr/X11R6/lib/FGL.renamed.libGL.so.1.2
-rw-r--r--  1 root root 634628 2005-10-11 19:17 /usr/X11R6/lib/FGL.renamed.libGL .so.1.2

---

### Post by mlomker on 2005-10-16
>  locate libGL.so.1.2


It looks like the installer moves Mesa's libGL file, renames it, and then does a symbolic link to the real file under /usr/X11R6.  That explains why ldd points to /usr/lib.  That is the correct file.

Try:

```

locate libGL.so

```

Check by using the **ls -l** command to see if any of the symbolic links are pointing at the old file that was renamed xlibmesa.

---

### Post by ilans on 2005-10-16
[QUOTE=mlomker]It looks like the installer moves Mesa's libGL file, renames it, and then does a symbolic link to the real file under /usr/X11R6.  That explains why ldd points to /usr/lib.  That is the correct file.

Try:

```

locate libGL.so

```

Check by using the **ls -l** command to see if any of the symbolic links are pointing at the old file that was renamed xlibmesa.[/QUOTE]


locate libGL.so
/usr/lib/i686/mmx/cmov/libGL.so.1
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/libGL.so.1
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/lib/libGL.so.1.2
/usr/lib/libGL.so
/usr/X11R6/lib/libGL.so.1
/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa.dpkg-tmp
/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/X11R6/lib/libGL.so.1.2
/usr/X11R6/lib/FGL.renamed.libGL.so.1.2
/usr/X11R6/lib/libGL.so

ls -l /usr/lib/libGL.so
lrwxrwxrwx  1 root root 27 2005-10-15 18:04 /usr/lib/libGL.so -> /usr/X11R6/lib/libGL.so.1.2

ls -l /usr/X11R6/lib/libGL.so
lrwxrwxrwx  1 root root 27 2005-10-15 18:04 /usr/X11R6/lib/libGL.so -> /usr/X11R6/lib/libGL.so.1.2

---

### Post by mlomker on 2005-10-16
> 
ls -l /usr/lib/libGL.so
lrwxrwxrwx  1 root root 27 2005-10-15 18:04 /usr/lib/libGL.so -> /usr/X11R6/lib/libGL.so.1.2


Could you do all of the files that locate discovered?  I'm trying to figure out if one of them is pointing to the wrong file.

---

### Post by SilverTab on 2005-10-16
similar results here...nothing is pointing to xlibmesa...
 locate libGL.so
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/i686/mmx/cmov/libGL.so.1
/usr/lib/libGL.so.1.2
/usr/lib/libGL.so.1
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
/usr/X11R6/lib/libGL.so.1.2
/usr/X11R6/lib/libGL.so.1

the entries for /usr/lib/*  are linking to the correct files (/usr/X11R6/lib/*)

---

### Post by ilans on 2005-10-16
[QUOTE=mlomker]Could you do all of the files that locate discovered?  I'm trying to figure out if one of them is pointing to the wrong file.[/QUOTE]

ls -l /usr/lib/i686/mmx/cmov/libGL.so.1
lrwxrwxrwx  1 root root 12 2005-10-16 16:19 /usr/lib/i686/mmx/cmov/libGL.so.1 ->  libGL.so.1.2

ls -l /usr/lib/i686/mmx/cmov/libGL.so.1.2
-rw-r--r--  1 root root 403432 2005-09-23 12:34 /usr/lib/i686/mmx/cmov/libGL.so. 1.2

ls -l /usr/lib/libGL.so.1
lrwxrwxrwx  1 root root 12 2005-10-16 14:39 /usr/lib/libGL.so.1 -> libGL.so.1.2

ls -l /usr/lib/fglrx/libGL.so.1.2.xlibmesa
-rw-r--r--  1 root root 407720 2005-09-23 12:34 /usr/lib/fglrx/libGL.so.1.2.xlib mesa

ls -l /usr/lib/libGL.so.1.2
lrwxrwxrwx  1 root root 25 2005-10-16 14:39 /usr/lib/libGL.so.1.2 -> ../X11R6/li b/libGL.so.1.2

ls -l /usr/lib/libGL.so
lrwxrwxrwx  1 root root 27 2005-10-15 18:04 /usr/lib/libGL.so -> /usr/X11R6/lib/ libGL.so.1.2

ls -l /usr/X11R6/lib/libGL.so.1
lrwxrwxrwx  1 root root 12 2005-10-16 14:39 /usr/X11R6/lib/libGL.so.1 -> libGL.so.1.2

ls -l /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa.dpkg-tmp
-rwxr-xr-x  1 root root 773466 2005-10-11 19:49 /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa.dpkg-tmp

ls -l /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa
-rwxr-xr-x  1 root root 773466 2005-10-11 19:49 /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa

ls -l /usr/X11R6/lib/libGL.so.1.2
-rw-r--r--  1 root root 634628 2005-10-11 19:17 /usr/X11R6/lib/libGL.so.1.2

ls -l /usr/X11R6/lib/FGL.renamed.libGL.so.1.2
-rw-r--r--  1 root root 634628 2005-10-11 19:17 /usr/X11R6/lib/FGL.renamed.libGL.so.1.2

ls -l /usr/X11R6/lib/libGL.so
lrwxrwxrwx  1 root root 27 2005-10-15 18:04 /usr/X11R6/lib/libGL.so -> /usr/X11R6/lib/libGL.so.1.2

---

### Post by mlomker on 2005-10-16
> ls -l /usr/X11R6/lib/libGL.so
lrwxrwxrwx  1 root root 27 2005-10-15 18:04 /usr/X11R6/lib/libGL.so -> /usr/X11R6/lib/libGL.so.1.2

Looks like I've struck out on that idea.  Back to head-scratching for a bit.

ilans,  what is the output of this for you (after a recent boot-up):

```

dmesg | grep fglrx

```

Attach a copy of your /etc/X11/xorg.conf and the /var/log/Xorg.0.log to your post (just rename them so they end in .txt).

You are running 32-bit Breezy from a clean install or an upgrade?  I assume you have a 9550 since you're in this thread?  Have you tried the reinstall method in [this thread]("http://ubuntuforums.org/showthread.php?p=408111") already?

---

### Post by ilans on 2005-10-16
[QUOTE=mlomker]
```

dmesg | grep fglrx

```

Attach a copy of your /etc/X11/xorg.conf and the /var/log/Xorg.0.log to your post (just rename them so they end in .txt).

You are running 32-bit Breezy from a clean install or an upgrade?  I assume you have a 9550 since you're in this thread?  Have you tried the reinstall method in [this thread]("http://ubuntuforums.org/showthread.php?p=408111") already?[/QUOTE]

I am using 32-bit breezy (upgraded from hoary), ATI 9550.
I just did another reinstall (method in your given link) 

dmesg | grep fglrx
[4294695.932000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294695.936000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294695.936000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294718.930000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294718.931000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294718.931000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294718.931000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294718.931000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4294718.932000] [fglrx:firegl_unlock] *ERROR* Process 8336 using kernel context 0

---

### Post by ilans on 2005-10-16
My xorg.conf

---

### Post by ilans on 2005-10-16
Suspesius raws from /var/lof/xorg.0.log (it is too long to atached)

---

### Post by mlomker on 2005-10-16
> 
[4294718.930000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294718.932000] [fglrx:firegl_unlock] *ERROR* Process 8336 using kernel context 0


These are certainly problems but it isn't related to the libraries.  I'd speculate that it is the result of either the system BIOS or the video card BIOS not passing the proper memory size to the driver.  It could be a new Ubuntu bug, of course, and I know that a report has been filed.  

Is your motherboard BIOS current?  I always like to double-check that when I'm dealing with these kind of problems.

It's [discussed here.]("http://www.rage3d.com/board/printthread.php?t=33736241")

---

### Post by ilans on 2005-10-16
[QUOTE=mlomker]These are certainly problems but it isn't related to the libraries.  I'd speculate that it is the result of either the system BIOS or the video card BIOS not passing the proper memory size to the driver.  It could be a new Ubuntu bug, of course, and I know that a report has been filed.  

Is your motherboard BIOS current?  I always like to double-check that when I'm dealing with these kind of problems.

It's [discussed here.]("http://www.rage3d.com/board/printthread.php?t=33736241")[/QUOTE]

I think that both bios, video card and motherboard, are o.k.
I had an excellent 3D performance in Ubuntu Hoary (before upgrading to Breezy) .
My daugther  played (in Hoary) with tuxracer, and the 3D run  smoothly)

---

### Post by SilverTab on 2005-10-16
[QUOTE=ilans]I think that both bios, video card and motherboard, are o.k.
I had an excellent 3D performance in Ubuntu Hoary (before upgrading to Breezy) .
My daugther  played (in Hoary) with tuxracer, and the 3D run  smoothly)[/QUOTE]

ilans: Check out my thread on the rage3d forum about this issue:
[http://www.rage3d.com/board/showthread.php?t=33831753](http://www.rage3d.com/board/showthread.php?t=33831753)

some things that I still haven't tried, could help you out...

---

### Post by mincho on 2005-10-16
i have done exactly as you say but i having problem in changing screen resolution when i configure the xorg and restart the xserver there is no change in resolution still 640x480.
           and when i click on System>>Preferences>> Screen Resolution there is an error message popped out ..
                > The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.
        otherwise all the things are good.
 please help me in resol;ution change.
> root@ubuntu:/home/mincho # fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

root@ubuntu:/home/mincho # glxgears
5823 frames in 5.0 seconds = 1164.600 FPS
6211 frames in 5.0 seconds = 1242.200 FPS
6224 frames in 5.0 seconds = 1244.800 FPS
6225 frames in 5.0 seconds = 1245.000 FPS
6189 frames in 5.0 seconds = 1237.800 FPS
6223 frames in 5.0 seconds = 1244.600 FPS
6148 frames in 5.0 seconds = 1229.600 FPS
6219 frames in 5.0 seconds = 1243.800 FPS
6108 frames in 5.0 seconds = 1221.600 FPS
root@ubuntu:/home/mincho # fgl_glxgears
1712 frames in 5.0 seconds = 342.400 FPS
2262 frames in 5.0 seconds = 452.400 FPS
2241 frames in 5.0 seconds = 448.200 FPS
2382 frames in 5.0 seconds = 476.400 FPS
2334 frames in 5.0 seconds = 466.800 FPS

             HELP ME HOW CAN I CHNAGE MY SCREEN RESOLUTION...... i want 1024x768....

---

### Post by mlomker on 2005-10-16
> i want 1024x768....

You should be able to go to a prompt and run **sudo dpkg-reconfigure xserver-xorg**.  Take the defaults for whatever you're not sure about and select only the resolution that you want.

---

### Post by mincho on 2005-10-16
mlomker ,
  i ve done already you just say in your but still no change in my resolution i take all the defaults. but no change tell me the correct way please.
                       thanks

---

### Post by mlomker on 2005-10-16
>  i ve done already you just say in your but still no change in my resolution i take all the defaults.

You can't take *all* of the defaults.  Did you select the resolution that you wanted?

You could also use the [online generator]("http://www.objorkum.com/scripts/fglrxconfig/") and use its output to replace the contents of your /etc/X11/xorg.conf file.

---

### Post by Pablo_Escobar on 2005-10-17
[QUOTE=mincho]mlomker ,
  i ve done already you just say in your but still no change in my resolution i take all the defaults. but no change tell me the correct way please.
                       thanks[/QUOTE]

You can edit xorg.conf file. Scroll down when they are resolutions typed with corresponding colour depths. If You're using 24bit depth (default) then make sure You have "1024x768" in that line.

If it's any more problem post Your xorg.conf here.

---

### Post by mincho on 2005-10-17
Here is my Xorg.conf file. please guide me that which thing i have to change in this file.please post here the edited version of this file please.

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Dell"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
	Monitor		"Dell"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by mincho on 2005-10-17
the one more thing,
  is the installation of g++-3.4 and g++-4.0 is essiential for this driver.
             thanks
 please post the edited version of my xorg.conf for only 1024x768 resolution.

---

### Post by Pablo_Escobar on 2005-10-17
Heh mincho, about g++-3.4 and g++-4.0 - I really don't know, it worked for me :) Maybe mlomker will make more of what really makes it work.

xorg.conf :

Looks ok, maybe try to find you monitor specs and change

Section "Monitor"
Identifier "Dell"
Option "DPMS"
EndSection

into

Section "Monitor"
Identifier "Dell"
HorizSync ...-...
VertRefresh ...-...
Option "DPMS"
EndSection


Insted of dots place the specifications of Your monitor. Mine for example
HorizSync 40-96
VertRefresh 50-160

Maybe that'll work.

---

### Post by mincho on 2005-10-17
it does'nt work with me.
     please tell me the other way....
                           mlomker where are you my brother tell me what i do....
 but thanks for your advise pablo..

---

### Post by jimmy41 on 2005-10-19
I was having the same problem with my 9550 and 32-bit cpu.

I listened to pablo and mlomker and had success.

Not sure what did it, but here's what I did.

using Synaptic, I removed fglrx-6-8-0 and added fglrx-control.
I also installed/reinstalled all the G++ libraries (g++, 3.3, 3.4, and 4).

Then I followed mlomker's installation how-to.

After reboot:
```

james@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

```

Thanks for the help!

---

### Post by mlomker on 2005-10-19
[QUOTE=mincho]Here is my Xorg.conf file. please guide me that which thing i have to change in this file.please post here the edited version of this file please.[/QUOTE]

It that's your current file and you are running Breezy then the system shouldn't even start--your font paths are wrong.  I recommend using the online generator that I suggested in my last post to create a new file.

---

### Post by norrbaggen on 2005-10-20
Hi,
Great easy and quick for a linux noob as me. I didn't get as much fps but it's ok. How do i see if 3d acceleration is really on? Any other settings in xorg.conf that I can change agp settings atc. It says that is uses PCI:0:1 someting.

norrbaggen@Linea:~$ glxgears -printfps
5788 frames in 5.0 seconds = 1157.546 FPS
5947 frames in 5.0 seconds = 1189.370 FPS
5888 frames in 5.0 seconds = 1177.589 FPS
5888 frames in 5.0 seconds = 1177.434 FPS
5888 frames in 5.0 seconds = 1177.533 FPS

norrbaggen@Linea:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


I got a HP Compaq nc6000 notebook, pentium M, ati mobility 9600

---

