---
title: "Discussion: ATI fglrx driver - latest version"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by mlomker on 2005-10-14
This is the thread for discussing [the how-to]("http://ubuntuforums.org/showpost.php?p=423584") for installing the latest ATI driver that is working for Ubuntu, and troubleshooting the results.

---

### Post by ilans on 2005-10-14
Thank you

I wonder if upgrading the driver can solve my unknown ATI device ( I have
ATI RADEON 9550 - That is not recognize by the kernel) 
What do you think mlomker ?

lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

---

### Post by mlomker on 2005-10-14
> Display controller: ATI Technologies Inc: Unknown device 4173

No.  That's a lower-level problem then the video driver (hal).  That won't have any effect on the function of the driver or the card, anyway.  

If you are having a specific problem then start a thread in the Video & Sound forum and we'll take a look.

---

### Post by SilverTab on 2005-10-14
[QUOTE=mlomker]No.  That's a lower-level problem then the video driver (hal).  That won't have any effect on the function of the driver or the card, anyway.  

If you are having a specific problem then start a thread in the Video & Sound forum and we'll take a look.[/QUOTE]


hey there, just to let you know that apprently, I have the exact same problem as ilans, and the same card (radeon 9550)

thats why nothing was working when you were trying to help me ;(

---

### Post by mlomker on 2005-10-14
> thats why nothing was working when you were trying to help me ;(

Well, if you want to try the new driver then give it a shot.  I wonder if it isn't a matter of using an [alternative Chipid value,]("http://www.rage3d.com/board/showthread.php?t=33803295")though.

I spent about 10 hours figuring out how to get this one installed.  Ubuntu has made a lot of changes to how both the restricted drivers work and the locations of all of the Mesa-related files.  That's a part of their work on modularizing Xorg.

---

### Post by SilverTab on 2005-10-14
[QUOTE=mlomker]Well, if you want to try the new driver then give it a shot.  I wonder if it isn't a matter of using an [alternative Chipid value,]("http://www.rage3d.com/board/showthread.php?t=33803295")though.

I spent about 10 hours figuring out how to get this one installed.  Ubuntu has made a lot of changes to how both the restricted drivers work and the locations of all of the Mesa-related files.  That's a part of their work on modularizing Xorg.[/QUOTE]


mm could be!...I'll follow the thread on Rage3d

---

### Post by ilans on 2005-10-14
[QUOTE=mlomker]

If you are having a specific problem then start a thread in the Video & Sound forum and we'll take a look.[/QUOTE]

I just did it:
[http://ubuntuforums.org/showthread.php?p=411649#post411649](http://ubuntuforums.org/showthread.php?p=411649#post411649)

---

### Post by Cloud[01] on 2005-10-14
gosh if it has worked!!!!

finished with that 1024/768 problem :)

great job and great how-to... And how fast!!! Just noticed the error and then in some hours found this post!!!

THANK YOU!

ciop ciop

---

### Post by eightysix on 2005-10-14
Hey guys, could you help me out? I keep getting this error:

```
eightysix@hikaru:/lib/modules/fglrx/build_mod$ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
eightysix@hikaru:/lib/modules/fglrx/build_mod$ cd /lib/modules/fglrx/build_mod eightysix@hikaru:/lib/modules/fglrx/build_mod$ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h

```

Any solutions?

---

### Post by mlomker on 2005-10-14
> file: /usr/src/linux/include/linux/version.h


Are you running 32-bit or amd64?  That's a reference to a linux source file, which shouldn't be needed with this new driver.  Did you do the build-dep step to download the kernel headers?

[Here's a how-to]("http://ubuntuforums.org/showpost.php?p=361253&postcount=10") for installing the kernel source, in case you need it.

---

### Post by souled on 2005-10-14
So, does this fix the 3d Rendering problems?

---

### Post by eightysix on 2005-10-14
[QUOTE=mlomker]Are you running 32-bit or amd64?  That's a reference to a linux source file, which shouldn't be needed with this new driver.  Did you do the build-dep step to download the kernel headers?

[Here's a how-to]("http://ubuntuforums.org/showpost.php?p=361253&postcount=10") for installing the kernel source, in case you need it.[/QUOTE]

I'm running AMD64. I'm downloading the kernel source right now, but it looks like it'll take a while because of all the people updating to Breezy.

---

### Post by mlomker on 2005-10-14
[QUOTE=souled]So, does this fix the 3d Rendering problems?[/QUOTE]

What problem?  This is a how-to to install the drivers in a working order, of course.  ;)

---

### Post by mlomker on 2005-10-14
> I'm running AMD64. I'm downloading the kernel source right now, but it looks like it'll take a while because of all the people updating to Breezy.

I could *not* get these drivers to work on amd64.  My box was an upgrade from Hoary to Breezy, so maybe it was just borked.  Do let me know if it works out.  The previous drivers did require the full source but ATI supposedly fixed that with this version.

I decided to switch to 32-bit this morning because there are just too many hassles and most of the people that I support on here are 32-bit.

---

### Post by eightysix on 2005-10-14
[QUOTE=mlomker]I could *not* get these drivers to work on amd64.  My box was an upgrade from Hoary to Breezy, so maybe it was just borked.  Do let me know if it works out.  The previous drivers did require the full source but ATI supposedly fixed that with this version.

I decided to switch to 32-bit this morning because there are just too many hassles and most of the people that I support on here are 32-bit.[/QUOTE]

I was trying to get the ATI drivers to work under Hoary with my Radeon 8500, but no avail. I was hoping that upgrading to Breezy would work. I'll let you know how it turns out.

I blame ATI. :mad:

---

### Post by CORE_ZSUL on 2005-10-15
Anybody know other link to download the Xorg 6.8 driver in RPM format ??

I can't download from ATI site.

Problem too: "wget http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.12.10-1.i386.rpm"

---

### Post by mlomker on 2005-10-15
> I can't download from ATI site.


They recently disabled the link that you mentioned because they switched to Akamai.  [Try this one.]("https://a248.e.akamai.net/f/674/9448/0/dlmdownloads.ati.com/drivers/linux/fglrx_6_8_0-8.18.6-1.i386.rpm")

---

### Post by CORE_ZSUL on 2005-10-15
[QUOTE=mlomker]They recently disabled the link that you mentioned because they switched to Akamai.  [Try this one.]("https://a248.e.akamai.net/f/674/9448/0/dlmdownloads.ati.com/drivers/linux/fglrx_6_8_0-8.18.6-1.i386.rpm")[/QUOTE]

I try, but.... :(

I'm moved to [http://www.ati.com/online/403/leech.asp](http://www.ati.com/online/403/leech.asp)

And I change:  If you use a mozilla based browser (Mozilla, Firefox or Netscape Navigator), referrer sending can also be deactivated (it is activated by default). To change that setting, browse to "about:config", then search for "network.http.sendRefererHeader". If the value is set to 1, referrer sending is enabled, if it is set to 0, it is disabled. To enable it, double click on it, then change the value.

But... :-x

---

### Post by mlomker on 2005-10-15
> 
I'm moved to [http://www.ati.com/online/403/leech.asp](http://www.ati.com/online/403/leech.asp)


They are making it almost impossible to write a how-to.  You'll just have to go to [http://support.ati.com](http://support.ati.com) and navigate to the driver on your own, I guess.

---

### Post by Septor on 2005-10-15
For those interested in Ubuntu packages of the driver, I submitted a patch for the ati-installer that will now correctly generate Ubuntu .debs.  You can find the patch and instructions on how to use it at: [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)
I have tested it on my Breezy system without problems.

---

### Post by mlomker on 2005-10-15
> I have tested it on my Breezy system without problems.

It is the users on amd64 that are having the most problems right now with Breezy's and the new drivers.  It only took me a few hours to find a working process for 32-bit.

Has it been tested on 64-bit?  I'm not willing to reload again on my box...takes too long.

---

### Post by Anchovie on 2005-10-15
I did everything but I still get "mesa" from fglrxinfo, any ideas? I'm running on Mobility Radeon 9000.

---

### Post by mlomker on 2005-10-15
> I did everything but I still get "mesa" from fglrxinfo, any ideas? I'm running on Mobility Radeon 9000.

The main issue is library linking.  What is the output of:

```

ldd /usr/bin/glxinfo

```

You could also look at post #20, but I haven't tested it.

---

### Post by Anchovie on 2005-10-15
ldd /usr/bin/glxinfo outputs...

```
linux-gate.so.1 =>  (0xffffe000)
libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e9f000)
libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e29000)
libglut.so.3 => /usr/lib/libglut.so.3 (0xb7dff000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ddd000)
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7caf000)
libX11.so.6 => /usr/lib/libX11.so.6 (0xb7bef000)
libXext.so.6 => /usr/lib/libXext.so.6 (0xb7be2000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7bd0000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7bcc000)
libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7ae6000)
libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7adb000)
/lib/ld-linux.so.2 (0xb7f4b000)
libXau.so.6 => /usr/lib/libXau.so.6 (0xb7ad8000)
libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7ad4000)
```

Do I have to uninstall what I installed before attempt steps in post #20?

---

### Post by mlomker on 2005-10-15
> Do I have to uninstall what I installed before attempt steps in post #20?

I have no idea.  If someone confirms that it works then we'll write a new how-to using the .deb file.

Your ldd output looks correct.  That's really weird.  You are running 32-bit, right?  I don't know of anyone that has it working on amd64 right now.

**ldd /usr/X11R6/bin/fglrxinfo** also points to the correct file?

```

mlomker@mlomkernote:/$ ls -l /usr/X11R6/lib/libGL.so.1*
lrwxrwxrwx  1 root root     12 2005-10-14 14:20 /usr/X11R6/lib/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x  1 root root 773466 2005-10-11 12:49 /usr/X11R6/lib/libGL.so.1.2

```

---

### Post by Anchovie on 2005-10-15
ldd /usr/X11R6/bin/fglrxinfo outputs...

```
linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e77000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7db7000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7da9000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c7b000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c69000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c66000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c63000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c5f000)
        /lib/ld-linux.so.2 (0xb7f23000)
```

ls -l /usr/X11R6/lib/libGL.so.1* outputs...

```
lrwxrwxrwx  1 root root     12 2005-10-15 06:34 /usr/X11R6/lib/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x  1 root root 773466 2005-10-11 10:49 /usr/X11R6/lib/libGL.so.1.2
```

=( I'll give step 20 a try then...

EDIT: Woot! It worked after I rebooted my computer! Whoops! =P

---

### Post by shadow07 on 2005-10-17
I can say that I was having the EXACT same problems as everyone here.  The source of the problem for me:  the incorrect version of GCC.  Once I installed g++-3.4 (G++ is the Debian versio nof GCC), the driver installed just fine.  In fact, I was able to get the latest version of the ATI driver (8.18.6) installed.  BUT, I needed to get the patch for the installer from [http://ati.cchtml.com/show_bug.cgi?id=198]("http://ati.cchtml.com/show_bug.cgi?id=198")

I will post tomorrow (Monday for me) the exact steps I used to install the ATI driver.

---

### Post by souled on 2005-10-17
[QUOTE=shadow07]I can say that I was having the EXACT same problems as everyone here.  The source of the problem for me:  the incorrect version of GCC.  Once I installed g++-3.4 (G++ is the Debian versio nof GCC), the driver installed just fine.  In fact, I was able to get the latest version of the ATI driver (8.18.6) installed.  BUT, I needed to get the patch for the installer from [http://ati.cchtml.com/show_bug.cgi?id=198]("http://ati.cchtml.com/show_bug.cgi?id=198")

I will post tomorrow (Monday for me) the exact steps I used to install the ATI driver.[/QUOTE]

I tried using this patch, but I still couldn't get it to work. I await your instruction :smile:

---

### Post by Septor on 2005-10-17
[QUOTE=souled]I tried using this patch, but I still couldn't get it to work. I await your instruction :smile:[/QUOTE]

What didn't work for you?  Please let me know so I can work on it to improve it for the next release from ATI.  Before you install any of the generated .deb files I would recommend you fire up synaptic, search for fglrx and un-install all packages (should be 3-5 of them).  You should not have to uninstall linux-resitricted-modules, but you will have to compile the kernel module.  Read the bugzilla page for full instructions.

Edit:  The libstdc++5 package is required for 3D acceleration to work.  I will update the patch on bugzilla with the necessary dependencies so that this will be taken care of automatically in the future.

---

### Post by CurlyChris on 2005-10-17
Ok - I'm trying the patch for the ati installer but have a problem at stage 4 of the instructions:

```
chris@ubuntu:~/Tarballs_and_debs/fglrx-install$ ./ati-installer 8.18.6 --buildpkg Ubuntu/breezy
bash: ./ati-installer: No such file or directory
chris@ubuntu:~/Tarballs_and_debs/fglrx-install$ ./ati-installer.sh 8.18.6 --buildpkg Ubuntu/breezy
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/Tarballs_and_debs/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.18.6-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/s upport/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
        cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
 fakeroot debian/rules binary
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found
~/Tarballs_and_debs/fglrx-install
chris@ubuntu:~/Tarballs_and_debs/fglrx-install$
```

So I managed to figure out that the .sh extension was missing from the 'ati-installer' file but that's about it!

Am I doing something wrong here?

Chris

---

### Post by Pablo_Escobar on 2005-10-17
Chris - install fakeroot package via apt :)
> fakeroot: command not found

---

### Post by CurlyChris on 2005-10-17
Thanks Pablo! (obvious really.............................. :oops: )

I finally managed to get the kernel module built - I needed the kernel headers and gcc-3.4 before module-assistant would finally complete without error. :roll:

Time to start playing around with xorg.conf again............. ;) 

I'll let you know how it goes!

Chris

---

### Post by Septor on 2005-10-17
[QUOTE=CurlyChris]Thanks Pablo! (obvious really.............................. :oops: )

I finally managed to get the kernel module built - I needed the kernel headers and gcc-3.4 before module-assistant would finally complete without error. :roll:

Time to start playing around with xorg.conf again............. ;) 

I'll let you know how it goes!

Chris[/QUOTE]

Good news!  Glad it worked once you got all the (many) tools installed :)

Play with the aticonfig tool... it will edit (not create from scratch) your xorg.conf and has lots of options.  run it in a terminal with no options for a list of all possible options.

For example, I would use something like:
```

aticonfig --initial
aticonfig --overlay-type=Xv --tv-format=NTSC-JPN --desktop-setup=clone

```

Anyways, play with it.  It is much nicer than the old fglrxconfig.

---

### Post by CurlyChris on 2005-10-17
Yippee!!! :D 

```
chris@ubuntu:~$ fglrxinfo display: :0.0  screen: 0 OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FireMV 2400 PCI DDR Generic
OpenGL version string: 1.3.1014 (X4.3.0-8.18.6)

chris@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1438 frames in 5.0 seconds = 287.600 FPS
1724 frames in 5.0 seconds = 344.800 FPS
1719 frames in 5.0 seconds = 343.800 FPS
1719 frames in 5.0 seconds = 343.800 FPS
1712 frames in 5.0 seconds = 342.400 FPS
chris@ubuntu:~$

```

And I can now have my laptop screen at a luscious 1400x1050 resolution too!!

Thanks, Septor, for the patch - I can confirm it works on my Radeon Mobility 9000M!  I'm sure Half Life runs faster than it did with the old 8.6.? driver on my Hoary setup?!

Just for the record, I've not run fglrxconfig for this installation but am using the one [generated online]("http://www.objorkum.com/scripts/fglrxconfig/"), as I've never yet run an fglrxconfig on my machine that has worked!  (Oh........... and, if it matters, I'm running a Pentium M 1.5G, using Breezy.)


Edit: just seen your post, Septor!  I'll give that config tool a try, thanks!

Chris

(A happy bunny! :D )

---

### Post by souled on 2005-10-17
Couple questions before I try this again (the patch way that Septor gave). In Synaptic, when I search fglrx, right now I have linux-restricted-modules, and xserver-xorg-driver-ati (after a clean install.) So, I'm supposed to uninstall linux-restricted, but what about xserver-xorg? Do I keep that?

And does it matter what order I install the 5 .deb files?

Also, can you help me a little bit with module-assistant. I installed it last time and ran that command with module-assistant, but it said abunch of stuff and it had to install header files for the kernel I think. I had to type in 'module-assistant prepare.' Is that supposed to happen? Then I ran module-assistant a-i fglrx after it was done with the prepare thing. Is that the correct way of doing things?

Thanks for the help.

---

### Post by Septor on 2005-10-17
[QUOTE=souled]Couple questions before I try this again (the patch way that Septor gave). In Synaptic, when I search fglrx, right now I have linux-restricted-modules, and xserver-xorg-driver-ati (after a clean install.) So, I'm supposed to uninstall linux-restricted, but what about xserver-xorg? Do I keep that?
[/quote]

Actually, you can keep both of those without problems.

> 
And does it matter what order I install the 5 .deb files?

Not really, and you don't necessarily need all 5 either.  Here is the order I'd use:

xorg-driver-fglrx
fglrx-kernel-sources
fglrx-control (optional, only if you want fireglcontrolpanel installed)
fglrx-sources (optional, source code for the fireglcontrol panel)
xorg-driver-fglrx-dev (optional, only useful for developers)

> 
Also, can you help me a little bit with module-assistant. I installed it last time and ran that command with module-assistant, but it said abunch of stuff and it had to install header files for the kernel I think. I had to type in 'module-assistant prepare.' Is that supposed to happen? Then I ran module-assistant a-i fglrx after it was done with the prepare thing. Is that the correct way of doing things?

Thanks for the help.

Yes you need the "linux-headers" package for your kernel. Then change to your /usr/src directory, untar fglrx.tar.bz2 then run "module-assistant update" followed by "module-assistant a-i fglrx". "module-assistant prepare" only needs to be run once, the first time you use it.

Hope that helps!

---

### Post by grinias on 2005-10-17
[QUOTE=Septor]


Yes you need the "linux-headers" package for your kernel. Then change to your /usr/src directory, untar fglrx.tar.bz2 then run "module-assistant update" followed by "module-assistant a-i fglrx". "module-assistant prepare" only needs to be run once, the first time you use it.

Hope that helps![/QUOTE]

I think is not necessary to untar  fglrx.tar.bz2 neither to cd to /usr/src or run 
"module-assistant update"; I just ran
 
"module-assistant a-i fglrx" 

(once i had installed the packages

xorg-driver-fglrx and 
fglrx-kernel-sources)
 
to install the driver and everything worked just fine.

But i lost hibernation somehow, so I use the "ati" driver again :???:

---

### Post by Septor on 2005-10-17
> **grinias]I think is not necessary to untar  fglrx.tar.bz2 neither to cd to /usr/src or run 
"module-assistant update" said:**
> 

nice, thanks for the tip!

[quote]
But i lost hibernation somehow, so I use the "ati" driver again :???:
There is a work-around with vbetool apparently.  I'd check out the Rage3D.com forums for more info: [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)

---

### Post by hackyou on 2005-10-17
I love you! :D 
Everything now works!
Thanks Thanks Thanks

---

### Post by screamingFit on 2005-10-17
HUGE thanks for the HOW-TO and all the hard work!

Got my Dell Inspiron 8600 with ATI Radeon Mobility 9600 128MB working great!

The only problem I had was during the monitor detection - it "melted" my screen.  Just hard-booted and ran through it again without choosing monitor detection and it ran flawless.

---

### Post by mindwarp on 2005-10-17
I followed all of the steps but I am getting no 3d acceleration.

Xorg says (a bunch):
```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
```

and 

and fglrxinfo says:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Running on a Radeon 9600, works fine with last driver just not the correct resolution.

---

### Post by bluck on 2005-10-17
[QUOTE=eightysix]Hey guys, could you help me out? I keep getting this error:


Any solutions?[/QUOTE]

i would suspect you need the kernel-package (or am i thinking kernel-source?) installed.

---

### Post by puccaso on 2005-10-17
hi folks, what do these mean...

```
mahir@jt:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

everything seems ok...
the fglrx driver works (or seems to)
but when i do 

```
mahir@jt:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square,
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
mahir@jt:~$
```


it says DRI no.. why does it do this?!
glxgears is UBER slow!

help please!

---

### Post by mlomker on 2005-10-17
Hi guys/gals.  I just wanted to let you know that I am not ignoring you.  Actually, I spent about four hours doing two clean installs of Breezy on my laptop to confirm that my how-to is correct...and it is 100% right on my machine, anyway.

I also spent **another** 6 hours trying to get the drivers to install on 64-bit and it looks impossible at the moment....well, beyond my abilities anyway.

I'm going to reload my box with 32-bit one more time this evening and try the .deb approach.  If it is solid then I'll rewrite the how-to for it.

---

### Post by souled on 2005-10-17
Hmm, when doing ./ati-installer 8.18.6 --buildpkg Ubuntu/breezy, I get this output:
```
Generating package: Ubuntu/breezy
/tmp/fglrx ~/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.18.6-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
        cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
make: dh_testdir: Command not found
make: *** [configure] Error 127
~/fglrx-install

```

Why am I getting this error?

---

### Post by souled on 2005-10-17
Ok, I installed debhelper, and I was able to get a little further in running ./ati-installer 8.18.6 --buildpkg Ubuntu/breezy:
```
Generating package: Ubuntu/breezy
/tmp/fglrx ~/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.18.6-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/s upport/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
make: Entering directory `/tmp/fglrx'
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
        cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
make: Leaving directory `/tmp/fglrx'
 fakeroot debian/rules binary
make: Entering directory `/tmp/fglrx'
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
        cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
        usr/lib \
        usr/X11R6 \
        usr/X11R6/lib \
        usr/X11R6/lib/modules \
        usr/share/fglrx/diversions
dh_installdirs -pxorg-driver-fglrx-dev \
        usr/include \
        usr/lib
dh_installdirs -pfglrx-kernel-source \
        usr/src/modules/fglrx \
        usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
        usr/bin \
        usr/share \
        usr/share/applnk \
        usr/share/gnome \
        usr/share/gnome/apps \
        usr/share/icons \
        usr/share/pixmaps
dh_installdirs -pfglrx-sources \
        usr/src
dh_install
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*" "usr/X11R6/lib/modules"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib/*.a"   "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
dh_install -pfglrx-kernel-source \
lib/modules/fglrx/build_mod/*.c            \
        lib/modules/fglrx/build_mod/*.h            \
        lib/modules/fglrx/build_mod/*.sh           \
        lib/modules/fglrx/build_mod/lib*           \
        lib/modules/fglrx/build_mod/2.6.x/Makefile \
        usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debia n"
dh_install -pfglrx-kernel-source  \
        debian/copyright        \
        debian/compat           \
        module/rules            \
        module/control.template \
        module/dirs.template    \
        module/postinst         \
        usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
 && chown -R root:src modules \
 && tar -c modules | bzip2 > fglrx.tar.bz2 \
 && rm -rf modules)
# install panel files
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel"     "usr/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/ico ns"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/pix maps"
dh_install -A -pfglrx-control "usr/share/gnome/apps/fireglcontrol.desktop" "usr/share/gnome/apps"
dh_install -A -pfglrx-control "usr/share/applnk/fireglcontrol.kdelnk" "usr/share /applnk"
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneed ed debian/xorg-driver-fglrx/usr/lib/libfglrx_gamma.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneed ed debian/xorg-driver-fglrx/usr/lib/libfglrx_pp.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneed ed debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneed ed debian/xorg-driver-fglrx/usr/X11R6/lib/modules/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneed ed debian/xorg-driver-fglrx/usr/X11R6/lib/modules/dri/atiogl_a_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-dr iver-fglrx/usr/bin/fgl_glxgears
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-dr iver-fglrx/usr/bin/fglrx_pplay
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-dr iver-fglrx/usr/bin/fglrx_xgamma
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-dr iver-fglrx/usr/bin/fglrxconfig
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-dr iver-fglrx/usr/bin/fglrxinfo
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-dr iver-fglrx/usr/bin/aticonfig
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx/usr/X11R6/lib/modules/li nux/libfglrxdrm.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libaticonfig .a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_gam ma.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_pp. a
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/fglrx-c ontrol/usr/bin/fireglcontrolpanel
dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i386-linux/lib/libc.so.6 not found.
dpkg: /usr/i386-linux/lib/libXext.so.6 not found.
dpkg: /usr/i386-linux/lib/libX11.so.6 not found.
dpkg: /usr/i386-linux/lib/libpthread.so.0 not found.
dpkg: /usr/i386-linux/lib/libdl.so.2 not found.
dpkg: /usr/i386-linux/lib/libm.so.6 not found.
dpkg: /usr/i386-linux/lib/libstdc++.so.5 not found.
dpkg: /usr/i386-linux/lib/librt.so.1 not found.
dpkg: /usr/i386-linux/lib/libGL.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx'
~/fglrx-install

```

Now what?

---

### Post by mlomker on 2005-10-17
> Now what?

No kidding.  It took me 3 hours to figure out the dependencies and the proper command-lines for generating them.  I really appreciate Septor's work on this but you know what they say about programmers and the ability to write documentation....  :D

```

sudo apt-get install build-essential fakeroot dh-make debconf

```

Now I'll see if they work...and start documenting things.

---

### Post by souled on 2005-10-17
Installed those packages, but I get the same output as before.

Before I did a fresh install of Breezy, I was able to get past this part, but for some reason I'm stuck here. I'm not exactly sure what I did differently in the last install....

---

### Post by Septor on 2005-10-17
[QUOTE=souled]Ok, I installed debhelper, and I was able to get a little further in running ./ati-installer 8.18.6 --buildpkg Ubuntu/breezy:
```
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i386-linux/lib/libc.so.6 not found.
dpkg: /usr/i386-linux/lib/libXext.so.6 not found.
dpkg: /usr/i386-linux/lib/libX11.so.6 not found.
dpkg: /usr/i386-linux/lib/libpthread.so.0 not found.
dpkg: /usr/i386-linux/lib/libdl.so.2 not found.
dpkg: /usr/i386-linux/lib/libm.so.6 not found.
dpkg: /usr/i386-linux/lib/libstdc++.so.5 not found.
dpkg: /usr/i386-linux/lib/librt.so.1 not found.
dpkg: /usr/i386-linux/lib/libGL.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1

```

Now what?[/QUOTE]

I don't know why dpkg is looking in /usr/i386-linux/lib ... does that directory even exist?  Something in dpkg seems wonky on your side. Anyone have any ideas about this?

---

### Post by souled on 2005-10-17
I'm doing a fresh install now haha. When I'm done installing, do you remember what the dependency files I need to install are?

---

### Post by Septor on 2005-10-17
> **mlomker]No kidding.  It took me 3 hours to figure out the dependencies and the proper command-lines for generating them.  I really appreciate Septor's work on this but you know what they say about programmers and the ability to write documentation....  :D
[/quote]
Ouch!  said:**
> 
```

sudo apt-get install build-essential fakeroot dh-make debconf

```

Now I'll see if they work...and start documenting things.

You'll need at least "linux-headers" (I think that is the package name) to compile the kernel module as well.  And "module-assistant" is a nice, easy way to compile and install the kernel module so get that too :)

---

### Post by souled on 2005-10-17
YAY! I've sucessfully ran the buildpkg command finally! After I reinstalled, I installed the linux-header files, then it worked. WOO. Ok, so I finished running the module-assistant. Do I have to run aticonfig in order to start using the fglrx drivers?

When I run fglrxinfo I still get the Mesa stuff, am I missing something?

---

### Post by Septor on 2005-10-17
[QUOTE=souled]YAY! I've sucessfully ran the buildpkg command finally! After I reinstalled, I installed the linux-header files, then it worked. WOO. Ok, so I finished running the module-assistant. Do I have to run aticonfig in order to start using the fglrx drivers?

When I run fglrxinfo I still get the Mesa stuff, am I missing something?[/QUOTE]

If you don't have your xorg.conf updated yet, then run
```

aticonfig --initial

```

That should fix up your xorg.conf for fglrx.  If you have problem please post your /var/log/Xorg.0.log and /etc/X11/xorg.conf or read through some of the threads on [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)

---

### Post by souled on 2005-10-18
Ahh I had to restart my computer to get the ATI Technologies stuff seen. Thanks a bunch Septor and mlomker. I appreciate all of the help. 

One last question. I get this error when trying to run the ATI Control. 'Details: Failed to execute child process "/usr/X11R6/bin/fireglcontrolpanel" (No such file or directory)"

---

### Post by mlomker on 2005-10-18
> You'll need at least "linux-headers" (I think that is the package name) to compile the kernel module as well.  And "module-assistant" is a nice, easy way to compile and install the kernel module so get that too 

Actually, the **module-assistant prepare** step takes care of that.  More docs to follow.

I took the time to try the whole process on 64-bit as well and it's still no-good.  They changed something fundamental about where files are placed.  I couldn't even get 2D until I moved two files to the proper directories: fglrxdrm.a and fglrx_drv.o.  Interestingly, fglrx did not show up in the dpkg-reconfigure xserver-xorg but it does for i386.  Even with those files in the proper directories you still end up with Mesa on the 3D side.

I'll also have to disagree with you about the removal of restricted-modules.  The modules in /lib/mod/kernversion/volatile always over-ride your generated fglrx.ko if that package is installed.

---

### Post by mlomker on 2005-10-18
Edit: How-to's were moved to [their own thread]("http://ubuntuforums.org/showthread.php?p=423589&posted=1#post423589").

---

### Post by rmerry on 2005-10-18
Doh! Just finished the first method ;)

Anyway bug exists with asus l5800c as per my post (although it locks to 1280x1024)
[http://ubuntuforums.org/showthread.php?p=422230](http://ubuntuforums.org/showthread.php?p=422230)

Fixed the problem, thank you :)

---

### Post by Septor on 2005-10-18
[QUOTE=mlomker]Actually, the **module-assistant prepare** step takes care of that.  More docs to follow.

I took the time to try the whole process on 64-bit as well and it's still no-good.  They changed something fundamental about where files are placed.  I couldn't even get 2D until I moved two files to the proper directories: fglrxdrm.a and fglrx_drv.o.  Interestingly, fglrx did not show up in the dpkg-reconfigure xserver-xorg but it does for i386.  Even with those files in the proper directories you still end up with Mesa on the 3D side.
[/quote]

I think I'll break down and install 64bit Ubuntu tonight on my spare partition, for testing at least.  I should be able to get things working, and when I do I'll post a new patch for the installer.

> 
I'll also have to disagree with you about the removal of restricted-modules.  The modules in /lib/mod/kernversion/volatile always over-ride your generated fglrx.ko if that package is installed.

Noted.  I'll add a diversion for that module or something so it gets moved out of the way automatically when the fglrx-kernel package is built/installed.

Thanks all for the package feedback... I only have 1 Ubuntu system, so all of your experiences really help me improve the state of things greatly.

---

### Post by Septor on 2005-10-18
[QUOTE=souled]Ahh I had to restart my computer to get the ATI Technologies stuff seen. Thanks a bunch Septor and mlomker. I appreciate all of the help. 

One last question. I get this error when trying to run the ATI Control. 'Details: Failed to execute child process "/usr/X11R6/bin/fireglcontrolpanel" (No such file or directory)"[/QUOTE]

The menu shortcut probably has the wrong path, fireglcontrolpanel is now in /usr/bin... you should be able to run the command manually from a terminal just fine though.

---

### Post by souled on 2005-10-18
[QUOTE=Septor]The menu shortcut probably has the wrong path, fireglcontrolpanel is now in /usr/bin... you should be able to run the command manually from a terminal just fine though.[/QUOTE]

Awesome. Everything works now! Thanks again for all of your help!

---

### Post by Schizoid on 2005-10-18
if you on x86_64 try running this

```
LIBGL_DEBUG=verbose fglrxinfo
```

if you ca you can see
```

libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/atiogl_a_dri.so
[COLOR="Red"]fglrx: libGL version does not match - OpenGL module is using glapi fallback[/COLOR]
libGL: XF86DRIGetClientDriverName: 8.16.20 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

either way try to take your posts over to the Ati threads on the Amd64 forum

---

### Post by mumbly58 on 2005-10-18
My system : 
laptop ACER Aspire 5024 - Turion 64bits ML-34 - 1Go - ATI Radeon Mobility X700 (RV410) PCI Express - UBUNTU Breezy Badger (fresh install) AMD64

Trying to configure this Ati 3D driver for days !
The fglrx driver works but in 2D and in a 1024x768 resolution.


Got this :

~$ LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.16.20 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.16.20 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
libGL error: drmMap of framebuffer failed < ---------------> What is that ?
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

~$ fgl_glxgears
libGL error: drmMap of framebuffer failed
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  39
  Current serial number in output stream:  39

Thanx in advance for your help.

---

### Post by Septor on 2005-10-18
[QUOTE=mumbly58]My system : 
laptop ACER Aspire 5024 - Turion 64bits ML-34 - 1Go - ATI Radeon Mobility X700 (RV410) PCI Express - UBUNTU Breezy Badger (fresh install) AMD64

Trying to configure this Ati 3D driver for days !
The fglrx driver works but in 2D and in a 1024x768 resolution.


Got this :

~$ LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.16.20 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.16.20 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
libGL error: drmMap of framebuffer failed < ---------------> What is that ?
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

~$ fgl_glxgears
libGL error: drmMap of framebuffer failed
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  39
  Current serial number in output stream:  39

Thanx in advance for your help.[/QUOTE]

8.16.20 has a resolution bug.  Try 8.14 or the new 8.18.

---

### Post by mlomker on 2005-10-18
> Noted.  I'll add a diversion for that module or something so it gets moved out of the way automatically when the fglrx-kernel package is built/installed.


If  diversion is just a file delete/rename then I don't know if that'll be adequate.  There's something funny about how that package works.  You can **rm *** the contents of that /volatile directory and it'll come back on reboot.  I think it is related to the /etc/init.d/S15linux-restricted-modules-common and S20module-init-tools scripts.  The modules also end up in some sort of ramdisk filesystem called **tmpfs** and nothing can be deleted from there.

> 
I think I'll break down and install 64bit Ubuntu tonight on my spare partition, for testing at least. I should be able to get things working, and when I do I'll post a new patch for the installer.

You would become extremely popular around here if you could figure that out!  As it stands even Breezy's included 8.16.20 driver will not function on a clean install.  I had it working on a Hoary->Breezy upgrade but once I reloaded I also couldn't get it back...I've spent over a day trying the things that I can understand (deleting files, symlinking to other libraries, etc).

---

### Post by mlomker on 2005-10-18
[QUOTE=rmerry]Doh! Just finished the first method ;)
[/QUOTE]

I'd prefer that people try the initial way first because it's a lot easier than generating those .deb files.  I don't know how long I'll be able to host the finished .debs because I can't afford to have it slow down my company's Internet connection.  If the load turns out to not be too bad then I'll leave them up.

---

### Post by kroiz on 2005-10-18
Hi,
I was having a lot of problems after I made a mess following to many guides simulatnasly.
So I reinstalled breezy and followed *mlomker* first method, every thing went fine, or atleast that is what I thought, because I got no errors, but after reboot, **glxgears -info** I still reports mesa driver.
Any idea what shoud I look for now?
are there any logs I can check out?

---

### Post by floyd27 on 2005-10-18
Hi..
I used your method in 5.04 and it was the only one that ever worked..
I had to delete EVERY fglrx file as stated in one of the steps..
However this step is not in the new guide??
Is this no longer necessary?
thanx

---

### Post by floyd27 on 2005-10-18
Guide worked perfect FIRST try....WOW
Thanx again......

i do have a Q for you..
in linspire that ati drivers are installed stock....I get 4000+ with ubuntu
and 4300+ with linspire...
I wonder what the difference is?

---

### Post by burok on 2005-10-19
This is my way installing **[COLOR="Blue"]ATI[/COLOR]** drivers :D

Ubunutu 5.10 (fresh install)
ati-driver-installer-8.18.6-i386.run

1. apt-get install build-essential
2. apt-get install linux-headers-2.6.12-9
3. apt-get install linux-headers-2.6.12-9-386
4. apt-get install gcc-3.4
5. apt-get install libstdc++5

6. rm -rf /lib/linux-restricted-modules/2.6.12-9-386/fglrx/
7. rm -f /lib/modules/2.6.12-9-386/volatile/fglrx.ko

8. sh ati-driver-installer-8.18.6-i386.run

9. /usr/X11R6/bin/fglrxconfig 
Do you want to initialize xfree86-dga (y/n)? [n] **y**
Do you want to use the external AGP GART module (y/n)? [n] **y**

10. reboot

glxinfo:
[COLOR="Red"]**direct rendering: Yes**[/COLOR]

---

### Post by kroiz on 2005-10-19
ok I reinstalled breezy and followed the second method.
but I'm stuck again, the make_install does not work for me.
```

kroiz@ubuntu:/lib/modules/fglrx$ [COLOR="Purple"]sudo sh make_install.sh[/COLOR]
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/ fglrx.ko): Operation not permitted
failed.

```

I lookeded in the make_install.sh and it seem that the problem is when the scripts is trying to make modprobe.
Any idea why whould modprobe say such a thing?

---

### Post by ilans on 2005-10-19
[QUOTE=burok]

glxinfo:
[COLOR="Red"]**direct rendering: Yes**[/COLOR][/QUOTE]

Do you have 3D acceleration ?
What is your  output to 'fglrxino' command ?

Anyway, I followed the new How-To (with the new Deb files) But still get
Mesa in fglrxinfo command (and of course no 3D acceleration at all). 
My video card is:  ATI 9550

---

### Post by derrick1985 on 2005-10-19
I just wanted to say that this HOWTO worked great and perfectly for me. Running on a 686 kernel.

derrick@Drock:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

derrick@Drock:~$ dmesg | grep fglrx
[4296068.234000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4296068.239000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4296068.239000] [fglrx] module loaded - fglrx 8.18.6 [Oct 11 2005] on minor 0
[4296068.253000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4296068.253000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4296068.253000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4296068.253000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4296068.254000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4296068.264000] [fglrx] free  AGP = 252440576
[4296068.264000] [fglrx] max   AGP = 252440576
[4296068.264000] [fglrx] free  LFB = 122679296
[4296068.264000] [fglrx] max   LFB = 122679296
[4296068.264000] [fglrx] free  Inv = 134217728
[4296068.264000] [fglrx] max   Inv = 134217728
[4296068.264000] [fglrx] total Inv = 134217728
[4296068.264000] [fglrx] total TIM = 0
[4296068.264000] [fglrx] total FB  = 0
[4296068.264000] [fglrx] total AGP = 65536

derrick@Drock:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
8875 frames in 5.0 seconds = 1774.890 FPS
8755 frames in 5.0 seconds = 1750.817 FPS
8636 frames in 5.0 seconds = 1727.135 FPS
8810 frames in 5.0 seconds = 1761.928 FPS
8711 frames in 5.0 seconds = 1742.029 FPS
8730 frames in 5.0 seconds = 1745.977 FPS
8697 frames in 5.0 seconds = 1739.208 FPS
8814 frames in 5.0 seconds = 1762.775 FPS
8770 frames in 5.0 seconds = 1753.865 FPS
8714 frames in 5.0 seconds = 1742.773 FPS



THANK YOU!

---

### Post by burok on 2005-10-19
[QUOTE=ilans]Do you have 3D acceleration ?[/QUOTE]

Yes 3D acceleration working very well.
 
[QUOTE=ilans]What is your  output to 'fglrxino' command ?[/QUOTE]

burok@ubuntu:/media/hd/ut2004$ /usr/X11R6/bin/fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 DDR Generic
OpenGL version string: 1.3.1014 (X4.3.0-8.18.6)

[QUOTE=ilans]Anyway, I followed the new How-To (with the new Deb files) But still get
Mesa in fglrxinfo command (and of course no 3D acceleration at all). 
My video card is:  ATI 9550[/QUOTE]

Try my 10 steps on fresh installed Ubuntu Breezy Badger 5.10. 

Take attention to this

apt-get install gcc-3.4
apt-get install libstdc++5
rm -rf /lib/linux-restricted-modules/2.6.12-9-386/fglrx/
rm -f /lib/modules/2.6.12-9-386/volatile/fglrx.ko

---

### Post by mlomker on 2005-10-20
> rm -rf /lib/linux-restricted-modules/2.6.12-9-386/fglrx/ rm -f /lib/modules/2.6.12-9-386/volatile/fglrx.ko That's identical to my how-to. You're just removing the linux-restricted-modules-$(uname -r) by deleting its contents rather than removing it. An approach that I would not recommend because it'll reinstall those files on next kernel update (unless you lock the package in Synaptic)...but why go through all of that effort when you could just remove it?

---

### Post by Dracontopes on 2005-10-21
Whoop got it working finally with this guide, good job!
I always install ati drivers on ubuntu (kubuntu) has always been the same, but for this release. :) 

Updating paths and upgrading library cache, I'd never think of that lol :P (too much a noob)

---

### Post by burok on 2005-10-21
[QUOTE=mlomker]That's identical to my how-to. You're just removing the linux-restricted-modules-$(uname -r) by deleting its contents rather than removing it. An approach that I would not recommend because it'll reinstall those files on next kernel update (unless you lock the package in Synaptic)...but why go through all of that effort when you could just remove it?[/QUOTE]

Yes, ur right. I'm noob :rolleyes:

I do it like that and finaly ATI works :)

sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.12-9
sudo apt-get install linux-headers-2.6.12-9-386
sudo apt-get install gcc-3.4
sudo apt-get install libstdc++5
sudo apt-get remove linux-restricted-modules-$(uname -r)

reboot.

sudo sh ati-driver-installer-8.18.6-i386.run 
sudo /usr/X11R6/bin/fglrxconfig 

reboot.

:)

---

### Post by mlomker on 2005-10-22
> 
sudo sh ati-driver-installer-8.18.6-i386.run 
sudo /usr/X11R6/bin/fglrxconfig 


Yup, that approach should work once Septor's patches get into ATI's installer.  At the time that I wrote this how-to the file paths were wrong and it wasn't that easy...**fglrxinfo** and other tools were not getting into /usr/bin like they should.

---

### Post by monkeyface on 2005-10-22
It doesn't work for me either.
A "modprobe fglrx" gives me "FATAL: Could not open '/lib/modules/2.6.12-9-k7/volatile/fglrx.ko': No such file or directory" and fglrxinfo says Mesa indirect...

I've built my own packages using the ATI installer instead of your prebuilt packages, can that be the reason ? :)

EDIT: Have gcc-3.4 installed, libstdc++5 and everything from the build-essential package plus fakeroot and such.. All linux-restricted-modules is removed and linux-headers is installed... I have a Radeon 9700 PRO.

---

### Post by Navyblue on 2005-10-22
Hi guys,

I have followed the .deb method and X can't even start if fglrx is selected. :( The error message seems to be the same as using the fglrx driver from the repository. Btw I am running Sapphire ATI Radeon 9550 on 64 bit Kubuntu.

This is a portion of Xorg.0.log which I think is relevant, I'm not sure which part is relevant but I don't want to post the whole chunk here.

```

(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure

```

Please tell me what other information that you'll need.

Thanks in advance.

---

### Post by mlomker on 2005-10-22
> EDIT: Have gcc-3.4 installed, libstdc++5 and everything from the build-essential package plus fakeroot and such.. All linux-restricted-modules is removed and linux-headers is installed... I have a Radeon 9700 PRO.

Try:

```

sudo depmod -ae

```

Also verify the fglrx.ko is in the right place--the last line here being the key.

```

mlomker@mlomkernote:/$ sudo updatedb
mlomker@mlomkernote:/$ locate fglrx.ko
/lib/modules/fglrx/fglrx.ko
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd
/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
/lib/modules/fglrx/build_mod/fglrx.ko
/lib/modules/2.6.12-9-k7/kernel/drivers/char/drm/fglrx.ko

```

---

### Post by mlomker on 2005-10-22
> 
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o


Oops.  I'll add that info to the how-to.  I had it in my other one.


**_Troubleshooting_**

**64-bit users:**

You may get this error message when you go to restart:

```

Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

```

You can fix this by editing your xorg.conf file and commenting out the libint10.a line:

```

sudo nano /etc/X11/xorg.conf

```

```

Section "Module"
#       Load    "int10"
EndSection

```

Ctrl-W, Y, Enter to save.

---

### Post by Navyblue on 2005-10-22
Thanks for your such speedy response. I can now boot with fglrx driver after weeks with ati driver.

However, from the look of OpenGL screensaver, 3d acceleration doesn't seems to be working.

fglrxinfo says:

```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

---

### Post by Navyblue on 2005-10-22
Ooops, thats because I screw up some parts of the xorg.conf. It now worked.

Thanks so much for your contributions to our community, it helped me so much :)

---

### Post by monkeyface on 2005-10-22
[QUOTE=mlomker]Also verify the fglrx.ko is in the right place--the last line here being the key.[/QUOTE]
Hmm, my fglrx.ko is in /lib/modules/2.6.12-9-k7/misc/... what can I do? Make a symbolic link or such?

---

### Post by mlomker on 2005-10-22
> Hmm, my fglrx.ko is in /lib/modules/2.6.12-9-k7/misc/... what can I do? Make a symbolic link or such?

Did you try the depmod command?

---

### Post by monkeyface on 2005-10-22
[QUOTE=mlomker]Did you try the depmod command?[/QUOTE]
The same :???:

---

### Post by mlomker on 2005-10-22
[QUOTE=monkeyface]The same :???:[/QUOTE]

The build process wouldn't put it under **misc**, so I'm not sure what the deal is there.  I'd delete the files and re-run the modules build just to be sure.

You could copy it to the /kernel/drivers/char/drm/ directory, but it just seems too odd to me.

---

### Post by KiLLeR_WoMBaT on 2005-10-23
Nothing works for me.  I have tried the HOW TO, the ATI Installer, the "patched" .deb files...everything.  I still have Mesa instead of DRI.  There has to be something I am missing.  I know that with other distros I had to compile using the kernel sources, but with ubuntu that seems to be a different process than I was used to.  Please can anyone recap how to uninstall EVERY bit of fglrx and ATI; then let me know how to reinstall the default driver that came with Breezy.  I have an ATI Radeon 9600 Pro Mobility 128MB AGP.

---

### Post by mlomker on 2005-10-23
> Please can anyone recap how to uninstall EVERY bit of fglrx and ATI

I doubt that it's possible to tell you because we don't know what you've done.  Video driver installation doesn't only effect the driver itself but the Xorg files as well (which Mesa is a part of).  You might be better off saving your stuff and reloading your box with a clean copy of Breezy.  A clean install is what all of the [how-to's]("http://ubuntuforums.org/showthread.php?p=408111") are based on.

Are you seeing errors in **dmesg | grep fglrx** or in the /var/log/Xorg.0.log?

---

### Post by kroiz on 2005-10-23
[QUOTE=KiLLeR_WoMBaT]Nothing works for me.  I have tried the HOW TO, the ATI Installer, the "patched" .deb files...everything.  I still have Mesa instead of DRI.[/QUOTE]

did you try:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATIOnBreezyOpenGLFix?highlight=%28ati%29%7C%28breezy%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATIOnBreezyOpenGLFix?highlight=%28ati%29%7C%28breezy%29)

---

### Post by souled on 2005-10-23
I'm back :( and with more problems. I recently restarted my computer... and the colors are all messed up. Maybe 16 or 8 bit color, not sure. When I used the spkg-reconfigure command, the color was fine, but everything was all messed up. The screen looked like it was all scrambled. I could read menus, but whenever I opened up a window it was all weird looking and unreadable. So, I tried aticonfig --initial and restarted Gnome, and the color problem was back. I'm guessing there's something wrong with the drivers? Any thoughts mlomker (or anyone else)?

EDIT: I moved my computer... and when I turned it back on everything is fine haha.

---

### Post by barranco on 2005-10-24
Great, thread

I'm one of those with the widescreen problem my hardware is

Toshiba M30X laptop
ATI Mobility 9600

However I also have a Atheros Wifi chip, its now working but it wont after I remove the rectricted-modules package
[PHP]sudo apt-get remove linux-restricted-modules-$(uname -r)[/PHP]

I there anyone that has been through this already that could give me a little directions?
:rolleyes: 
I've never configured the madwifi drivers myself.

---

### Post by souled on 2005-10-24
I think you can install the drivers by the .deb way without removing the restricted-modules.

---

### Post by Septor on 2005-10-24
[QUOTE=souled]
EDIT: I moved my computer... and when I turned it back on everything is fine haha.[/QUOTE]

The reason there are thumb screws on the video cable is so that it doesn't come partially/totally unplugged and mess up your screen... try them out ;)

---

### Post by Septor on 2005-10-24
[QUOTE=barranco]Great, thread

I'm one of those with the widescreen problem my hardware is

Toshiba M30X laptop
ATI Mobility 9600

However I also have a Atheros Wifi chip, its now working but it wont after I remove the rectricted-modules package
[PHP]sudo apt-get remove linux-restricted-modules-$(uname -r)[/PHP]

I there anyone that has been through this already that could give me a little directions?
:rolleyes: 
I've never configured the madwifi drivers myself.[/QUOTE]


You need the l-r-m package for the madwifi driver.  If you also want to install fglrx separately you'll have to rename the "fglrx.ko" kernel module provided by l-r-m _before_ you install the ATI driver.  Simply rename it to fglrx.ko.bak or whatever.  You'll probably find this file at: /lib/modules/2.6.12-*/volatile/fglrx.ko

Once you rename it, there should hopefully be no problems installing the ATI driver.

---

### Post by nicky75 on 2005-10-24
Thank you, the how to work great fo me:D 
Finally I have the 3D acceleration, I have Hercules 8500 DV

---

### Post by Cadbury on 2005-10-24
im using the Ubuntu Breezy Badger 5.10

when i type in: apt-get install gcc-3.4 module-assistant

i get: Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant

im more of a fedora user so i dont know much about apt-get im more usto yum

plz help :(

---

### Post by mlomker on 2005-10-24
[QUOTE=souled]I think you can install the drivers by the .deb way without removing the restricted-modules.[/QUOTE]

Not in my tests.  Please don't make comments like this in a how-to thread unless you've personally tested it.

---

### Post by mlomker on 2005-10-24
> im more of a fedora user so i dont know much about apt-get im more usto yum


You probably don't have all of the repositories added in.  Type **sudo nano /etc/apt/sources.list** and make sure all of the repo lines have *main restricted multiverse universe* on the end.  Ctrl-X, Y, Enter to save.  **sudo apt-get update** and then try the install.

---

### Post by mlomker on 2005-10-24
> You need the l-r-m package for the madwifi driver. 

What does l-r-m mean?

>  If you also want to install fglrx separately you'll have to rename the "fglrx.ko" kernel module provided by l-r-m _before_ you install the ATI driver.  Simply rename it to fglrx.ko.bak or whatever.  You'll probably find this file at: /lib/modules/2.6.12-*/volatile/fglrx.ko


As I've mentioned before, this doesn't work.  You can delete the **entire** contents of the volatile directory and it'll come back on the next reboot.  The /etc/init.d/linux-restricted-modules-common script runs something called lrm-manager at startup and the entire contents of that volatile directory are refreshed.  The /etc/init.d/module-init-tools then also runs depmod and prefers the /volatile directory modules over your installed versions.

I'm going to experiment with how to disable them but I'm always hesitant to take that approach because future kernel updates could break any temporary fix.

EDIT:  I've tried renaming /sbin/lrm-manager or disabling the script but that just results in an empty /volatile directory on reboot.

---

### Post by souled on 2005-10-24
[QUOTE=mlomker]Not in my tests.  Please don't make comments like this in a how-to thread unless you've personally tested it.[/QUOTE]

I installed the drivers using the deb packages, and I still have the linux-restricted-module installed (guessing that's what l-r-m package is), and my drivers are functioning flawlessly.

---

### Post by mlomker on 2005-10-24
> However I also have a Atheros Wifi chip, its now working but it wont after I remove the rectricted-modules package


I'm still trying to figure out a way to leave it installed but haven't got it yet.  That linux-restricted-modules packages is dynamically created on reboot so renaming files and that kind of thing doesn't work.

You could [download]("http://madwifi.org/wiki/UserDocs/GettingMadwifi") and figure out how to compile the madwifi drivers from source, of course.

If you're willing to try an experiment (should just take a couple reboots) then try this for me:

```

cd /lib/modules/$(uname -r)/volatile
sudo cp ath_hal.ko ../madwifi
sudo mv /sbin/lrm-manager /sbin/lrm-manager.old

```

Then reboot and let me know if your wi-fi still works.  If it does then verify that the /volatile directory is empty (should be).  If it breaks then you should be able to just rename that lrm-manager file back and reboot.

---

### Post by barranco on 2005-10-24
[QUOTE=mlomker]
If you're willing to try an experiment (should just take a couple reboots) then try this for me:

```

cd /lib/modules/$(uname -r)/volatile
sudo cp ath_hal.ko ../madwifi
sudo mv /sbin/lrm-manager /sbin/lrm-manager.old

```
[/QUOTE]

I'm gonna try that later today and I'll let you know, regardless of if it works or not i'm also gonna try and compile the drives from the source, I mean I'm here to learn.

thanks to everyone, I'll keep you posted

---

### Post by germac on 2005-10-24
I followed the how to to install fglr drivers for my ati radeon X600 and I got this error message when trying fglrxinfo or fgl_glxgears. What can I do?

"XFree86-DRI" missing on display ":0.0"

---

### Post by penguinchrissy on 2005-10-24
it worked but when I try and launch control pannel I get this

```
Details: Failed to execute child process "/usr/X11R6/bin/fireglcontrolpanel" (No such file or directory)
```

Did I do somethign wrong when installing?

---

### Post by barranco on 2005-10-25
Ok, Im gonna downgrade right now to 8.18.6 I've got a couple of questions...

1.- Where can an get a list of the drivers the restricted-modules package include, so that I know what else would I need to recompile along the madwifi drivers.

2.- Is it a way to get the fglrx driver with libqt3c102-mt that Skype requires or a way to get Skype with the libqt3-mt that fglrx requires?

If I had to choose, I rather have 3D than skype but it really sucks cause that's just another reason for me to spend time away from linux.

**--UPDATE: ** boy was that sentence melodramatic... ok, turns out I just had to install the [this]("http://www.mneylon.com/blog/archives/2005/09/25/skype-on-breezy/") version of skype that won't even bother with the libqt3.

---

### Post by barranco on 2005-10-25
[QUOTE=mlomker]
If you're willing to try an experiment (should just take a couple reboots) then try this for me:

```

cd /lib/modules/$(uname -r)/volatile
sudo cp ath_hal.ko ../madwifi
sudo mv /sbin/lrm-manager /sbin/lrm-manager.old

```

Then reboot and let me know if your wi-fi still works.  If it does then verify that the /volatile directory is empty (should be).  If it breaks then you should be able to just rename that lrm-manager file back and reboot.[/QUOTE]

Ok, done it I rebooted my wi-fi still works and in fact my /volatile directory is empty, what does that mean?

thanks

---

### Post by Septor on 2005-10-25
[QUOTE=penguinchrissy]it worked but when I try and launch control pannel I get this

```
Details: Failed to execute child process "/usr/X11R6/bin/fireglcontrolpanel" (No such file or directory)
```

Did I do somethign wrong when installing?[/QUOTE]

No, it is a problem with the shortcut... it links to the wrong directory.  Just run "fireglcontrolpanel" directly from a terminal or the "Run" command to start it.  
BTW, These shortcuts are correct in the latest patches at: [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

---

### Post by barranco on 2005-10-25
ATI Mobility [9600]

Ok, it worked out nicely, I have OpenGL @ 1280x800, now as soon as I get myself a s-video cable I'll check if the tv-out its working, do I need to manually set it up normally?

ah ok, and now the madwifi drivers... here we go yay!!:p

---

### Post by Cadbury on 2005-10-25
im sorry to be such a nucence in asking prob simple things as how to use apt

i did what u said mlomker and it sorta worked i guess. i tryed the 1st command 
#sudo apt-get install gcc-3.4 module-assistant

i got

> adrian@ubuntu:~/ATI$ apt-get install gcc-3.4 module-assistant
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependenci
        Depends: imlib1 but it is not going to be installed
        Depends: sox but it is not going to be installed
        Depends: libpng10-0 but it is not going to be installed
        Depends: docker but it is not going to be installed
        Depends: tcltls but it is not going to be installed
  gcc-3.4: Depends: gcc-3.4-base (>= 3.4.4-6ubuntu8) but it is not going to be installed
     Depends: cpp-3.4 (>= 3.4.4-6ubuntu8) but it is not going to be installed
           Depends: cpp-3.4 (< 3.4.6) but it is not going to be installed
           Depends: binutils (>= 2.16.1-2ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
adrian@ubuntu:~/ATI$ /home/adrian/ATI#

i dont know if i should force install or not

yum just downloaded everything for u:( 

this is my sources.list

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted multiverse universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted multiverse universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted multiverse universe
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted multiverse universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted multiverse universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted multiverse universe


i dont know if theres anything wrong with it or not.

any replys will be greatly appreciated :)

---

### Post by Guillaume Rouchy on 2005-10-25
I have juet installed Ubuntu Breezy on my laptop (Fujistu Amilo M1437G) that has a ATI Radeon Mobility X700. I have followed the HOWTO without any problem and i get 

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.6)

Meanwhile, i cannot switch to the resolution 1200x800, although it is present in the xorg.conf:

> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver		"fglrx"
	Option		"UseInternalAGPGART" "no"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Écran générique"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor		"Écran générique"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x800" "1024x768" "800x600"
	EndSubSection
EndSection



I am very new to Ubuntu and linux so i don't know what direction i should investigate... Thanks for any help!

---

### Post by mlomker on 2005-10-25
> These shortcuts are correct in the latest patches at: 

I'll generate some new .debs today for i386.  I didn't know you had fixed the paths in that release because it only mentioned 64-bit in the description. 

I'll have to test to see if that fixes the library path problem on 64-bit, because even if the shortcuts are correct you always needed to do this on Hoary before it'd run properly: **export LD_LIBRARY_PATH=/usr/lib32/**

---

### Post by mlomker on 2005-10-25
> Ok, done it I rebooted my wi-fi still works and in fact my /volatile directory is empty, what does that mean?

That means that madwifi users can install these ATI drivers.  That's great news and I'll update the how-to with this process.

---

### Post by mlomker on 2005-10-25
> I'll check if the tv-out its working, do I need to manually set it up normally?


No idea.  I've never gotten it to work on my laptop.

---

### Post by mlomker on 2005-10-25
> yum just downloaded everything for u:( 


So will apt-get when the repositories are totally synched up.  The problem is that the list of available files will get updated (what gets refreshed with **apt-get update**) before the actual files are copied.  I never use the main repositories because they are frequently too slow like that.

[Try one of the mirrors.]("https://wiki.ubuntu.com/Archive")  Attached is my sources.list file--just replace my company's mirror with another one from that list.

---

### Post by mlomker on 2005-10-25
> I am very new to Ubuntu and linux so i don't know what direction i should investigate... Thanks for any help!

Run **sudo dpkg-reconfigure xserver-xorg** and select only 1280x800 as a resolution.  If that doesn't work then you'll have to look at your /var/log/Xorg.0.log because your monitor must be rejecting the setting.

---

### Post by penguinchrissy on 2005-10-25
Does the tv in work with these new drivers or is there a way I can get it to work I've tried every thing and all I get is that it can't attach to dev/video 0 is there a way I can set it up?

---

### Post by sylvester_0 on 2005-10-27
Great. A new problem.

Background info:
I had been using debian for a long time before I switched to ubuntu. I liked how everything (including 3D acceleration) was "automagically" configured. Now, things have gone downhill in Breezy. I have been using it flawlessly since warty and been upgrading through time. I upgraded my hoary to breezy during the testing process and my 3D broke. Ok, no big deal, they're still testing. So, once the final dist-upgrade came around and it still didn't work, I was unhappy. So yesterday, I finally did a reinstall of my breezy with a final 5.10 cd image I just downloaded. Acceleration didn't work with stock "ati" driver (I have seen it work). So I installed the restricted modules and all of the required fglrx pieces. It worked, partially. My card was detected as a R2400 DDR generic or something like that (someone else in the thread has the same problem). 3D screensavers wouldn't even open, but this was the last of my concerns. Glxgears was slow. UT2004 worked beautifully up until the level was fully loaded (segfault).

So now I have followed this guide. Removed old pieces, installed sources, etc. Now I get
[HTML]
jared@satur9:~$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
[/HTML]
and
[HTML]
jared@satur9:~$ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => not found
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e84000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e5b000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e39000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d0b000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c4b000)
        libGL.so.1 => not found
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b64000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b59000)
        libGL.so.1 => not found
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7b4c000)
        /lib/ld-linux.so.2 (0xb7f0d000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b49000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b44000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b41000)
jared@satur9:~$
[/HTML]
and
[HTML]
root@satur9:/# find|grep libGL.so.1
./usr/share/fglrx/diversions/libGL.so.1.2
./usr/lib/i686/mmx/cmov/libGL.so.1.2
./usr/lib/i686/mmx/cmov/libGL.so.1
./usr/lib/libGL.so.1
./usr/lib/libGL.so.1.2
./usr/X11R6/lib/libGL.so.1
[/HTML]
(the /usr/X11R6/lib/libGL.so.1 is a symbollic link to /usr/lib/libGL.so.1 I have created based on other posts here)

I am at my wits end with this ATI stuff. My next machine is definitely nVidia.

---

### Post by mlomker on 2005-10-27
> I am at my wits end with this ATI stuff. My next machine is definitely nVidia.

As stated in the preface of the how-to, the 8.18.8 driver was released just this morning and has unresolved permissions problems.  I'll word my warning even stronger because I don't want anyone other than testers to install it until it is fixed.

---

### Post by sylvester_0 on 2005-10-27
Ok, I ran fglrxinfo as root and I get:

[HTML]
root@satur9:/# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FireMV 2400 PCI DDR Generic
OpenGL version string: 1.3.1014 (X4.3.0-8.18.8)
[/HTML]

by running a lscpi you can clearly see that this is not my video card at all:
[HTML]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02)
[/HTML]

here's a glxinfo:
[HTML]
root@satur9:/# glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
...
OpenGL renderer string: FireMV 2400 PCI DDR Generic
...
[/HTML]
...and of course glxgears is slower than ever.

I appologize for my previous post, I didn't realize that this was such a new release. I would  be perfectly happy using the fglrx that ships with Breezy STABLE but it is obviously broken and it used to work beautifully. Is this "modularization of xorg" a transition period like going to gcc-4? Or will it just always be hit and miss from here on out?

---

### Post by mlomker on 2005-10-27
> Or will it just always be hit and miss from here on out?

Sounds to me like ATI's code is misdetecting the chipset.  Unless you ran the same version of the driver on Hoary then I'd tend to assume that it is an ATI bug.

You could jump on [ATI's support forum]("http://www.rage3d.com/board/forumdisplay.php?f=88").  There is a ChipID command that you can use in the xorg.conf to make the driver think your card is a different model (rather than autodetecting it).

I did a Google search and it sounds like that card should be **ChipID = 0x4c66**.  You'll find a reference to the ChipID in the /var/log/Xorg.0.log file.

---

### Post by sylvester_0 on 2005-10-27
Well, this is just lovely...
[HTML]
jared@satur9:/$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
/usr/lib/amarok/amarokapp: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
[/HTML]
...like I posted before, this was a fresh system. I followed the install guide and now it seems to be hosed. Amarok was working fine before this. Great. Anyways, it seems I'm off to reintall Breezy for the second time in 2 days. This is kind of sad because it's only had Ubuntu installed on it a total of 2 times now. Ubuntu developers are you listening?!? Please, please, please give us at least a WORKABLE version of fglrx in your STABLE repositories.

I repeat: [COLOR="Red"]These drivers killed my newly installed system. Do not use them yet.[/COLOR]

Thanks for all your help mlomker, from a fellow Kubuntu user whose homestate is ND!

---

### Post by Septor on 2005-10-27
[QUOTE=mlomker]As stated in the preface of the how-to, the 8.18.8 driver was released just this morning and has unresolved permissions problems.  I'll word my warning even stronger because I don't want anyone other than testers to install it until it is fixed.[/QUOTE]

Can you be more specific about this "permission problem"?  I built the Ubuntu/breezy packages directly from the ati-installer and installed them without problems... any info would be appreciated, especially if it is a problem with my package generation scripts.

---

### Post by mlomker on 2005-10-27
[QUOTE=Septor]Can you be more specific about this "permission problem"?  I built the Ubuntu/breezy packages directly from the ati-installer and installed them without problems... any info would be appreciated, especially if it is a problem with my package generation scripts.[/QUOTE]

I sent you a couple PM's about it today.  All of the files from xorg-driver-fglrx get installed with a chmod of 700, rendering the driver unusable to anybody other than root.

---

### Post by mlomker on 2005-10-27
> I repeat: [COLOR="Red"]These drivers killed my newly installed system. Do not use them yet.[/COLOR]

Thanks for all your help mlomker, from a fellow Kubuntu user whose homestate is ND!

Yeah, I stated that in fairly bold type on the top of the how-to.  The permissions are wrong but I'm sure we'll have it fixed soon.  Basically only the 'root' user can use the 8.18.8 drivers at the moment.  

You should be able to switch back to the ATI drivers for a day or two until this is sorted.

---

### Post by Septor on 2005-10-28
[QUOTE=mlomker]I sent you a couple PM's about it today.  All of the files from xorg-driver-fglrx get installed with a chmod of 700, rendering the driver unusable to anybody other than root.[/QUOTE]

Ah I see... sorry missed the PMs :cool: 

The thing I can't figure out is why when I created and installed the Ubuntu packages from 8.18.8 it works fine on my Breezy laptop...  I'll look into it for sure though after work today.

---

### Post by Septor on 2005-10-28
Well I had a nice long detailed reply of the problem and its fix... then I closed the wrong tab... so now you get the short version ;)

Your umask is wrong when building the packages.  If you built the packages directly from the ati-driver-installer.run you wouldn't have this problem.  That is, don't --extract the driver then build packages from inside the fglrx-install directory but rather:

```

sudo /bin/sh ati-driver-installer-8.18.8-i386.run --buildpkg Ubuntu/breezy

```

If you really want to build from the extracted fglrx-install directory, set your umask to 0022:
```

/bin/sh ati-driver-installer-8.18.8-i386.run --extract
cd fglrx-install
sudo -s
umask 0022
./ati-installer.sh 8.18.8 --buildpkg Ubuntu/breezy
exit

```

There is nothing wrong with the packages if you build them from the downloaded installer as it fixes up the umask.

---

### Post by Delvien on 2005-10-28
Hi everyone, i tried this recently on my Dell i6000d laptop with ATi mobility radeon x300 128mb , went throught all the steps , when i went to reconfigure x-server , then rebooted, it came to kubuntu and it had lines all over my screen, and the top of it was a mass of colors "melting downward" any ideas on how to make these drivers work, so that i may play with cedega :( ?

---

### Post by darrenrxm on 2005-10-28
The drivers do not work for me either. Why can't we just use the ati installer to install these drivers? Wouldn't that be the best way? Nevermind, I'll wait a while until you guys have a install system that works for everyone.

---

### Post by mlomker on 2005-10-28
> Nevermind, I'll wait a while until you guys have a install system that works for everyone.

It sounds like with this version that would work on 32-bit systems.  You still need to deal with the restricted modules, so I disagree with some how-to's that are like:  Gee, just install the thing.  The n00b's will be back saying 'it doesn't work' within a few minutes.

You also can't remove the drivers when you run the script without building the .debs.  That's another common question within minutes of your how-to being finished: Didn't work, so how do I remove it?

The last version of this driver was broken and the current on the .debs have to be build differently than the last version...nothing is 'simple' around here, I think.

---

### Post by mlomker on 2005-10-28
> There is nothing wrong with the packages if you build them from the downloaded installer as it fixes up the umask.

Silly me, I was following the exact same steps that I used with the last version.  That would have been far too easy.  ;)

I've updated the how-to to generate the packages from the installer.

---

### Post by xuefengwang101 on 2005-10-28
my chipset is  ati mobility radeon 9100 igp 
i want to know dose it support by the fglrx driver??

---

### Post by mlomker on 2005-10-28
> my chipset is  ati mobility radeon 9100 igp 


Yes, but you should try the [8.16.20 driver]("http://ubuntuforums.org/showthread.php?p=408111") first.

---

### Post by yyagol on 2005-10-28
Hmmmmm big problem
when i try to install the gcc it gose good :
```
$ sudo apt-get install gcc-3.4
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
```
so i understand it is now installed ( i uninstall the gcc 4.0)
and when i try to install the modules i get this:
```
$ sudo sh ./ati-driver-installer-8.18.8-i386.run --buildpkg Ubuntu/breezy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.18.8........................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
[COLOR="Red"]sh: gcc: command not found[/COLOR]
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

```
now can eny 1 tell me what is going on here couse i am realy confuse
is my machine go crazy or what?

---

### Post by mlomker on 2005-10-28
> ( i uninstall the gcc 4.0)


gcc4 should be installed and the build-essential package would have done so if it wasn't already.  You can have more than one version of gcc installed at the same time...

You can try this command prior to running it, but I didn't have to do this.

```

export CC=/usr/bin/gcc-3.4

```

---

### Post by yyagol on 2005-10-28
[QUOTE=mlomker]
You can try this command prior to running it, but I didn't have to do this.

```

export CC=/usr/bin/gcc-3.4

```[/QUOTE]
ill try that ....i just reinstall brezzy so now i start from zero
just to make shour nothing is wrong 
i'll let you know if it works couse i think the [COLOR="Red"]gcc[/COLOR] is the problem
the installation gose well every time i'v tryed it ( no errors ) before with 5.04
and it worked fine , but with breezy i cant get it to work.

---

### Post by mlomker on 2005-10-28
[QUOTE=yyagol]ill try that ....i just reinstall brezzy so now i start from zero[/QUOTE]

I'll do that again myself as soon as I find the time today.  I really wish ATI would stop releasing drivers once a week...it's too time consuming for me to keep up with a constantly changing how-to.  Reloading my box 4 times to test it on 32-bit and 64-bit kills an afternoon every time.

---

### Post by yyagol on 2005-10-28
[QUOTE=mlomker]  I really wish ATI would stop releasing drivers once a week...it's too time consuming for me to keep up with a constantly changing how-to.  Reloading my box 4 times to test it on 32-bit and 64-bit kills an afternoon every time.[/QUOTE]
[SIZE="4"]so true[/SIZE]
i just wish they can make one that can realy work out of the box

---

### Post by yyagol on 2005-10-28
still no good
after new fresh installation of Breezy flowing the instractions i get
some errors :
i could not get rid of the Mesa
i had to add  [COLOR="Red"]gcc-3.3-base[/COLOR] and [COLOR="Red"]libstdc++5[/COLOR] to install the driver
with no error but still :
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

$ lspci|grep ati
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

$ less Xorg.0.log|grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Failed to set up write-combining range (0xe0000000,0x8000000)

$ less Xorg.0.log|grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP

$ lsmod|grep fglrx
fglrx                 246944  0
agpgart                32328  2 fglrx,sis_agp

```

but i cant figure out how to fix it...any idea ?

---

### Post by mlomker on 2005-10-28
You might see some errors here:

```

dmesg | grep fglrx
dmesg | grep agp

```

[Other posts]("http://ubuntuforums.org/showthread.php?t=70173") suggest that it is motherboard related.  I'd suggest going to [ATI's board]("http://www.rage3d.com/board/forumdisplay.php?f=88") if your BIOS is current all that jazz.

---

### Post by j0nas on 2005-10-28
I followed all of the given instructions.  After installing all of the .deb packages I can't find the aticonfig program or the fglrxinfo program that you mention.  How do I get these programs so I can complete the configuration?

---

### Post by Septor on 2005-10-28
[QUOTE=j0nas]I followed all of the given instructions.  After installing all of the .deb packages I can't find the aticonfig program or the fglrxinfo program that you mention.  How do I get these programs so I can complete the configuration?[/QUOTE]

If they .deb were created and installed then they should both be located in /usr/bin...are they not there?

---

### Post by Bubbles on 2005-10-29
Yikes...

This is my first time trying linux.  It's not looking promising...

Please bear in mind I am Joe user, not uber geek.  "Linux for humans" sounded promising, but the troubleshooting on these forums doesn't fit the hype.

First attempt at Ubuntu went nowhere because it wouldn't recognize my USB keyboard, so I bought another keyboard to go into my PS/2 port.

Now I can't get resolutions higher than 1024x768, which looks blurry on my 1280x1024 LCD.  (ATI x800)

I followed the instructions to re-install the 8.16.20 drivers.  No issues during the process, but the problem was not fixed.

So then I tried the 8.18.8 method and ran into an error after running the first terminal command line after rebooting.  (Something like "unable to find module-assistant.")  Any hints?

---

### Post by barranco on 2005-10-29
I successfully upgraded this drivers following the HOW-TO however, as I removed the restricted modules now I'm discovering that my pcmcia doesnt work and probably some other stuff I don't know about too, would it possibly be there a way to just discard the ati driver that comes with the resctricted modules and keep everything else?

anyhow, I followed some guys HOW-TO on pcmcia but it didnt work for me, still looking for more info... 

thanks guys

---

### Post by yyagol on 2005-10-29
[QUOTE=mlomker] I'd suggest going to [ATI's board]("http://www.rage3d.com/board/forumdisplay.php?f=88") if your BIOS is current all that jazz.[/QUOTE]

it is so much difrent then what is here but ill give it a try
i was thinking it myte be the kernel couse with 2.6.10-5 it worked
then why not with this one? well it needs to recompile?

my motherboard is GIGABYTE 85655FX  and they talked of ASUS
so i dont think its the board. beside it worked befor ( fedora , Hoary ) why not now.

---

### Post by Hire on 2005-10-29
Hi, 

When I try to do glxgears -info I have this output:

```
glxgears: error while loading shared libraries: libGL.so.1: cannot open
 shared object file: No such file or directory
```

Why? 

And with ldd /usr/X11R6/bin/fglrxinfo I have this output:

```
         linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => not found
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e13000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e06000)
        libc.so.6 => /lib/tls/libc.so.6 (0xb7cd8000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7cd5000)
        libdl.so.2 => /lib/tls/libdl.so.2 (0xb7cd1000)
        /lib/ld-linux.so.2 (0xb7f04000)
```

How can I fix it?

---

### Post by yyagol on 2005-10-29
i think i found the reson for all fassing:
```
ATI module generator V 2.0
==========================
initializing...
build_date =Fri Oct 28 21:34:50 IST 2005
uname -a =Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
uname -s =Linux
uname -m =i686
uname -r =2.6.12-9-386
uname -v =#1 Mon Oct 10 13:14:36 BST 2005
uid=0(root) gid=0(root) groups=0(root)
.
drwxr-xr-x  41 root root 4096 2005-10-28 19:35 /usr/include
.
total 408
drwxr-sr-x   2 root src    4096 2005-10-28 21:34 ATI
-rw-r--r--   1 root src  116168 2005-10-28 18:42 fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb
-rw-r--r--   1 root root 273116 2005-10-28 18:33 fglrx.tar.bz2
lrwxrwxrwx   1 root src      26 2005-10-28 18:41 linux -> linux-headers-2.6.12-9-386
drwxr-xr-x  18 root root   4096 2005-10-28 17:39 linux-headers-2.6.12-9
drwxr-xr-x   4 root root   4096 2005-10-28 17:39 linux-headers-2.6.12-9-386
drwxr-xr-x   3 root src    4096 2005-10-28 18:33 modules
.
file /lib/modules/2.6.12-9-386/build/include/linux/agp_backend.h says: AGP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.12-9-386/build/include/linux/autoconf.h says: MODVERSIONS=1
.
CC=gcc-3.4
cc_version=3.4.5
found major but not minor version match for gcc-3.4 and the ip-library
ls -l ./libfglrx_ip.a
lrwxrwxrwx  1 root root 20 2005-10-28 21:34 ./libfglrx_ip.a -> ./libfglrx_ip.a.GCC3
.
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
def_vma_api_version=-DFGL_LINUX253P1_VMA_API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8173:[COLOR="Red"] warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)[/COLOR]
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8183:[COLOR="Red"] warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)[/COLOR]
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6077: [COLOR="Red"]warning: 'ati_gart_base' defined but not used[/COLOR]
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:542: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:544: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:564: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:595: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_verify_area':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1478: warning: `verify_area' is deprecated (declared at include/asm/uaccess.h:105)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `do_vm_kmap_nopage':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2465: warning: assignment makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1964: warning: 'deferred_flush' defined but not used
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
build succeeded with return value 0
.
duplicating results into driver repository...
target location: /lib/modules/fglrx
copying fglrx.ko
copying logfile of build
*** end of build log ***

```

---

### Post by mlomker on 2005-10-29
> So then I tried the 8.18.8 method and ran into an error after running the first terminal command line after rebooting.  (Something like "unable to find module-assistant.")  Any hints?

Did you install it?  That was one the items you had to apt-get.

---

### Post by mlomker on 2005-10-29
> just discard the ati driver that comes with the resctricted modules and keep everything else?

No.  There's also nothing related to PCMICIA in restricted-modules.  You could try renaming lrm-manager like in [this post]("http://www.ubuntuforums.org/showpost.php?p=439548") but I don't recommend it.  It'll just get undone the next time they update the kernel.

---

### Post by mlomker on 2005-10-29
> so i dont think its the board. beside it worked befor ( fedora , Hoary ) why not now.

It worked with what version of the driver in Hoary?  A lot of things change between major releases in Ubuntu.  I'm not a programmer, I'm just just another guy like you trying to make things work.

---

### Post by mlomker on 2005-10-29
[QUOTE=yyagol]i think i found the reson for all fassing:
[/QUOTE]

I always get a few of those 'deprecated' errors when I compile things.  In any case, that's an ATI problem and not anything that we can fix.

---

### Post by Septor on 2005-10-30
[QUOTE=Bubbles]Yikes...

This is my first time trying linux.  It's not looking promising...

Please bear in mind I am Joe user, not uber geek.  "Linux for humans" sounded promising, but the troubleshooting on these forums doesn't fit the hype.

First attempt at Ubuntu went nowhere because it wouldn't recognize my USB keyboard, so I bought another keyboard to go into my PS/2 port.

Now I can't get resolutions higher than 1024x768, which looks blurry on my 1280x1024 LCD.  (ATI x800)

I followed the instructions to re-install the 8.16.20 drivers.  No issues during the process, but the problem was not fixed.

So then I tried the 8.18.8 method and ran into an error after running the first terminal command line after rebooting.  (Something like "unable to find module-assistant.")  Any hints?[/QUOTE]

Hey Bubbles.  You probably need to install the module-assistant package.  So fire up the Synaptic package manager, search of module-assistant and install it.  Then follow through the 8.18.8 howto again and everything should work.

---

### Post by serko on 2005-10-30
Hi to everyone!

After so many unlucky shoots of installing fglrx (I think it's now over 30 shoots) and using all different methods that I found on ubuntuforum.org, even after trying different versions I have no more good idea so I'm writing...

First of all I'm kind of newbie since I wasn't using much Linux in past but i have tendencie to change that once and for all (tired of m$ bullshit). 

I have AMD 1.6GHz and a fresh copy of Breezy (32 bit), kernel 2.6.12-9-386 and Ati Radeon 9000PRO (I don't know if this card is supported at all. I found somewhere that it isn't but I'm not sure since in official list Radeon 9000 is supported).

So if in refer to thread HOW-TO: ATI fglrx driver 8.18.8 ([http://ubuntuforums.org/showthread.php?t=78466&highlight=radeon](http://ubuntuforums.org/showthread.php?t=78466&highlight=radeon))

damijan@lucky:~$ fglrxinfo
bash: fglrxinfo: command not found

Ok fglrx is not installed

Remove Breezy's included drivers if they are installed:

I have no drivers installed only linux-386 linux-restricted-modules-2.6.12-9-386 linux-restricted-modules-386 so I have removed modules using instructions.

I have reconfigured (In fact configured the same once more) xserver with:

sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

Quick reboot...

Now I het to installing driver... 

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno
E: Ni mogo&#269;e najti paketa module-assistant 

(Don't mind that it isn't in English... no packet found module-assistant)

Ok module-assistant installed... once more 
sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf
and everything looks fine for now...

Now bulid of debian packages:

Well not that I forgot to download driver :))) ... just a little break... for bear... cigarete.. anyway :)

damijan@lucky:~$ sudo sh ./ati-driver-installer-8.18.8-i386.run --buildpkg Ubuntu/breezy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.18.8........................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/fglrx-install
Package /home/damijan/xorg-driver-fglrx_8.18.8-1_i386.deb has been successfully generated
Package /home/damijan/xorg-driver-fglrx-dev_8.18.8-1_i386.deb has been successfully generated
Package /home/damijan/fglrx-kernel-source_8.18.8-1_i386.deb has been successfully generated
Package /home/damijan/fglrx-control_8.18.8-1_i386.deb has been successfully generated
Package /home/damijan/fglrx-sources_8.18.8-1_i386.deb has been successfully generated
~/fglrx-install
Removing temporary directory: fglrx-install

Well it still looks ok and fine and so on...

now I don't understand why cd .. since I have packages in same directory like driver-install but anyway let's move on to first problem:

damijan@lucky:~$ sudo dpkg -i fglrx-control_8.18.8-1_i386.deb
Selecting previously deselected package fglrx-control.
(Reading database ... 59929 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.18.8-1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-control:
 fglrx-control depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
dpkg: error processing fglrx-control (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-control

Control depends on xorg-driver and this one is not installed yet. Interesting. My logical solution is to install xorg-driver first, but before there is:

damijan@lucky:~$ sudo dpkg -i fglrx-kernel-source_8.18.8-1_i386.deb
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 59937 files and directories currently installed.)
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.18.8-1_i386.deb) ...
Setting up fglrx-kernel-source (8.18.8-1) ...

now to xorg-driver

damijan@lucky:~$ sudo dpkg -i xorg-driver-fglrx_8.18.8-1_i386.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 59941 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.18.8-1_i386.deb) ...
Adding `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on libstdc++5; however:
  Package libstdc++5 is not installed.
dpkg: error processing xorg-driver-fglrx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-driver-fglrx

Ok I don't have libstdc++5... I'll install it so I get to:

damijan@lucky:~$ sudo dpkg -i xorg-driver-fglrx_8.18.8-1_i386.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 59947 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.18.8-1_i386.deb) ...
Adding `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
Setting up xorg-driver-fglrx (8.18.8-1) ...

seems fine... but now back to control... should I install that again or what??? Well my choice is to install it again:

damijan@lucky:~$ sudo dpkg -i fglrx-control_8.18.8-1_i386.deb
Selecting previously deselected package fglrx-control.
(Reading database ... 60021 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.18.8-1_i386.deb) ...
Setting up fglrx-control (8.18.8-1) ...

And now to upgrade:

damijan@lucky:~$ sudo apt-get -f upgrade
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno
0 nadgrajenih, 0 na novo name&#353;&#269;enih, 0 bo odstranjenih in 0 ne nadgrajenih.

Well there's nothing to upgrade... fine for me.

Kernel driver build:

damijan@lucky:~$ sudo module-assistant prepare
 apt-get  install linux-headers-2.6.12-9-386

Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno
Naslednji dodatni paketi bodo name&#353;&#269;eni:
  linux-headers-2.6.12-9
Naslednji NOVI paketi bodo name&#353;&#269;eni:
  linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
0 nadgrajenih, 2 na novo name&#353;&#269;enih, 0 bo odstranjenih in 0 ne nadgrajenih.
Potrebno je dobiti 0B/6725kB arhivov.
Po odpakiranju bo uporabljenega 70,1MB dodatnega prostora na disku.
Ali &#382;elite nadaljevati [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package linux-headers-2.6.12-9.
(Reading database ... 60029 files and directories currently installed.)
Unpacking linux-headers-2.6.12-9 (from .../linux-headers-2.6.12-9_2.6.12-9.23_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-9-386.
Unpacking linux-headers-2.6.12-9-386 (from .../linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb) ...
Setting up linux-headers-2.6.12-9 (2.6.12-9.23) ...

Setting up linux-headers-2.6.12-9-386 (2.6.12-9.23) ...

Done!

damijan@lucky:~$ sudo module-assistant update

Updated infos about 68 packages

damijan@lucky:~$ sudo module-assistant a-i fglrx
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti... Narejeno
Najnovej&#353;a razli&#269;ica fglrx-kernel-source je &#382;e name&#353;&#269;ena.
0 nadgrajenih, 0 na novo name&#353;&#269;enih, 0 bo odstranjenih in 0 ne nadgrajenih.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2
modules/
modules/fglrx/
modules/fglrx/debian/
modules/fglrx/debian/changelog
modules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/debian/rules
modules/fglrx/debian/control.template
modules/fglrx/debian/dirs.template
modules/fglrx/debian/postinst
modules/fglrx/agp3.c
modules/fglrx/agpgart_be.c
modules/fglrx/firegl_public.c
modules/fglrx/i7505-agp.c
modules/fglrx/nvidia-agp.c
modules/fglrx/agp_backend.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/drm_compat.h
modules/fglrx/drm.h
modules/fglrx/drm_os_linux.h
modules/fglrx/drmP.h
modules/fglrx/drm_proc.h
modules/fglrx/firegl_public.h
modules/fglrx/make.sh
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/Makefile
Done with /usr/src/fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.12-9-386.
(Reading database ... 73787 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-9-386 (from .../fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb) ...
Setting up fglrx-kernel-2.6.12-9-386 (8.18.8-1+2.6.12-9.23) ...

I think everything went fine... I know I'm "little" long with my thread... but anyway.... I said I'm a noob :)

Now to xorg.conf (I read many threads and I don't like this way but let's go step by step):

damijan@lucky:~$ sudo aticonfig --initial
Using /etc/X11/xorg.conf
Uninitialised file found, configuring.

Well now xserver restart and the result should be Mesa :( as always... we'll I'll find out.

damijan@lucky:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Yes, as I thought.

ANY IDEA? AT ALL?

DESPERATE :confused: :confused:

Here's the output of ldd /usr/bin/glxinfo

damijan@lucky:~$ sudo ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7e5a000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7de4000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7dbb000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d99000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c6b000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7baa000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7b9d000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7b8b000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b88000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7aa2000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7a97000)
        /lib/ld-linux.so.2 (0xb7f06000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a93000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7a8f000)

Think I found it:

damijan@lucky:~$ sudo ls -l /usr/X11R6/lib/libGL.so.1
ls: /usr/X11R6/lib/libGL.so.1: No such file or directory

I also don't have any /lib/modules/fglrx/ directory... obviously no fglrx installed.... what the hell am I doing wrong?

---

### Post by mlomker on 2005-10-30
> o drivers installed only linux-386 linux-restricted-modules-2.6.12-9-386 linux-restricted-modules-386

The newer drivers will not work with restricted-modules installed because the 8.16.20 driver is a part of that package.

> now I don't understand why cd .. since I have packages in same directory like driver-install but anyway let's move on to first problem:

A leftover from the .6 version.  I'll correct it.

> 
Control depends on xorg-driver and this one is not installed yet. Interesting. My logical solution is to install xorg-driver first, but before there is:


As stated in the how-to, you could have ignored those errors as they would have been fixed by the update.

> 
ANY IDEA? AT ALL?


This how-to is a method to install the drivers, not a guarantee that there isn't something wrong with them.  There are quite a few people who are having bugs related to the driver itself, but only ATI can fix that.

> 
damijan@lucky:~$ sudo ls -l /usr/X11R6/lib/libGL.so.1
ls: /usr/X11R6/lib/libGL.so.1: No such file or directory


That isn't a problem because the file should be /usr/lib/libGL.so.1.2 and not in that directory.  ATI's unpatched 8.18.6 driver went there but not the Ubuntu patched versions.

> 
I also don't have any /lib/modules/fglrx/ directory... obviously no fglrx installed.... what the hell am I doing wrong?

You shouldn't.  You're thinking of the 8.16.20 drivers and not the newer ones.  The file is at /lib/modules/2.6.12-9-k7/misc/fglrx.ko on my machine.

You need to look through the output of **dmesg | fglrx** and the /var/log/Xorg.0.log file for error messages related to the driver.  You could also try **sudo fglrxinfo** to see if it returns a different result--if it does then you may have a permissions problem on some of the driver files (I had that happen once).

I'll also stress that this how-to was tested on a clean install and I have no idea what condition your installation is in after so many attempts to install the driver.

---

### Post by serko on 2005-10-30
Well now it's time to laugh.
Obviously I was wasting my time for one reason.
Ctrl+Alt+Backspace restarts X but not all drivers.
Now a few hours after I made **clean** installation like I said in my thread before I just started my Ubuntu and fglrxinfo shows next (not Mesa like before, it's in thread up above)
damijan@lucky:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: FIRE GL 9000 PRO DDR Athlon (3DNow!) (FireGL) (GNU_ICD)
OpenGL version string: 1.3.1014 (X4.3.0-8.18.8)

Looks like everything is fine :):):):) :D :D 

**mlomker THANKS FOR EVERYTHING**, i mean not only help to my topic but all howtos and so on...

Just one more question

glxgears fps? what's the command? I used the funny one long command... it also works...

damijan@lucky:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
5976 frames in 5.0 seconds = 1195.023 FPS
5951 frames in 5.0 seconds = 1190.111 FPS
5944 frames in 5.0 seconds = 1188.718 FPS
5951 frames in 5.0 seconds = 1190.104 FPS
5952 frames in 5.0 seconds = 1190.320 FPS

---

### Post by mlomker on 2005-10-30
> damijan@lucky:~$ glxgears -iacknowledgethatthistoolisnotabenchmark


You could add an alias to your /etc/bash.bashrc file:

```

alias glxgears='glxgears -printfps'

```

Here's the command we used to find that in the first place:

```

strings /usr/bin/glxgears

```

---

### Post by duffman25 on 2005-10-30
Hi

I've been waiting for ati tu add support for dynamic clocks, since I have a laptop & my battery with fglrx won't last for long. After reading the release notes for 8.18.8 I thought I would install it. I've read the how-to & tried to generate the .debs but something goes wrong & no deb's are outputted, so I went & did the install with the gui from ati.

After logging & looking at x.org's log I see that the fglrx module is loaded but I have no 3d acceleration & no dynamic clocks. Here's some of my config files.

I'm using a laptop: Acer aspire 1691WMLI with X600 Pci-express ati radeon. Can somebody help me?

---

### Post by duffman25 on 2005-10-30
More output maybe it helps:

```

FATAL: Module fglrx not found.

```

---

### Post by mlomker on 2005-10-30
[QUOTE=duffman25]More output maybe it helps:
[/QUOTE]

I edited your post because it seemed a bit excessive for establishing that the module wasn't installed.  I would have helped you figure out my how-to but you didn't ask for help.  

Like I said in my how-to, not using the .debs means that you won't know if the installer succeeded because their error handling is dismal.  You could look for their log file and see where it failed.  They have their own [support forum]("http://www.rage3d.com/board/forumdisplay.php?f=88").

You could start by searching for the module:

```

sudo updatedb
locate fglrx.ko

```

---

### Post by duffman25 on 2005-10-30
[QUOTE=mlomker]I edited your post because it seemed a bit excessive for establishing that the module wasn't installed.  I would have helped you figure out my how-to but you didn't ask for help.  I'm not too interested in providing support for ATI's installer since I spent so much time working on my own how-to.  I do know that it generates a log of what it did somewhere...perhaps you should look for it.  Like I said in my how-to, not using the .debs means that you won't know if the installer succeeded because their error handling is dismal.

Perhaps you could start with this, because it sounds like the module wasn't even created.

```

sudo updatedb
locate fglrx.ko

```[/QUOTE]



javier@A1691:~$ sudo updatedb
javier@A1691:~$ locate fglrx.ko
javier@A1691:~$

Nothing found

---

### Post by duffman25 on 2005-10-30
I'm trying again to generate the .deb's but the ati installer doesn't generate them, instead it gives NO errors:
```

sudo sh ./ati-driver-installer-8.18.8-i386.run --buildpkg Ubuntu/breezy
[...]
Generating package: Ubuntu/breezy
/tmp/fglrx ~/Desktop/ati/fglrx-install
~/Desktop/ati/fglrx-install
Removing temporary directory: fglrx-install
javier@A1691:~/Desktop/ati$ ls
ati-driver-installer-8.18.8-i386.run   Xorg.0.log         xorg.conf.txt
fglrx-installer_8.18.8-1_i386.changes  Xorg.0.log.tar.gz

```

I have everything you recommended to be installed before generating the dev

---

### Post by Kimppa on 2005-10-30
Hello

Thank you for this HOW-TO. I've followed exactly your instructions, but I'm still getting this output for fglrxinfo

```

kimppa@kleppane:~ $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I'm running out of ideas on what to try next and I was wondering if one of you guys could point me in the right direction. I've only been trying to get these drivers installed for the past couple of weeks, so it would be nice to finally get them working :)

Here's some info I've picked up while reading this thread, hopefully there's some useful information that will tell you what my problem is (or rather, how to fix it).

As I mentioned, I've followed this thread's instructions, and I've also done the things suggested in [https://wiki.ubuntu.com/BinaryDriverHowto/ATIOnBreezyOpenGLFix](https://wiki.ubuntu.com/BinaryDriverHowto/ATIOnBreezyOpenGLFix)

Here are some ouputs for a few commands

ldd /usr/bin/glxinfo
```

kimppa@kleppane:~ $kimppa@kleppane:~ $ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7f0a000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e94000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e6b000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e49000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d1b000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c5a000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c4d000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c3b000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c38000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b52000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b47000)
        /lib/ld-linux.so.2 (0xb7fc6000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b43000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b3f000)
kimppa@kleppane:~ $

```

glxinfo
```

kimppa@kleppane:~ $ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
kimppa@kleppane:~ $

```

Any ideas?

Thank you in advance

---

### Post by duffman25 on 2005-10-30
Can someone post here the files installed by the ati installer? It's the output of these 3 commands:

```

dpkg -L fglrx-control_8.18.8-1_i386.deb
dpkg -L fglrx-kernel-source_8.18.8-1_i386.deb
dpkg -L xorg-driver-fglrx_8.18.8-1_i386.deb

```

Thanxs.

---

### Post by mlomker on 2005-10-30
> I have everything you recommended to be installed before generating the dev

I don't have any suggestions because I've never seen that problem.  My how-to was written from and tested on a clean Breezy install.  If your machine was a Hoary upgrade or anything other than a recent clean install then your problems start becoming unique.

---

### Post by mlomker on 2005-10-30
```

kimppa@kleppane:~ $kimppa@kleppane:~ $ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7f0a000)

```

That's the wrong path for the latest driver.  You may have followed these instructions but you must have made other attempts in the past.  You might have to do a fresh install to get things back to defaults before the drivers will work for you.

Should be:

```

        libGL.so.1 => /usr/lib/libGL.so.1 (0x4286d000)

```

The only thing that I'd suggest doing is deleting the /etc/ld.so.conf file if it exists and then run **sudo ldconfig**.

---

### Post by mlomker on 2005-10-30
[QUOTE=duffman25]Can someone post here the files installed by the ati installer? [/quote]

```

mlomker@mlomkernote:/$ dpkg -L fglrx-control
/.
/usr
/usr/bin
/usr/bin/fireglcontrolpanel
/usr/share
/usr/share/applnk
/usr/share/applnk/fireglcontrol.kdelnk
/usr/share/gnome
/usr/share/gnome/apps
/usr/share/gnome/apps/fireglcontrol.desktop
/usr/share/icons
/usr/share/icons/ati.xpm
/usr/share/pixmaps
/usr/share/pixmaps/ati.xpm
/usr/share/doc
/usr/share/doc/fglrx-control
/usr/share/doc/fglrx-control/copyright

mlomker@mlomkernote:/$ dpkg -L fglrx-kernel-source
/.
/usr
/usr/src
/usr/src/fglrx.tar.bz2
/usr/share
/usr/share/doc
/usr/share/doc/fglrx-kernel-source
/usr/share/doc/fglrx-kernel-source/copyright
/usr/share/modass
/usr/share/modass/packages
/usr/share/modass/packages/fglrx-kernel-source

mlomker@mlomkernote:/$ dpkg -L xorg-driver-fglrx
/.
/usr
/usr/lib
/usr/lib/libfglrx_gamma.so.1.0
/usr/lib/libfglrx_pp.so.1.0
/usr/lib/libGL.so.1.2
package diverts others to: /usr/share/fglrx/diversions/libGL.so.1.2
/usr/X11R6
/usr/X11R6/lib
/usr/X11R6/lib/modules
/usr/X11R6/lib/modules/dri
/usr/X11R6/lib/modules/dri/atiogl_a_dri.so
/usr/X11R6/lib/modules/dri/fglrx_dri.so
/usr/X11R6/lib/modules/drivers
/usr/X11R6/lib/modules/drivers/fglrx_drv.o
/usr/X11R6/lib/modules/linux
/usr/X11R6/lib/modules/linux/libfglrxdrm.a
/usr/share
/usr/share/fglrx
/usr/share/fglrx/diversions
/usr/share/doc
/usr/share/doc/xorg-driver-fglrx
/usr/share/doc/xorg-driver-fglrx/README.Debian
/usr/share/doc/xorg-driver-fglrx/copyright
/usr/share/doc/xorg-driver-fglrx/articles
/usr/share/doc/xorg-driver-fglrx/articles/1gbhang.html
/usr/share/doc/xorg-driver-fglrx/articles/4461.html
/usr/share/doc/xorg-driver-fglrx/articles/4462.html
/usr/share/doc/xorg-driver-fglrx/articles/4463.html
/usr/share/doc/xorg-driver-fglrx/articles/4464.html
/usr/share/doc/xorg-driver-fglrx/articles/4469.html
/usr/share/doc/xorg-driver-fglrx/articles/4470.html
/usr/share/doc/xorg-driver-fglrx/articles/4475.html
/usr/share/doc/xorg-driver-fglrx/articles/4478.html
/usr/share/doc/xorg-driver-fglrx/articles/4479.html
/usr/share/doc/xorg-driver-fglrx/articles/4480.html
/usr/share/doc/xorg-driver-fglrx/articles/4481.html
/usr/share/doc/xorg-driver-fglrx/articles/4482.html
/usr/share/doc/xorg-driver-fglrx/articles/4483.html
/usr/share/doc/xorg-driver-fglrx/articles/4484.html
/usr/share/doc/xorg-driver-fglrx/articles/4485.html
/usr/share/doc/xorg-driver-fglrx/articles/corruptstereo.html
/usr/share/doc/xorg-driver-fglrx/articles/corruptvtswitch.html
/usr/share/doc/xorg-driver-fglrx/articles/devshm.html
/usr/share/doc/xorg-driver-fglrx/articles/dga3dhang.html
/usr/share/doc/xorg-driver-fglrx/articles/doom3corrupt.html
/usr/share/doc/xorg-driver-fglrx/articles/dualheadvideo.html
/usr/share/doc/xorg-driver-fglrx/articles/laptopsuspend.html
/usr/share/doc/xorg-driver-fglrx/articles/missingdrmheaders.html
/usr/share/doc/xorg-driver-fglrx/articles/mousecursorhang.html
/usr/share/doc/xorg-driver-fglrx/articles/no3d-aiw8500dv.html
/usr/share/doc/xorg-driver-fglrx/articles/no3d-kt400.html
/usr/share/doc/xorg-driver-fglrx/articles/nomembercount.html
/usr/share/doc/xorg-driver-fglrx/articles/pcie3dmemoryleak.html
/usr/share/doc/xorg-driver-fglrx/articles/r420blankdisplay.html
/usr/share/doc/xorg-driver-fglrx/articles/rv280dviblankdisplay.html
/usr/share/doc/xorg-driver-fglrx/articles/rv350springdale.html
/usr/share/doc/xorg-driver-fglrx/articles/secondheadcorruption.html
/usr/share/doc/xorg-driver-fglrx/articles/xf86_enodev.html
/usr/share/doc/xorg-driver-fglrx/articles/xrestartpcie.html
/usr/share/doc/xorg-driver-fglrx/articles/xvsatshift.html
/usr/share/doc/xorg-driver-fglrx/LICENSE.GPL.gz
/usr/share/doc/xorg-driver-fglrx/configure.html
/usr/share/doc/xorg-driver-fglrx/driverfaq.html
/usr/share/doc/xorg-driver-fglrx/index.html
/usr/share/doc/xorg-driver-fglrx/issues.html
/usr/share/doc/xorg-driver-fglrx/LICENSE.expat
/usr/share/doc/xorg-driver-fglrx/LICENSE.xmlconfig
/usr/share/doc/xorg-driver-fglrx/linuxfaq.html
/usr/share/doc/xorg-driver-fglrx/release-notes
/usr/share/doc/xorg-driver-fglrx/release-notes/images
/usr/share/doc/xorg-driver-fglrx/release-notes/images/backgrnd.gif
/usr/share/doc/xorg-driver-fglrx/release-notes/images/caution.gif
/usr/share/doc/xorg-driver-fglrx/release-notes/images/clipbrd.gif
/usr/share/doc/xorg-driver-fglrx/release-notes/images/noboarder.gif
/usr/share/doc/xorg-driver-fglrx/release-notes/index.html
/usr/share/doc/xorg-driver-fglrx/tips-linux.html
/usr/share/doc/xorg-driver-fglrx/user-manual
/usr/share/doc/xorg-driver-fglrx/user-manual/index.html
/usr/share/doc/xorg-driver-fglrx/ATI_LICENSE.TXT.gz
/usr/share/doc/xorg-driver-fglrx/LICENSE.QPL.gz
/usr/bin
/usr/bin/fgl_glxgears
/usr/bin/fglrx_pplay
/usr/bin/fglrx_xgamma
/usr/bin/fglrxconfig
/usr/bin/fglrxinfo
/usr/bin/aticonfig

```

---

### Post by Bubbles on 2005-10-30
[QUOTE=mlomker]Did you install it?  That was one the items you had to apt-get.[/QUOTE]

It's the apt-get command that gives that error message.

---

### Post by Bubbles on 2005-10-30
[QUOTE=Septor]Hey Bubbles.  You probably need to install the module-assistant package.  So fire up the Synaptic package manager, search of module-assistant and install it.  Then follow through the 8.18.8 howto again and everything should work.[/QUOTE]

I searched and couldn't get anything to install.  I've just tried enabling some "multiverse" thing, but all that gives me is 404 errors.

---

### Post by Septor on 2005-10-30
[QUOTE=Bubbles]I searched and couldn't get anything to install.  I've just tried enabling some "multiverse" thing, but all that gives me is 404 errors.[/QUOTE]

module-assistant is located in universe: [http://packages.ubuntu.com/breezy/misc/module-assistant](http://packages.ubuntu.com/breezy/misc/module-assistant)

---

### Post by catinsnow on 2005-10-31
[QUOTE=duffman25]I'm trying again to generate the .deb's but the ati installer doesn't generate them, instead it gives NO errors:
```

sudo sh ./ati-driver-installer-8.18.8-i386.run --buildpkg Ubuntu/breezy
[...]
Generating package: Ubuntu/breezy
/tmp/fglrx ~/Desktop/ati/fglrx-install
~/Desktop/ati/fglrx-install
Removing temporary directory: fglrx-install
javier@A1691:~/Desktop/ati$ ls
ati-driver-installer-8.18.8-i386.run   Xorg.0.log         xorg.conf.txt
fglrx-installer_8.18.8-1_i386.changes  Xorg.0.log.tar.gz

```

I have everything you recommended to be installed before generating the dev[/QUOTE]
I found them in /tmp/

---

### Post by Kimppa on 2005-10-31
[QUOTE=mlomker]
That's the wrong path for the latest driver.  You may have followed these instructions but you must have made other attempts in the past.  You might have to do a fresh install to get things back to defaults before the drivers will work for you.

Should be:

```

        libGL.so.1 => /usr/lib/libGL.so.1 (0x4286d000)

```

The only thing that I'd suggest doing is deleting the /etc/ld.so.conf file if it exists and then run **sudo ldconfig**.[/QUOTE]


Yes, I had _a few_ attempts on other how-to:s before trying yours. I did what you suggested and now it is working. Thank you a lot!

---

### Post by MarcoL on 2005-11-01
Hi,

when I try to install the driver, I get the following error:
```

marco@ubuntu:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.18.8-1_i386.deb
(Lettura del database ... 64934 file e directory attualmente installati.)
Spacchetto xorg-driver-fglrx (da xorg-driver-fglrx_8.18.8-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/ 
libGL.so.1.2 by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so. 1.2 to
 /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: errore processando xorg-driver-fglrx_8.18.8-1_i386.deb (--install):
 il sottoprocesso pre-installation script ha restituito un codice di errore 2
Sono occorsi degli errori processando:
 xorg-driver-fglrx_8.18.8-1_i386.deb
marco@ubuntu:~/Desktop$

```

Previously I installed the driver 8.16.20, but I had it to remove because the resolution bug.

I'm quite a newbie, so I don't know what kind of info about my system are useful here.

Thanks in advance.

---

### Post by ouminan on 2005-11-01
I'm using the instructions in the HOW-TO for 8.18.x off a fresh installation of 64-bit Breezy, and I'm getting this problem...

Upon executing:
```
sudo sh ./ati-driver-installer-8.18.8-x86_64.run --buildpkg Ubuntu/breezy
```

It does a bunch of stuff and then errors out at:
```
dh_install -pxorg-driver-fglrx "debian/70fglrx"           "etc/X11/Xsession.d"
cp: cannot stat `./debian/70fglrx': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
~/fglrx-install
Removing temporary directory: fglrx-install
```

Any insight as to what went wrong?

---

### Post by mlomker on 2005-11-01
> I'm quite a newbie, so I don't know what kind of info about my system are useful here.


I'm not sure what your question is.  Did you run **apt-get upgrade**?

```

You might get some errors regarding dependencies during the installation. You can ignore them since they should be resolved when you run the upgrade step.

```

---

### Post by mlomker on 2005-11-01
> Any insight as to what went wrong?

Yeah, I think that's a bug with the 64-bit installer since I also had it.  I had to copy that 70fglrx file from the directory that it is in to underneath the packages/Ubuntu/debian folder.  I don't recall exactly what directory it was in.

I'll send a message to Septor about it.

---

### Post by MarcoL on 2005-11-01
[QUOTE=mlomker]I'm not sure what your question is.  Did you run **apt-get upgrade**?
[/QUOTE]

Thanks for your reply :) 

I did get an error  regarding dependencies when I typed 
```
sudo dpkg -i fglrx-control_8.18.8-1_i386.deb
```
and according to your how-to I ignored it.

But this error seems different to me, so I stopped the installation.
So the question may be: 
Is it a "normal" error? Is it safe to proceed? 

(sorry for my english)

---

### Post by ouminan on 2005-11-01
> I had to copy that 70fglrx file from the directory that it is in to underneath the packages/Ubuntu/debian folder.

Thanks for the quick reply. :)

Would you happen to remember offhand where the 70fglrx file is?  I wanted to do the same, but couldn't locate the file.

Thank you!

---

### Post by Septor on 2005-11-01
[QUOTE=ouminan]Thanks for the quick reply. :)

Would you happen to remember offhand where the 70fglrx file is?  I wanted to do the same, but couldn't locate the file.

Thank you![/QUOTE]

It looks like ATI missed some of my files when they made the 64bit installer.  The 32bit installer is fine though so you could just copy the 70fglrx file from the 32bit installer (fglrx-install/packages/Ubuntu/debian/70fglrx) to the 64bit one.  The packages/Ubuntu directories _should_ be identical between the 32 and 64bit versions however it seems the the following files are missing from the 64bit one:
```

$ diff -ru 64/fglrx-install/packages/Ubuntu 32/fglrx-install/packages/Ubuntu
Only in 32/fglrx-install/packages/Ubuntu/debian: 70fglrx
Only in 32/fglrx-install/packages/Ubuntu/debian: fireglcontrol.desktop
Only in 32/fglrx-install/packages/Ubuntu/debian: fireglcontrol.kdelnk
Only in 32/fglrx-install/packages/Ubuntu/module: postinst

```

The safest, and probably easiest way to fix this would be to delete the 64bit packages/Ubuntu directory and then just copy the same directory back from the 32bit installer... of course then you need to download the whole 32bit installer.  

I am attaching a tarbal containing the entire packages/Ubuntu directory that you can use instead of downloading the whole 32bit ati-installer.  Just unpack it into the extracted fglrx-install directory and then build the packages.

Remember: when building the packages from inside the fglrx-install directory to run "umask 002" first!

I'll get ATI to fix this in the next release.

---

### Post by jiahanhao on 2005-11-02
at long last, my ordeal with the ati drivers is over...

i am running an amd64 generic arch on a p4 3.2 ghz laptop running an ati mobility radeon x800....

i followed the steps in the walkthrough, with the exception of running the ati shell script in graphical mode, with the --keep option enabled at command line. I downloaded the tarball provided by septor, rm -rf'd the packages file in the fglrx-install directory after the program bombed out, moved the untarred packages directory into the fglrx-install dir, and then (i had two terminals open at the time) i entered into an archaic looking ati installer window, which i ctrl-c'd to exit, after which all the deb packages magically appeared...

ran through the steps of the module-assistant stuff, and got to the point where fglrx.ko wouldn't modprobe. i downloaded hexcurse from the repositories, then edited the fglrx.ko file with it (found this trick over at rage3d.com). searched for the closest supported chipset (the 5d48 mobility x800 xl, the complete list of supported chips is available in the Xorg.0.log), which was in little endian of 485d, replaced the 8 with an A (from the lspci output for my video card, 5d4a),  ran aticonfig, added ChipID 0x5d48 to the fglrx device section, downloaded the old libdri.a, copied this to the /usr/X11R6/lib/modules/extensions directory, rebooted, and somehow, finally everything worked...

no drmMap error, no device not found error, no broken symlinks, and all it took was 3 weeks of my life.

i'm thinking of writing a python script to do all this junk for you, if anyone is interested (lots of struct.unpacks looming on the horizon) but i'll need to set up an ftp server to host all the deb files and whatnot first...

---

### Post by Septor on 2005-11-02
[QUOTE=jiahanhao]at long last, my ordeal with the ati drivers is over...

i am running an amd64 generic arch on a p4 3.2 ghz laptop running an ati mobility radeon x800....

i followed the steps in the walkthrough, with the exception of running the ati shell script in graphical mode, with the --keep option enabled at command line. I downloaded the tarball provided by septor, rm -rf'd the packages file in the fglrx-install directory after the program bombed out, moved the untarred packages directory into the fglrx-install dir, and then (i had two terminals open at the time) i entered into an archaic looking ati installer window, which i ctrl-c'd to exit, after which all the deb packages magically appeared...

ran through the steps of the module-assistant stuff, and got to the point where fglrx.ko wouldn't modprobe. i downloaded hexcurse from the repositories, then edited the fglrx.ko file with it (found this trick over at rage3d.com). searched for the closest supported chipset (the 5d48 mobility x800 xl, the complete list of supported chips is available in the Xorg.0.log), which was in little endian of 485d, replaced the 8 with an A (from the lspci output for my video card, 5d4a),  ran aticonfig, added ChipID 0x5d48 to the fglrx device section, downloaded the old libdri.a, copied this to the /usr/X11R6/lib/modules/extensions directory, rebooted, and somehow, finally everything worked...

no drmMap error, no device not found error, no broken symlinks, and all it took was 3 weeks of my life.

i'm thinking of writing a python script to do all this junk for you, if anyone is interested (lots of struct.unpacks looming on the horizon) but i'll need to set up an ftp server to host all the deb files and whatnot first...[/QUOTE]


Good job!  I'm tired out just from reading your post :)

Please open a new bug and post your "lspci -vv" and "lspci -n" info for your card at [http://ati.cchtml.com](http://ati.cchtml.com)

---

### Post by mlomker on 2005-11-02
> i'm thinking of writing a python script to do all this junk for you, if anyone is interested (lots of struct.unpacks looming on the horizon) but i'll need to set up an ftp server to host all the deb files and whatnot first...

If your experience is anything like mine you'll go through all the work and then ATI will release v 8.18.10 with all of your fixes already in it two days after you're done.  I'd agree with filing the bug report but I wouldn't bother with doing the work for ATI, if I were you.

---

### Post by rcamanda on 2005-11-02
I have to thank you.  That is an excellent guide.  After days and days of frustration, restarts reinstalls, I finally did it following your excellent HOWTO.
However, LOL I forgot to do the madwifi section.  My wifi still works, but just in case it causes me problems down the road is there anything else I can do?

---

### Post by JuanC on 2005-11-02
[QUOTE=Septor]It looks like ATI missed some of my files when they made the 64bit installer.  The 32bit installer is fine though so you could just copy the 70fglrx file from the 32bit installer (fglrx-install/packages/Ubuntu/debian/70fglrx) to the 64bit one.  The packages/Ubuntu directories _should_ be identical between the 32 and 64bit versions however it seems the the following files are missing from the 64bit one:
```

$ diff -ru 64/fglrx-install/packages/Ubuntu 32/fglrx-install/packages/Ubuntu
Only in 32/fglrx-install/packages/Ubuntu/debian: 70fglrx
Only in 32/fglrx-install/packages/Ubuntu/debian: fireglcontrol.desktop
Only in 32/fglrx-install/packages/Ubuntu/debian: fireglcontrol.kdelnk
Only in 32/fglrx-install/packages/Ubuntu/module: postinst

```

The safest, and probably easiest way to fix this would be to delete the 64bit packages/Ubuntu directory and then just copy the same directory back from the 32bit installer... of course then you need to download the whole 32bit installer.  

I am attaching a tarbal containing the entire packages/Ubuntu directory that you can use instead of downloading the whole 32bit ati-installer.  Just unpack it into the extracted fglrx-install directory and then build the packages.

Remember: when building the packages from inside the fglrx-install directory to run "umask 002" first!

I'll get ATI to fix this in the next release.[/QUOTE]

How to build the packages?

I try ```
./ati-packager.sh
``` but don't work

---

### Post by vicomte on 2005-11-02
Hi, I've read every Howto I could and done them all over and over and I'd be very keen for someone to tell me whats going on thats wrong.

I hope there is all the information below you need. If there is anything else you need to help me diagnose the problem, let me know.

I'm stubborn as hell and have spent many many hours trying to get this to work. Now I am asking for help.

I have an AMD machine, my kernel is 2.6.12-9-k7 which I apt-get'd

FGLRXINFO
> root@ZEUS:/usr/src# fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

LSMOD | GREP FGLRX
> root@ZEUS:/usr/src# lsmod | grep fglrx
fglrx                 260512  0
agpgart                34888  2 fglrx,via_agp


GLXINFO
> root@ZEUS:/usr/src# glxinfo
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



XORG.CONF
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Buttons" "7"
EndSection

Section "Monitor"
	Identifier   "SyncMaster 710n"
	Option	    "DPMS"
EndSection

Section "Device"

#	VideoRam	256
#	Option		"UseFBDev"		"true"
	Identifier  "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
	Monitor    "SyncMaster 710n"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection



---

### Post by vicomte on 2005-11-02
XORG.0.LOG
> 
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ZEUS 2.6.12-9-k7 #1 Mon Oct 10 13:47:52 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-k7 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:47:52 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  3 09:32:29 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster 710n"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"

SNIP

(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AR [Radeon 9600] rev 0, Mem @ 0xc0000000/28, 0xdfef0000/16, I/O @ 0xc800/8, BIOS @ 0xdfec0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) rev 0, Mem @ 0xb0000000/28, 0xdfee0000/16
SNIP

(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(WW) Warning, couldn't open module GLcore
(II) UnloadModule: "GLcore"
(II) UnloadModule: "glx"
(II) Unloading /usr/X11R6/lib/modules/extensions/libglx.a
(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.18.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
.... SNIP

(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.18.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.18g2                           
(II) ATI Proprietary Linux Driver Build Date: Oct 25 2005 10:35:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.18.1-driver-lnx-221930
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 PRO (RV360 4152) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
...

	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9600 PRO (RV360 4152)" (Chipset = 0x4152)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x7c29)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xdfef0000
(--) fglrx(0): ROM-BIOS at 0xdfec0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) fglrx(0): Connected Display1: CRT on secondary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: 11e  Serial#: 1296707895
(II) fglrx(0): Year: 2004  Week: 47
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: H4JXB20319
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on secondary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 30 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
... Modelines ....

(++) fglrx(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.18.8
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): cpuSpeedMHz: 0x000005fd
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdfffde80 - 0xdfffdeff (0x80) MX[B]
	[8] -1	0	0xdfffdf00 - 0xdfffdfff (0x100) MX[B]
	[9] -1	0	0xdfffc000 - 0xdfffcfff (0x1000) MX[B]
	[10] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[11] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[12] -1	0	0xdffc0000 - 0xdffdffff (0x20000) MX[B]
	[13] -1	0	0xdfffe000 - 0xdfffffff (0x2000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xdfee0000 - 0xdfeeffff (0x10000) MX[B](B)
	[16] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xdfec0000 - 0xdfedffff (0x20000) MX[B](B)
	[18] -1	0	0xdfef0000 - 0xdfefffff (0x10000) MX[B](B)
	[19] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM Bus area:     0xc0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xc0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
Symbol __glXActiveScreens from module /usr/X11R6/lib/modules/drivers/fglrx_drv.o is unresolved!
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "7"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 7
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) 3rd Button detected: disabling emulate3Button



DRIVERS I'M USING
> 
root@ZEUS:/usr/src/ati-drivers# ls
ati-driver-installer-8.18.8-i386.run   fglrx-sources_8.18.8-1_i386.deb
fglrx-control_8.18.8-1_i386.deb        xorg-driver-fglrx_8.18.8-1_i386.deb
fglrx-installer_8.18.8-1_i386.changes  xorg-driver-fglrx-dev_8.18.8-1_i386.deb
fglrx-kernel-source_8.18.8-1_i386.deb



LOCATE libGL
> root@ZEUS:~# locate libGL
/usr/lib/i686/mmx/cmov/libGL.so
/usr/lib/i686/mmx/cmov/libGL.a
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/i686/mmx/cmov/libGL.so.1
/usr/lib/libGL.so
/usr/lib/libGL.so.1
/usr/lib/libGLU.so.1
/usr/lib/dri/libGL.so
/usr/lib/libGLU.so.1.3.060302
/usr/lib/libGL.a
/usr/lib/libGLU.a
/usr/lib/libGLU.so
/usr/lib/libGL.so.1.2
/usr/lib/FGL.renamed.libGL.so.1.2
/usr/X11R6/lib/FGL.renamed.libGL.so.1.2
/usr/X11R6/lib/libGL.so.1.2
/usr/X11R6/lib/libGL.so
/usr/X11R6/lib/libGL.so.1


LOCATE libglx
> root@ZEUS:~# locate libglx
/usr/X11R6/lib/modules/extensions/libglx.a

---

### Post by mlomker on 2005-11-02
[QUOTE=vicomte]Hi, I've read every Howto I could and done them all over and over and I'd be very keen for someone to tell me whats going on thats wrong.
[/QUOTE]

What do you get from **dmesg | grep fglrx**?  Do you have errors in /var/log/Xorg.0.log?

---

### Post by vicomte on 2005-11-03
> vic@ZEUS:~$ dmesg | grep fglrx
[4294685.853000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294685.855000] [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
[4294685.855000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4343865.788000] [fglrx] module unloaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4343881.101000] [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
[4343881.101000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4343881.109000] [fglrx] module unloaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4344355.906000] [fglrx] Maximum main memory to use for locked dma buffers: 681 MBytes.
[4344355.907000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0



Xorg.O.log warnings
> vic@ZEUS:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) Warning, couldn't open module GLcore
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Errors

> vic@ZEUS:~$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "glx" (a required submodule could not be loaded, 0)

Thanks, your help is highly appreciated

---

### Post by niko_ on 2005-11-03
vicomte, i dont know why you get this, since you have your xorg.conf right configured.
the problem is here:

Section "Module"
Load "GLcore"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

but it seems you have glx there, so something is blocking it or your xorg is broken.
my latest fglrx works fine and i have a bit different module section in xorg.conf
well i have "dbe" instead "GLcore", maybe it would also work for you. good luck.

---

### Post by mitsu on 2005-11-03
I have a Pundit-R which has Radeon 9100 IGP running on Ubuntu Breezy with custom kernel 2.6.13.4. I have tried to install ATI drivers using the howto but still have OpenGL vendor:Mesa etc. Glxgears 280 FPS. /var/log/Xorg.0.log gives warning that DRI is not supported on Radeon 9100 IGP. Seems that I have to change to radeon drivers using this method: [http://wiki.debian.org/?radeonIGPsDR](http://wiki.debian.org/?radeonIGPsDR). Is there any chance to get the fglrx drivers work on my system.

root@HDLinux:~# dmesg | grep fglrx
[17179603.312000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179603.316000] [fglrx] Maximum main memory to use for locked dma buffers: 373 MBytes.
[17179603.316000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[17179603.336000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[17179603.336000] [fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[17179603.336000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[17179603.668000] [fglrx] free  AGP = 54800384
[17179603.668000] [fglrx] max   AGP = 54800384
[17179603.668000] [fglrx] free  LFB = 53211136
[17179603.668000] [fglrx] max   LFB = 53211136
[17179603.668000] [fglrx] free  Inv = 0
[17179603.668000] [fglrx] max   Inv = 0
[17179603.668000] [fglrx] total Inv = 0
[17179603.668000] [fglrx] total TIM = 0
[17179603.668000] [fglrx] total FB  = 0
[17179603.668000] [fglrx] total AGP = 16384

/var/log/Xorg.0.log:
...
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.18.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.18g2                
(II) ATI Proprietary Linux Driver Build Date: Oct 25 2005 10:35:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.18.1-driver-lnx-221930
(--) Assigning device section with no busID to primary device
(**) ChipID override: 0x5834
(**) Chipset RADEON 9100 IGP (RS300 5834) found
...
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(**) fglrx(0): Chipset: "RADEON 9100 IGP (RS300 5834)" (Chipset = 0x5834)
(**) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x8107)
(**) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe8000000
(--) fglrx(0): MMIO registers at 0xfde00000
(--) fglrx(0): ROM-BIOS at 0xfdd00000
...
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 65536 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9100 IGP
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: RS3
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(--) fglrx(0): VideoRAM: 65536 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
...
(WW) fglrx(0): Specified desktop setup not supported: 8
...
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
        compiled for 6.8.0, module version = 8.18.8
        ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x00000bb1
(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"
(**) fglrx(0): using built in AGPGART module: no
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
...
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:5:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xdcbf2000
(II) fglrx(0): [drm] mapped SAREA 0xdcbf2000 to 0xb7aec000
(II) fglrx(0): [drm] framebuffer handle = 0xe8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.18.8
(II) fglrx(0):     Date: Oct 25 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.13.4-custom
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfde00000
(II) fglrx(0): [agp] Mode=0x1f00021b bridge: 0x1002/0x5833
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00031a
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xdce81000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0x1c000000 FBMappedSize: 0x005c1000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1178)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): Using software cursor
(WW) fglrx(0): Option "EnablePageFlip" is not used
(WW) fglrx(0): Option "AGPMode" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM

---

### Post by mlomker on 2005-11-03
> 
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found


If you look at your xorg.conf you'll see that your device section refers to 1:0:0.  That's a problem.  You should be able to just remove that line.

Try creating a new xorg.conf using the [online generator.]("http://www.objorkum.com/scripts/fglrxconfig/")

---

### Post by mlomker on 2005-11-03
> I have a Pundit-R which has Radeon 9100 IGP running on Ubuntu Breezy with custom kernel 2.6.13.4.

Have you had the fglrx drivers work under linux with this hardware before?  I have no experience with using custom kernels with the driver, so if you can work with the Ubuntu kernel then that'd be best.  The driver itself is reporting that it doesn't support your card, which is interesting.  I thought all 8500+ cards were supported.

I'd recommending heading over to [ATI's forum]("www.rage3d.com/board/forumdisplay.php?f=88") and post there.

---

### Post by mitsu on 2005-11-03
Fglrx kind of worked with standard Breezy. There were problems: most screensavers got stuck and glxgears didn't work either. But fglrxinfo reported ATI driver.

Unfortunately I have a Twinhan digital satellite card which works only with the latest dvb-kernel which in turn needs the latest kernel. So I have to get my display drivers work with it as well.

---

### Post by mlomker on 2005-11-03
> So I have to get my display drivers work with it as well.

I understand that is your eventual goal, but if you can get them to work with the Ubuntu kernel then you can isolate the problem to your custom kernel's parameters....

---

### Post by rcamanda on 2005-11-03
I noticied in /etc/X11/xorg.conf the Device section shows the driver as "ATI"  and further down a duplicate section that shows the driver as "fglrx".   Is this the key component in allowing the official ATI driver to work?

---

### Post by eddye on 2005-11-03
Hy I am a new user of linux UBUNTU
I have it for about 3 days and couple of hours.

The probmem is this :
Cant get [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.3-9ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.3-9ubuntu4_i386.deb)  Neujemanje vsote MD5 ( i dont know how to translate)
E: Nekaterih arhivov ni mogo&#269;e dobiti. Poskusite uporabiti apt-get update ali --fix-missing.(It says i can't get some arhives. Please try apt-get update or --fix-missing) This is ewen if i type only apt-get install gcc3-4

I tryed everything :( 
and sorry of my bad english

---

### Post by mlomker on 2005-11-03
> I tryed everything :( 


The main Ubuntu repo seems to get out of synch a lot.  Try using [one of the mirrors]("https://wiki.ubuntu.com/Archive") instead, perhaps one that is closer to you.

I attached a copy of my sources.list.  You can edit it to use a different repository and then save it as /etc/apt/sources.list.

---

### Post by vicomte on 2005-11-03
[QUOTE=mlomker]If you look at your xorg.conf you'll see that your device section refers to 1:0:0.  That's a problem.  You should be able to just remove that line.

Try creating a new xorg.conf using the [online generator.]("http://www.objorkum.com/scripts/fglrxconfig/")[/QUOTE]


No, commenting that out won't help. My card detects ID's 1:0:0 and 1:0:1 as theire is 2 video out ports on the card. One is DVI and then other is standard VGA. Creating a second device section fix's this, though I only use one monitor. That error has no impact on my ability to use GL.

---

### Post by mlomker on 2005-11-03
> One is DVI and then other is standard VGA. 

Ah, ok.  I see an error about being unable to load GLcore.  Have you verified the permissions in that directory?

```

mlomker@mlomkernote:/usr/X11R6/lib/modules/extensions$ ls -l
total 3015
-rw-r--r--  1 root root   15928 2005-10-10 13:10 libdbe.a
-rw-r--r--  1 root root   29410 2005-10-10 13:10 libdri.a
-rw-r--r--  1 root root  151264 2005-10-10 13:10 libextmod.a
-rw-r--r--  1 root root 2331122 2005-10-10 13:10 libGLcore.a
-rw-r--r--  1 root root  481602 2005-10-10 13:10 libglx.a
-rw-r--r--  1 root root   24096 2005-10-10 13:10 librecord.a
-rw-r--r--  1 root root   38374 2005-10-10 13:10 libxtrap.a

```

---

### Post by Septor on 2005-11-03
[QUOTE=mitsu]Is there any chance to get the fglrx drivers work on my system.
(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"
[/QUOTE]

I'd have to say no.  The "radeon" driver should work though, and it is installed by default in Ubuntu so should run without problems.

---

### Post by eddye on 2005-11-04
Code:

sudo module-assistant prepare
sudo module-assistant update (I came to here and it downloaded some files for about 27min and then the error was shown)
sudo module-assistant a-i fglrx

Now to update your xorg.conf for fglrx (there are a variety of ways of doing this):


Code:

sudo aticonfig --initial


Ive dome this do i have to do something else??

---

### Post by adam.tropics on 2005-11-04
Been following this thread for..well, a while....much frustration. But half way there.
Have fglrx working. ATI Radeon Xpress 200m, toshiba laptop. Plus also have the 1280*800 resolution, all looking fantastic. Not sure quite how it all works, but it works, i tried so many things, i totally confused myself.
Anyway 2 things. 1/ How do I permanently save the whole ubuntu current setup before i total it again!!! and 2/ I'm not sure if i have done all i can do as dvd still struggle to play badly. Also my panels strugglesunless I stick with solid colour or system defaults??? I only have 256 memory, 64 is shared with ATI, can upgrade the memory next week which i am told will give the ATI 128, will that be enough or is there more to do. Not sure what you need to see in terms of files... any help welcome plus many thanks to all who contributed to this thread. Try reading it from start to end though....getting confusing...even for linux!!

---

### Post by Pettman on 2005-11-04
I have followed the how-to, read this thread from the beginning to end, read other threads and still get ```
pettman@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
pettman@ubuntu:~$ glxgears -printfps
1712 frames in 5.3 seconds = 324.194 FPS
1680 frames in 5.3 seconds = 315.232 FPS
1680 frames in 5.3 seconds = 314.795 FPS
1680 frames in 5.3 seconds = 315.372 FPS

```I am starting to get sick of trying to get the drivers working.
I run the 32-bit version of ubuntu 5.10 on a AMD Athlon XP2800+, ASUS A7V600 motherboard (with VIA KT600 nothbridge, VIA VT8237 southbridge), HIS ATi Radeon 9600 Pro (the devicemanager says something about RV350 AP), 1024 MB  DDR400 (PC3200) RAM (two 512 MB modules). If there is anything else you need to know in order to help med say so.

EDIT: Forgott glxgears -printfps running in the backgruond for a while and i reached a fps above 600 at times.

EDIT2: In the Xorg.0.log I found the following errors ```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
``` in the .xsession-errors there were nothing that seemed relevant to me.

edit3: installed the .deb package generated by the 8.18.8 package so it should not be anything funny with that.

---

### Post by adam.tropics on 2005-11-04
Don't know why this worked, but installed the fglrx driver, then used *fglrxconfig* _instead_ of *dpgk-reconfigure.*..... It went through the configuration, probed and did not recognise the exact video card as being supported, but on reboot, all worked. Well, much better than before. Particularly pleased about being back to 1280*800!  

As for glxgears....I see a lot of postings here with their details, but being new here....at what point is it meant to be ok, and what point a dead loss?? And why are the fgl_glxgears reporting different frame rates???

---

### Post by vicomte on 2005-11-04
[QUOTE=mlomker]Ah, ok.  I see an error about being unable to load GLcore.  Have you verified the permissions in that directory?

```

mlomker@mlomkernote:/usr/X11R6/lib/modules/extensions$ ls -l
total 3015
-rw-r--r--  1 root root   15928 2005-10-10 13:10 libdbe.a
-rw-r--r--  1 root root   29410 2005-10-10 13:10 libdri.a
-rw-r--r--  1 root root  151264 2005-10-10 13:10 libextmod.a
-rw-r--r--  1 root root 2331122 2005-10-10 13:10 libGLcore.a
-rw-r--r--  1 root root  481602 2005-10-10 13:10 libglx.a
-rw-r--r--  1 root root   24096 2005-10-10 13:10 librecord.a
-rw-r--r--  1 root root   38374 2005-10-10 13:10 libxtrap.a

```[/QUOTE]

Seems I'm missing a libglx.a / .so

where do I get that?

> vic@ZEUS:/usr/X11R6/lib/modules/extensions$ ls -l
total 296
-rw-r--r--  1 root root  15928 2005-10-11 04:10 libdbe.a
-rw-r--r--  1 root root  29410 2005-10-25 10:45 libdri.a
-rw-r--r--  1 root root  29410 2005-10-11 04:10 libdri.a_old
-rw-r--r--  1 root root 151264 2005-10-11 04:10 libextmod.a
lrwxrwxrwx  1 root root      9 2005-11-03 22:25 libglx.a -> libglx.so
-rw-r--r--  1 root root  24096 2005-10-11 04:10 librecord.a
-rw-r--r--  1 root root  38374 2005-10-11 04:10 libxtrap.a

---

### Post by geearf on 2005-11-04
Hello,

can anyone get suspend to ram with this, cause I hope this would fix the problem but still not :(

---

### Post by z!cHz@cH on 2005-11-04
Hi, 

I tried this Howto on my notebook but gnome doesnt start anymore.

I think the driver doesnt support my Graphics card.

Ati radeon 320M igp.

Does someone now how to get it to work with this card?

update:

I managed to start gnome again by restoring a xorg.conf backup.

my fps with glxgears is 110 max (small window).

please help me.

---

### Post by mlomker on 2005-11-04
> sudo module-assistant update (I came to here and it downloaded some files for about 27min and then the error was shown)


You shouldn't get an error at that point.  Did your **sudo apt-get update** complete properly?  The **module-assistant prepare** step will often download your linux-headers but should not generate any errors.  I believe the **update** step only takes seconds to run.

---

### Post by mlomker on 2005-11-04
> 1/ How do I permanently save the whole ubuntu current setup before i total it again!!! 

Do you have a second partition or an external hard disk that you can save to?  Download a copy of Knoppix and use the **partimage** tool to back up your system partition.  That's what I do...I can switch back and forth between Ubuntu versions and installs in 10 minutes or less.

> and 2/ I'm not sure if i have done all i can do as dvd still struggle to play badly. Also my panels strugglesunless I stick with solid colour or system defaults???

If **glxgears -printfps** is giving you 1000+ fps then there's nothing more to be done with the video drivers.  Have you checked DMA settings for your drives? (assuming they are IDE and not sata).

> Try reading it from start to end though....getting confusing...even for linux!!

It really can't be read that way because it covers the previous 8.18.6 and the current .8, which had different problems.

---

### Post by mlomker on 2005-11-04
> can anyone get suspend to ram with this, cause I hope this would fix the problem but still not :(

No, ATI doesn't support it.  That is in the FAQ on their website.

---

### Post by mlomker on 2005-11-04
> 
I think the driver doesnt support my Graphics card.
Ati radeon 320M igp.


It isn't supported by fglrx.[Here's]("http://rzr.online.fr/docs/comp/gfxcard.htm") the only website that I had found with useful information.  It would require a lot of work to recompile a kernel and the X server and even then you'll only get 190 fps.

I had one of these in my previous laptop and decided that it was time to upgrade.

---

### Post by geearf on 2005-11-04
[QUOTE=mlomker]No, ATI doesn't support it.  That is in the FAQ on their website.[/QUOTE]


Ooh I did not know that, so we are never gonna to get it work :(
I guess next laptop will be having a nvidia card then.

Anyway thanks,

---

### Post by scflymedic on 2005-11-04
Great how-to!  Followed the guide on page 1 without problems.  I have an emachines m6810 with ati mobility 9600 64mb ram, fresh install of breezy 5.10 with k7 kernal, fglrx_gears in at around 354fps and glxgears around 2100fps.  Thanks!

---

### Post by mlomker on 2005-11-04
> I guess next laptop will be having a nvidia card then.


That's an option but there are plenty of problems with Nvidia as well.  The Mobility 9600, 9700, and X-series cards work fine.

---

### Post by Pettman on 2005-11-04
I have put some additions in my previous post ([http://www.ubuntuforums.org/showthread.php?p=466408#post466408](http://www.ubuntuforums.org/showthread.php?p=466408#post466408))

---

### Post by mlomker on 2005-11-04
>  "xf86_ENOMEM"


What kernel are you using?  This is a common error that you'll find a lot of hits on in Google.  It's related to the kernel and the agpgart.  What do you get from **lsmod | grep gart** and **dmesg | grep fglrx**?

You might want to make a post on the [Rage3d forum ]("www.rage3d.com/board/forumdisplay.php?f=88").

---

### Post by geearf on 2005-11-04
[QUOTE=mlomker]That's an option but there are plenty of problems with Nvidia as well.  The Mobility 9600, 9700, and X-series cards work fine.[/QUOTE]
Hello,

I don't know, I have an nvidia on my desktop without problem, but I never tried suspend to ram with it ..

---

### Post by mitsu on 2005-11-06
[QUOTE=Septor]I'd have to say no.  The "radeon" driver should work though, and it is installed by default in Ubuntu so should run without problems.[/QUOTE]

I found a report of working older version of fglrx driver in Pundit-R so it should be possible. Anyway, I gave up and configured radeon driver included in the 2.6.13.4 kernel. That gives 720 FPS in glxgears. I guess that is good enough.

---

### Post by mlomker on 2005-11-06
> I don't know, I have an nvidia on my desktop without problem, but I never tried suspend to ram with it 

Ah, I forgot what we were talking about.  Right...none of the ATI's will support suspend.

---

### Post by Pettman on 2005-11-06
[QUOTE=mlomker]What do you get from **lsmod | grep gart** and **dmesg | grep fglrx**?[/QUOTE]
This: ```
pettman@ubuntu:~$ lsmod | grep gart
agpgart                32328  2 via_agp,fglrx
pettman@ubuntu:~$ dmesg | grep fglrx
[4294688.042000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294688.044000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294688.045000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[4294718.732000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294718.732000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294718.732000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294718.732000] [fglrx] AGP detected, AgpState   = 0x1f000a0f (hardware caps of chipset)
[4294718.732000] [fglrx:firegl_unlock] *ERROR* Process 8151 using kernel context 0
```

---

### Post by mlomker on 2005-11-06
> 
[4294718.732000] [fglrx:firegl_unlock] *ERROR* Process 8151 using kernel context 0[/code]

What kernel?  **uname -r**

There are quite a few threads with people having the unlock problem.  I don't have a solution for it.  One poster told me that he did a clean reload of Breezy and the problem went away.  My only guess would be that it is due to mismatched file versions, but I haven't seen a solid answer to the problem.

---

### Post by Pettman on 2005-11-06
[QUOTE=mlomker]What kernel?  **uname -r**[/QUOTE]
It sais "2.6.12-9-386".

---

### Post by adam.tropics on 2005-11-07
With the fglrx drivers when you enter the amount of video memory, on a card which can theoretically adjust that (ATI from 64 to 128 ), are you actually making that adjustment or just reporting a known amount?

Also Mlomker as you seem to be the knowledgable person around here, could you heck [this out if you have time...]("http://www.ubuntuforums.org/showthread.php?t=87023")

Many thanks.

---

### Post by mlomker on 2005-11-07
[QUOTE=adam.tropics]With the fglrx drivers when you enter the amount of video memory, on a card which can theoretically adjust that (ATI from 64 to 128 ), are you actually making that adjustment or just reporting a known amount?[/quote]

If you're referring to the configuration of your xorg.conf file then you're just informing the driver because it isn't automatically detecting it properly for some reason.  If you have a card that uses shared memory then that's actually configured in your system BIOS.

---

### Post by Heliode on 2005-11-07
Thanks for this Howto, it was easy to execute and works perfectly for me now. The only things I ran into were the *debs not appearing in my download dir, but in /tmp. Also, for some strange reason, I had to reboot before the fglrx driver worked; ctrl+alt+backspace wasn't enough.
Other than that, it was very smooth. I finially got my laptop up to 1400x1050. Never imagined it was a bug in the driver... I just figured I must've screwed something up myself.

Thanks again!

---

### Post by mlomker on 2005-11-07
> I had to reboot before the fglrx driver worked; ctrl+alt+backspace wasn't enough.


That can happen if you were using the previous fglrx--either it is already in memory or the kernel module dependencies are still seeing the previously installed driver.  There are so many variables that I have to assume a fresh Breezy install and that the user is currently running the ATI driver.

---

### Post by Heliode on 2005-11-07
In that case I guess I'll have to confess that I didn't reboot after removing the old module, since I wasn't using it at the time. Guess that didn't matter.

---

### Post by Jivicin on 2005-11-07
The HOW-TO worked perfectly.  Thankyou

---

### Post by rturner on 2005-11-08
Thanks as well.  I just put in my new Radeon 9200 SE and booted up, hoping Ubuntu would find the drivers, but not too surprised when X wouldn't load.  I went downstairs to another machine to research the card.  Found lots of information that had me scratching my head and then I found your HOW TO.  I ended up reading it on the other machine and making changes via SSH.  

Everything seemed to work fine from the remote computer until I tried the fglrxinfo test at the end, which had errors.  I came upstairs and the Ubuntu machine was loaded with X, so I ran fglrxinfo there and got perfect results.  Must've been something you can't run remotely.

---

### Post by Riot5 on 2005-11-08
Howdy,

I've been using Linux for all of 3 days now, and I wanted to get some 3D acceleration going, so I followed the howto for the 8.18 driver and now, if I use the fglrx driver, I get a black screen instead of a login screen when Ubuntu is starting up.  I can only use my computer if I go and switch back to the default "ati" driver in recovery mode.  What kinda stuff should I post that will help to solve this?

By the way, my card is an ATI Radeon 9800 XT, if that helps.

---

### Post by mlomker on 2005-11-09
> What kinda stuff should I post that will help to solve this?


You get the boot splash and whatnot and then a black screen....you don't get to GDM?  That could be a monitor detection problem, I suppose.  You'll want to look in the /var/log/Xorg.0.log file after a failed boot for errors.

---

### Post by MoidPale on 2005-11-10
Hi,

i followed your how-to and it worked almost, 

i still got the problem: no MTRRs available, i solved that following this:

I got it working on my Asus A4700K too.
 <HACK_ALERT>
 I'm using the latest linux-image-2.6.10-4-amd64-k8 kernel with all related packages (linux-restricted-modules, xorg-driver-fglrx, linux-headers, etc)
 
 I also got the fglrx-kernel-source package.
 Went into /usr/src/modules/fglrx-kernel/fglrx/build_mod and patched firegl-public.c by replacing all occurences of the CONFIG_MTRR define with XCONFIG_MTRR so that the module thinks MTRR is not compiled into the kernel.
 Went into /usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x, ran make, and placed the resulting fglrx.ko in 
 /lib/modules/2.6.10-4-amd64-k8/kernel/drivers/video/
 
 Rebooted and voilà, DRI !
 </HACK_ALERT>

this way i have no problems with the fglrx-driver anymore:

dmesg gives me:

[   73.404910] [fglrx] module loaded - fglrx 8.18.6 [Oct 11 2005] on minor 0
[   73.417529] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[   73.417535] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[   73.417565] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   73.417580] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   73.417622] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   73.417631] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   73.422000] [fglrx] free  AGP = 121909248
[   73.422004] [fglrx] max   AGP = 121909248
[   73.422006] [fglrx] free  LFB = 52719616
[   73.422008] [fglrx] max   LFB = 52719616
[   73.422010] [fglrx] free  Inv = 0
[   73.422011] [fglrx] max   Inv = 0
[   73.422013] [fglrx] total Inv = 0
[   73.422014] [fglrx] total TIM = 0
[   73.422016] [fglrx] total FB  = 0
[   73.422018] [fglrx] total AGP = 32768


and /var/log/Xorg.0.log:

II) fglrx(0): [drm] register handle = 0xfb9f0000
(II) fglrx(0): [agp] Mode=0x1f00421b bridge: 0x10de/0x00d1
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f00431a
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0x00581000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x005e9000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1210)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 800)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.


So i guess everything is allright there. But when i do fglrxinfo (after 'export LIBGL_DEBUG=verbose ') i get: 

libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib64/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib64/modules/dri/fglrx_dri.so: undefined symbol: _glapi_get_proc_offset)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib64/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib64/modules/dri/fglrx_dri.so: undefined symbol: _glapi_get_proc_offset)
libGL error: unable to find driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I have absolutely no idea what i did wrong

---

### Post by yyagol on 2005-11-10
hhhhmmmmmmm

so here is the deal i installed the ati 8.18.8 on a SUSE machine
well let me tell you all [COLOR="Red"]The same problem[/COLOR] with SUSE 10.0 and the fglrx.
so i reinstall Hoary and a for my wonder it works perfect 
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)
```

so i will stick to Hoary if i want a working machine thankyou all

---

### Post by Septor on 2005-11-10
[QUOTE=MoidPale]Hi,

i followed your how-to and it worked almost, 


So i guess everything is allright there. But when i do fglrxinfo (after 'export LIBGL_DEBUG=verbose ') i get: 

libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib64/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib64/modules/dri/fglrx_dri.so: undefined symbol: _glapi_get_proc_offset)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.18.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib64/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib64/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib64/modules/dri/fglrx_dri.so: undefined symbol: _glapi_get_proc_offset)
libGL error: unable to find driver: fglrx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I have absolutely no idea what i did wrong[/QUOTE]

Okay try doing this before running your app.
```

export LIBGL_DRIVERS_PATH=/usr/X11R6/lib/modules/dri:/usr/X11R6/lib32/modules/dri

```

Also since you are on a 64bit system, you can't use ATI's installer as it will put the 32bit and 64bit libraries in the wrong places on Ubuntu.  Check out the howto at  [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589) or [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Juzz on 2005-11-10
I have a problem with my drivers:

```
veggerby@Justinsnye:~$ sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 19,2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 165663 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Do you know what I can do?

---

### Post by greg_mci on 2005-11-10
No matter how often I try, I get this:

```
gregor@P4HT:~/Desktop$ sudo dpkg -i fglrx-control_8.18.8-1_i386.deb
Selecting previously deselected package fglrx-control.
(Reading database ... 77964 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.18.8-1_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-control:
 fglrx-control depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
dpkg: error processing fglrx-control (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-control
gregor@P4HT:~/Desktop$ sudo dpkg -i fglrx-kernel-source_8.18.8-1_i386.deb
(Reading database ... 77971 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.18.8-1 (using fglrx-kernel-source_8.18.8-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.18.8-1) ...
gregor@P4HT:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.18.8-1_i386.deb
(Reading database ... 77971 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.18.8-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx_8.18.8-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx_8.18.8-1_i386.deb
gregor@P4HT:~/Desktop$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 77971 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16_i386.deb (--unpack):
 trying to overwrite `/usr/bin/fireglcontrolpanel', which is also in package fglrx-control
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
gregor@P4HT:~/Desktop$ sudo module-assistant prepare
 apt-get  install linux-headers-2.6.12-9-686

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fglrx-control: Depends: xorg-driver-fglrx but it is not going to be installed
  linux-headers-2.6.12-9-686: Depends: linux-headers-2.6.12-9 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Done!
gregor@P4HT:~/Desktop$ sudo module-assistant update

Updated infos about 68 packages
gregor@P4HT:~/Desktop$ sudo module-assistant a-i fglrx
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fglrx-control: Depends: xorg-driver-fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Updated infos about 1 packages
gregor@P4HT:~/Desktop$ sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.1: cannot open shared object file: No such file or directory
gregor@P4HT:~/Desktop$


```

---

### Post by mlomker on 2005-11-10
> Do you know what I can do?

Hopefully Septor will see your post and reply to it.  Why are you removing it?

---

### Post by mlomker on 2005-11-10
I don't know why it's trying to install **/var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16_i386.deb** but I'd delete the file because that's the old version.

---

### Post by Juzz on 2005-11-10
[QUOTE=mlomker]Hopefully Septor will see your post and reply to it.  Why are you removing it?[/QUOTE]
I am trying to install the drivers as per the topic of this thread ;)

---

### Post by mlomker on 2005-11-10
[QUOTE=Juzz]I am trying to install the drivers as per the topic of this thread[/QUOTE]

Your post said **sudo apt-get remove** and that would remove drivers, not install them.  Removing the Ubuntu drivers would not create a diversion-related error because they do not utilize diversions.  Perhaps you need to provide more details about what you've already tried to install?

---

### Post by adam.tropics on 2005-11-11
Ok, all working, but having upgraded system memory, ATI uses a windows utility to up the video memory from 64 to 128 (radeon xpress 200m) which it has done. Linux now reports the remaining memory correctly, however the performance on glxgears has actually reduced! have re-run fglrxconfig but that had VideoRam commented out in the resulting file.(plus the commented out amount is 256, i thought it was meant to be in kb?)(have tried manually editing VideoRam but no different) 
So the question is how do i ensure that the system is actually using the available video memory (it's shared btw hence the upgrade)? ie is there a command which outputs it? and any idea why glxgears might suffer as a result?
Many thanks......again!

---

### Post by mlomker on 2005-11-11
[QUOTE=adam.tropics] ie is there a command which outputs it? and any idea why glxgears might suffer as a result?[/QUOTE]

If you do **dmesg | grep fglrx** shortly after bootup it'll list the memory that it is finding.  My previous laptop had shared memory and I didn't see any performance improvement when I changed the values.  It might get slower because the graphics chip has to manage more memory...

---

### Post by fallencan on 2005-11-11
hi

i just installed the 8.18.8 driver as described like here. everything installed flawlessly. after i edited the xorg.conf and rebooting the ubuntu xorg refused to start. after changing fglrx to ati i can start xorg again. what can be wrong while there is no error while installing the drivers? i'm new to linux and ubuntu so i don't know what can i do know. if u can help me i will be happy. thanks anyway.

---

### Post by mlomker on 2005-11-11
> i edited the xorg.conf and rebooting the ubuntu xorg refused to start.

Could you be more specific?  Did you get to the login prompt?  Did it boot normally but came up into a black screen?

The place to start looking is in the /var/log/Xorg.0.log and kern.log files after the failed boot.  You should be able to Ctrl-Alt-F2 over to another terminal and log in...if you are familiar with the command line.

---

### Post by adam.tropics on 2005-11-11
tried **dmesg | grep fglrx** and got
 [4294726.609000] [fglrx] Maximum main memory to use for locked dma buffers: 314 MBytes.
[4294726.609000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294726.622000] [fglrx:firegl_unlock] *ERROR* Process 7339 using kernel context 0


Had a look at Xorg log file, and some highlights are 
[I]
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4

###the drmOpenDevice runs all from /dev/dri/card0 to 254, then goes
###with 0.....

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''

(WW) fglrx(0): Kernel Module version does *not* match driver.

[/I]

Could this all be to do with my having got video all working then having upgraded to 686 kernel??

Also, given your last response, would i be better off then leaving the video card at 64mb and letting the system have the extra memory instead??

---

### Post by mlomker on 2005-11-11
> Also, given your last response, would i be better off then leaving the video card at 64mb and letting the system have the extra memory instead??

If you play games then you'll want to try a couple settings and check your frame rates.  I don't play games, so I chose to use the lower number.

If you installed the linux-restricted modules with your new kernel then that's your problem.  You can't have it installed if you're using the newer drivers.

---

### Post by Juzz on 2005-11-11
[QUOTE=mlomker]Your post said **sudo apt-get remove** and that would remove drivers, not install them.  Removing the Ubuntu drivers would not create a diversion-related error because they do not utilize diversions.  Perhaps you need to provide more details about what you've already tried to install?[/QUOTE]
Hey mlomker,

You can ignore my post - something didn't go as planned earlier, though when doing those commands previously didn't result in any major error - then I tried the steps again when that error came up.

Now after having been up in Winblows, I wanted to give it another go, and lo and behold the stuff worked :o :rolleyes: :D 

Heh, that even made me realize how poor the win version of Americas Army is - in linux I get flawless performance, but in winblows it was laggy :-&

EDIT: One minor thing though - even though I copied the driver file (ath_hal.ko) to the madwifi folder - then my Ath0 has disappeared from my system - though it shows up in lspci correct.

---

### Post by Juzz on 2005-11-11
[QUOTE=fallencan]hi

i just installed the 8.18.8 driver as described like here. everything installed flawlessly. after i edited the xorg.conf and rebooting the ubuntu xorg refused to start. after changing fglrx to ati i can start xorg again. what can be wrong while there is no error while installing the drivers? i'm new to linux and ubuntu so i don't know what can i do know. if u can help me i will be happy. thanks anyway.[/QUOTE]
One thing I noticed when trying this is that when you are going through the steps to create a new xorg.conf sometimes the font paths are incorrect.
Just copy those over from your backup.

---

### Post by PSyMastR on 2005-11-12
Well, this sucks.  I tried your guide, and all went well until i used the command ```
sudo aticonfig --initial
``` and restarted with ctrl+alt+backspace.  Now I cant get into graphical mode, and is posting this using w3m.  I tried using the fglrxinfo command and it gave me an error:
```
Error: unable to open display :0
```
Am I screwed or something?

---

### Post by Septor on 2005-11-12
[QUOTE=PSyMastR]Well, this sucks.  I tried your guide, and all went well until i used the command ```
sudo aticonfig --initial
``` and restarted with ctrl+alt+backspace.  Now I cant get into graphical mode, and is posting this using w3m.  I tried using the fglrxinfo command and it gave me an error:
```
Error: unable to open display :0
```
Am I screwed or something?[/QUOTE]
fglrxinfo only works if X is running... check your /var/log/Xorg.0.log for information on why X wouldn't start... and try a reboot if you haven't already.

---

### Post by adam.tropics on 2005-11-12
In case anyone needs to know, the ATI fglrx driver has gone to 8.19.x on the ATI site.

Also, ***don't download the installer via the first link***, cancel out and try the 'if you're having problems downloading....' link. 

The origonal link will only download two thirds of the file! Other link is fine though.

---

### Post by mlomker on 2005-11-12
[QUOTE=Juzz]EDIT: One minor thing though - even though I copied the driver file (ath_hal.ko) to the madwifi folder - then my Ath0 has disappeared from my system - though it shows up in lspci correct.[/QUOTE]

You might need to **sudo depmod -a**

---

### Post by mlomker on 2005-11-12
[QUOTE=adam.tropics]Also, ***don't download the installer via the first link***, cancel out and try the 'if you're having problems downloading....' link. 
[/QUOTE]

It looks like the new version is updated to fix the 64-bit problems and they've added code to support power management on laptops.  That's a biggie for some people.  I'll be curious to hear if that is working for Ubuntu.

I guess I'll start reloading my machine to try out these new drivers.

---

### Post by mlomker on 2005-11-12
I just tried an install on 64-bit (for 8.19.10) and the driver is broken, at least on my machine. I'm not sure what this error is yet, but it is one that I haven't seen in previous revisions:

```
 
mlomker@mlomkernote:~$ glxinfo
name of display: :0.0
libGL error: drmMap of sarea failed

``` 

The result, however, is that you end up with Mesa and no acceleration. I don't see any errors in Xorg.0.log or dmesg that would indicate a problem.

---

### Post by Juzz on 2005-11-12
[QUOTE=mlomker]You might need to **sudo depmod -a**[/QUOTE]
I think I already did that, but I'll give it another go ;)

---

### Post by Cuppa-Chino on 2005-11-12
Nope, looks like the new version 8.19.10 is no good for me.

Have system freezes again, anybody else?
In the last hour the system has frozen :
[LIST]
[*]during screen saver
[*]while running normaly
[*]during glxgears
[/LIST]
when freeze occurs, nothing but reset button gets me out of it, am running:

P4 2.4Ghz on Asus P4P800, 1gig PC4000 mem - no overclock with a ATI Radeon 9500 (9700 compatible, but system freezes irrespective of ChipID setting)

Any ideas? ](*,) I like Ubuntu and would like to continue using Linux for everything but if I have to fork out for an Nvidia card just to do it, that would be expensive!

> -ubuntu:~$ dmesg | grep fglrx
[4294708.291000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[4294708.291000] [fglrx] module loaded - fglrx 8.19.10 [Nov  9 2005] on minor 0
[4294709.210000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294709.210000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294709.210000] [fglrx] Kernel AGP support doesn't provide agplock functionalit y.
[4294709.210000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of  chipset)
[4294709.210000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294709.222000] [fglrx] free  AGP = 256126976
[4294709.222000] [fglrx] max   AGP = 256126976
[4294709.222000] [fglrx] free  LFB = 116387840
[4294709.222000] [fglrx] max   LFB = 116387840
[4294709.222000] [fglrx] free  Inv = 0
[4294709.222000] [fglrx] max   Inv = 0
[4294709.222000] [fglrx] total Inv = 0
[4294709.222000] [fglrx] total TIM = 0
[4294709.222000] [fglrx] total FB  = 0
[4294709.222000] [fglrx] total AGP = 65536

:arrow: need to change AGP in BIOS! to 256mb
:arrow:  *[fglrx] Internal AGP support requested, but kernel AGP support active. *could this be important
, but somehow that should not prevent freezes, have looked at **var/log/Xorg.0.log** but am cannot find anything in there, what am I looking for in there

---

### Post by Hollowman on 2005-11-12
Thanks for the great How-To:  worked like a charm for me.  I have been having problems with the driver since brezzy. but this works great. 


thanks

Hollowman

---

### Post by Cufishing on 2005-11-12
mlomker,
Once again my hat is off to you.
As the 'newb' I didn't figure it out, but with the little experience I have gained, I learned. DO NOT place the download in a special folder then try to run this how-to. It just don't work. Use your home folder. For some reason the pkg would not build a tmp folder??

Anyhow, I made it.

drew@OSS:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

drew@OSS:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
16548 frames in 5.0 seconds = 3309.525 FPS
16518 frames in 5.0 seconds = 3303.547 FPS
16529 frames in 5.0 seconds = 3305.798 FPS
16523 frames in 5.0 seconds = 3304.459 FPS
16458 frames in 5.0 seconds = 3291.412 FPS

drew@OSS:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2577 frames in 5.0 seconds = 515.400 FPS
2968 frames in 5.0 seconds = 593.600 FPS
3009 frames in 5.0 seconds = 601.800 FPS

---

### Post by souled on 2005-11-13
Ok, I'm starting to have a problem with the drivers. When the drivers were installed, the color of the screen was all bright and messed up (16 bit color?). I removed the drivers, and when I rebooted the color was back to normal. When I installed the 8.19 drivers, the problem with the colors started again. I have no idea what provoked the colors to be messed up all of a sudden. The drivers worked fine until I rebooted recently. I have no idea what's happening.

When trying to reinstall the 8.19 drivers, I get this error when I run sudo module-assistant a-i fglrx:
```

eric@motherland:~/download$ sudo module-assistant a-i fglrx
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2
modules/
modules/fglrx/
modules/fglrx/debian/
modules/fglrx/debian/changelog
modules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/debian/rules
modules/fglrx/debian/control.template
modules/fglrx/debian/dirs.template
modules/fglrx/debian/postinst
modules/fglrx/agp3.c
modules/fglrx/agpgart_be.c
modules/fglrx/firegl_public.c
modules/fglrx/i7505-agp.c
modules/fglrx/nvidia-agp.c
modules/fglrx/agp_backend.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/drm_compat.h
modules/fglrx/drm.h
modules/fglrx/drm_os_linux.h
modules/fglrx/drmP.h
modules/fglrx/drm_proc.h
modules/fglrx/firegl_public.h
modules/fglrx/make.sh
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/Makefile
Target package file
/usr/src/fglrx-kernel-2.6.12-9-386_8.18.6-1+2.6.12-9.23_i386.deb already
exists, not rebuilding!
Selecting previously deselected package fglrx-kernel-2.6.12-9-386.
(Reading database ... 103326 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-9-386 (from .../fglrx-kernel-2.6.12-9-386_8.18.6-1+2.6.12-9.23_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.12-9-386:
 fglrx-kernel-2.6.12-9-386 depends on xorg-driver-fglrx (= 8.18.6-1); however:
  Version of xorg-driver-fglrx on system is 8.19.10-1.
dpkg: error processing fglrx-kernel-2.6.12-9-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.12-9-386

I: Direct installation failed, trying to post-install the dependencies

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fglrx-kernel-2.6.12-9-386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 381kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by mlomker on 2005-11-13
> Have system freezes again, anybody else?


I'm afraid that you are not alone there, but I don't know the answer.  What model of card do you have?  Was your Breezy install a fresh load and fairly recent?  Freezes are usually hardware problems but if you had run fine under Hoary and hadn't changed anything then that'd be a different story...

Entry-level ATI & Nvidia cards are like $50.  If you just bought an X800+ then I can understand.

---

### Post by Cuppa-Chino on 2005-11-13
[QUOTE=mlomker]I'm afraid that you are not alone there, but I don't know the answer.  What model of card do you have?  Was your Breezy install a fresh load and fairly recent?  Freezes are usually hardware problems but if you had run fine under Hoary and hadn't changed anything then that'd be a different story...

Entry-level ATI & Nvidia cards are like $50.  If you just bought an X800+ then I can understand.[/QUOTE]

thanks mlomker, I do not want to be a nag-bag and I really appreciate your efforts.

Breezy was a fresh install, running only wireless card via Ndis and with fresh Firefox on top.... freezes are independent of whether I run the card as a 9500 or as a 9700 via ChipID force and card has never shown any odd behaviour under the Vole's own OS

well I have an AGP  radeon 9500/9700 model (board is labelled 9500 but it works and has worked without error for 2 years as a soft-modded 9700 under Windofs) - the AGP is part of crux, because if I upgrade now, then I will in a way delay upgrading the entire kit...
[LIST]
[*]if I sell mine 9700 on ebay that will net me ~50-60U$/t (maybe a bit more) in the UK
[*]getting something of at least equal power means a ~6600GT (although that is not much better) will cost me something like 150-180U$/t
[*]mind you that is replacing a card that cost me that in the first place, I paid only 150U$/t for my 9500 :arrow: which turned out to be a 9700)... 
[*]means 100+U$/t for no increase in performance which seems a lot...
[/LIST]
*incase you are wondering I would like to end up just running Ubuntu and playing the occaisional session in 3D in Linux*

---

### Post by rhipwell on 2005-11-13
Ok I'm totally lost on trying to get ATI drivers working. I've been unable to get fglrx to work following the how-to. my output is as follows: 

fglrxinfo outputs:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

The output of ldd /usr/bin/glxinfo is: 

linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7f1e000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7ea8000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e7e000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e5c000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d2e000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c6e000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c61000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c4f000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7c49000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c46000)
        libdrm.so.1 => /usr/lib/libdrm.so.1 (0xb7c3f000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b59000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b4e000)
        /lib/ld-linux.so.2 (0xb7f98000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b4a000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b46000)

ldd /usr/X11R6/bin/fglrxinfo outputs: 

        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e93000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7dd3000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7dc5000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c97000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7c75000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c63000)
        libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7c5e000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c5b000)
        libdrm.so.1 => /usr/lib/libdrm.so.1 (0xb7c53000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c50000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c4c000)
        /lib/ld-linux.so.2 (0xb7f0d000)

ls -l /usr/X11R6/lib/libGL.so.1* outputs: 

lrwxrwxrwx  1 root root 35 2005-11-10 21:11 /usr/X11R6/lib/libGL.so.1 -> /usr/lib/i686/mmx/cmov/libGL.so.1.2
lrwxrwxrwx  1 root root 35 2005-11-10 21:12 /usr/X11R6/lib/libGL.so.1.2 -> /usr/lib/i686/mmx/cmov/libGL.so.1.2

So far I've tried using 8.18.8 and 8.19.10 driver versions with no luck. Rebooting doesn't seem to address the issue either. 

My video card is a radion 9200se and I am running Breezy. 

Any ideas?  

Thanks 

-Robert

---

### Post by basfrank on 2005-11-13
Hi Forum,

I got the prprietary ati fglrx driver 8.18.08 to work. 3d also.:) 
Yesterday I tried the new 8.19.10.
The installation worked fine but there's no 3d support.:( 
Fglrxinfo says the mesa module has been taken not the ati one.
I have no idea what's wrong with it.
I posted my [install.log]("http://paste.ubuntuusers.de/427") and [URL="http://paste.ubuntuusers.de/428"]Xorg.0.log  
[/URL]
Can you help me?

---

### Post by Cufishing on 2005-11-13
Are you getting any errors during the apt-get install phase?
If so, you need to open your repositories up.

By chance did 'ctrl-alt-backspace' re-cycle you session after you finished the aticonfig?

What about errors during the compilation of the kernel driver?

---

### Post by rhipwell on 2005-11-13
[QUOTE=Cufishing]Are you getting any errors during the apt-get install phase?
If so, you need to open your repositories up.

By chance did 'ctrl-alt-backspace' re-cycle you session after you finished the aticonfig?

What about errors during the compilation of the kernel driver?[/QUOTE]

Regarding my issues - I received no errors during compilation, I rebooted after the install ( so killing control alt backspace is redundant ) and I also did not get any errors from apt. Thanks

---

### Post by mlomker on 2005-11-13
> well I have an AGP  radeon 9500/9700 model (board is labelled 9500 but it works and has worked without error for 2 years as a soft-modded 9700 under Windofs) - the AGP is part of crux, because if I upgrade now, then I will in a way delay upgrading the entire kit...

You might want to hit the rage3d.com board and see if they have some ideas.  I'm happy to write installation how-to's but there's not a lot that I can do if there's something wrong with the driver itself.

---

### Post by mlomker on 2005-11-13
[QUOTE=rhipwell]Ok I'm totally lost on trying to get ATI drivers working. [/QUOTE]

Look through /var/log/Xorg.0.log and **dmesg | grep fglrx** for errors.

---

### Post by mlomker on 2005-11-13
[QUOTE=basfrank]I posted my [install.log]("http://paste.ubuntuusers.de/427") and [URL="http://paste.ubuntuusers.de/428"]Xorg.0.log  
[/URL]Can you help me?[/QUOTE]

Please post a new thread with your question.  The fact that you have an installer.log means that you did not follow my how-to.

---

### Post by souled on 2005-11-13
I did a fresh install of Breezy, and tried this HOWTO, but it did not work. When I install the debs and restart X, the colors are all messed up and I don't get 3D acceleration. The colors go back to normal when I uninstall the deb files. Have a Radeon 9200, what's the problem? Before I reinstalled Breezy, I tried installing 8.16, 8.18, and 8.19 drivers with the same result. I had it working for a month and then all of a sudden it stopped working... I don't get it.

---

### Post by mlomker on 2005-11-14
[QUOTE=souled]I had it working for a month and then all of a sudden it stopped working... I don't get it.[/QUOTE]

You might want to start a new thread or look on the rage3d site.  The how-to is to get them installed...whether or not they work is another story.  The latest drivers don't allow my laptop to shut down, for example...I just get this lovely white/black checkboard pattern on my screen.  I might go back to the 8.18.8, myself, because I never use sleep/hibernation on my laptop and don't need the new feature.

---

### Post by Pettman on 2005-11-14
What is wrong when you get the mesa stuff? you know ```
somebody@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```
Is it that the mesa kernel module loads instead of the fglrx module?

---

### Post by mlomker on 2005-11-14
[QUOTE=Pettman]What is wrong when you get the mesa stuff? [/QUOTE]

That just means 'it isn't working.'  See post 266 for troubleshooting.

---

### Post by rhipwell on 2005-11-14
[QUOTE=mlomker]Look through /var/log/Xorg.0.log and **dmesg | grep fglrx** for errors.[/QUOTE]

dmesg has no errors, however Xorg.0.log shows the following (excluding modelines ): 
(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000007bc
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled

Thanks

---

### Post by mlomker on 2005-11-14
[QUOTE=rhipwell]
dmesg has no errors, 
[drm] failed to load kernel module "fglrx"
[/QUOTE]

You need to run it soon after booting or **cat /var/log/kern.log | grep fglrx** and figure out what was from the last bootup.

---

### Post by rhipwell on 2005-11-14
[QUOTE=mlomker]You need to run it soon after booting or **cat /var/log/kern.log | grep fglrx** and figure out what was from the last bootup.[/QUOTE]

I just rebooted, dmesg | grep fglrx has no output

cat /var/log/kern.log | grep fglrx shows no new entries ( last entry from nov 10th )
which reads as: 

 Nov 10 21:05:45 localhost kernel: [4294701.530000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 10 21:05:45 localhost kernel: [4294701.532000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
Nov 10 21:05:45 localhost kernel: [4294701.533000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
Nov 10 21:05:45 localhost kernel: [4294701.547000] [fglrx:firegl_unlock] *ERROR* Process 8911 using kernel context 0
Nov 10 21:13:29 localhost kernel: [4294701.372000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 10 21:13:29 localhost kernel: [4294701.374000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
Nov 10 21:13:29 localhost kernel: [4294701.374000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
Nov 10 21:13:29 localhost kernel: [4294701.388000] [fglrx:firegl_unlock] *ERROR* Process 8973 using kernel context 0


cat /var/log/Xorg.0.log | grep fglrx shows the following: 

(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000007bc
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled

---

### Post by vicus on 2005-11-15
Mlomker, cannot believe it. After i followed your howto regarding the new ATI driver, works like a charm, i get about 2000 fps in glxgears. I only tried Tuxracer and so, but it works, and fglrxinfo shows the correct info. Can't thank you enough.
I have a motherboard Gigabyte with Nforce2 and the video is Hercules Radeon 9600 256 MB, if anyone has problems with ATI and 3D in Ubuntu Breezy, just follow Mlomker instructions. It's on.

---

### Post by BLTicklemonster on 2005-11-15
I'm sorry, but I just don't get it. I've been to the site linked to for the ati drivers several times before, and gone to most of the links, and I don't see any drivers to download. What am I missing? I was under the impression that the link would take me to a download, not a page of links. 

I have two machines that accursedly have rage cards in them. I assume that 3d rage pro cards will work with the drivers alluded to (but not found) on the site linked to in the original how to?

Now for the clincher:

I hope to goodness that somoene in the Dapper development team pays attention to what is going on here. Apparently ATI and Ubuntu don't go together well, so something should be done about it. 

Obviously no one on the driver side of things is going to do it, or there would be a glow in the dark class 5 "here it is" link posted somewhere that you could click and either download a file, or find a page with actual downloads, not obscure links to other sites with cryptic babblings of superior intellects. 

And apparently there's not much that can be done from Ubuntu's side of things. BUT: if you notice when you install ubuntu, it does a dandy job of automagically getting your video card to come up. It would behoove Ubuntu's image to have that functionallity present in the event someone (me and 98 percent of every one who has an ati card trying ubuntu, apparently) gets to the point where x won't come up because the drivers/config file/operator/whatever is geeked. Perhaps a prompt at that point mentioning that if one were to type restore-video (or something) and press enter, it would go back and put the video up like it was before, and put a log file on the desktop wth all info pertaining to the problem listed in it for the user to mull over while they marvel at how freaking incredible Ubuntu is for putting such a nice freaking feature in their os. (if it can do it once, it can do it again. so why not make it do that when it finds that x won't start because of someone trying to get their 3d support for their ati card so it will look like it's running an nvidia, not a strobe light)


That is about as close to non ranting as I can get after the 4th reinstall of ubuntu on a raging idiot box. (Note to self, radeon's technical superiority I keep hearing about is a ruse to get you to not use the internet so that bandwidth can remain high. Never buy radeon again, stick with nvidia)


(Showing results 1 to 25 of 500 Search: Key Word(s): ati, drivers  )

---

### Post by Pettman on 2005-11-15
[QUOTE=mlomker]That just means 'it isn't working.'  See post 266 for troubleshooting.[/QUOTE]
the log file that you recomended taking a look in containde this (and a lot of other stuff)```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
The "dmesg | grep fglrx" does not give any output at all.

---

### Post by mlomker on 2005-11-15
[QUOTE=BLTicklemonster]I'm sorry, but I just don't get it. I've been to the site linked to for the ati drivers several times before, and gone to most of the links, and I don't see any drivers to download. [/QUOTE]

Their site uses SSL and I cannot directly link to the download page.  That really irks me.

Follow the link, click on Linux Drivers, click on Radeon 8500 series, click on the 8.19.10 driver, and finally click on the Download link for the ATI driver installer.

Oh, and everything about Ubuntu is done by volunteers (myself included), so unless you're going to do some programming work to help out then stop complaining.  You pay for Windows and then Microsoft charges for support...here you don't pay for anything.

---

### Post by mlomker on 2005-11-15
[QUOTE=rhipwell]
Nov 10 21:13:29 localhost kernel: [4294701.388000] [fglrx:firegl_unlock] *ERROR* Process 8973 using kernel context 0
Nov 10 21:05:45 localhost kernel: [4294701.533000] [fglrx] module loaded - fglrx 8.18.8 [Oct 25 2005] on minor 0
[/QUOTE]

That one has a lot of causes.  Did you install 8.18.8 or the latest version?

Make sure you only have one fglrx.ko on your system:

```

sudo updatedb
locate fglrx.ko

```

You'll find quite a few other posts on here regarding the firegl_unlock error.  Some people fixed it by reloading Ubuntu and others are unresolved.

---

### Post by mlomker on 2005-11-15
[QUOTE=Pettman]The "dmesg | grep fglrx" does not give any output at all.[/QUOTE]

You should try the search on post 279 as well.  The module isn't loading, so the module-assistant step may have failed.

---

### Post by BLTicklemonster on 2005-11-15
[QUOTE=mlomker] so unless you're going to do some programming work to help out then stop complaining.  You pay for Windows and then Microsoft charges for support...here you don't pay for anything.[/QUOTE]


I'll learn to levitate if it helps.

But either I will let Santa bring everyone here Nvidia cards or put Hoary on their machines (I seem to remember seeing people had no problems with ati on hoary) and take a pair of needle nose pliers to the ati cards. 


Thanks for your help.

---

### Post by BLTicklemonster on 2005-11-15
[QUOTE=Pettman]What is wrong when you get the mesa stuff? you know ```
somebody@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```
Is it that the mesa kernel module loads instead of the fglrx module?[/QUOTE]

I dont mean to be a bother, but if mesa stuff doesn't work, then why is it bundled with ubuntu? shouldn't t- never mind, I don't want to get anyone mad here. I'm sure that in a while this will all be settled down.

---

### Post by rhipwell on 2005-11-15
[QUOTE=mlomker]You should try the search on post 279 as well.  The module isn't loading, so the module-assistant step may have failed.[/QUOTE]

AHA! module assistant did fail! I received the following:

Target package file
/usr/src/fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb already
exists, not rebuilding!
Selecting previously deselected package fglrx-kernel-2.6.12-9-386.
(Reading database ... 110379 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-9-386 (from .../fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.12-9-386:
 fglrx-kernel-2.6.12-9-386 depends on xorg-driver-fglrx (= 8.18.8-1); however:
  Version of xorg-driver-fglrx on system is 8.19.10-1.
dpkg: error processing fglrx-kernel-2.6.12-9-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.12-9-386

I: Direct installation failed, trying to post-install the dependencies

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fglrx-kernel-2.6.12-9-386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 381kB disk space will be freed.
Do you want to continue [Y/n]?
I ran apt-get -f install and removed that package...I will update when I reboot. Thanks for the help!

**UPDATE**

Boo-urns - no luck with the reboot 

Xorg.0.log shows: 

(--) fglrx(0): Display dimensions: (320, 240) mm
(--) fglrx(0): DPI set to (101, 108)
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000007bb
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled


Thanks again

---

### Post by BLTicklemonster on 2005-11-15
Fresh install. No updates. I did this:

> **Remove old fglrx driver**

Remove Breezy's included drivers if they are installed:

```


sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

```

Reboot.

and now I'm looking at a real pretty blue screen with the good old Nvidia advertisement on it.

What am I supposed to do now?


*edit:

Answer, sudo nano dpkg-reconfigure xserver-xorg twice. Nice.

Also, one must be sure to have the correct [repositories](http://www.psychocats.net/linux/sources.php) and be sure to 
```

sudo apt-get install gcc-3.4
sudo apt-get install g++-3.4

```
before attemtping
```

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base

```
and do these in this order:
```

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base
sudo sh ./ati-driver-installer-8.19.10-i386.run --buildpkg Ubuntu/breezy
sudo dpkg -i xorg-driver-fglrx_8.19.10-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.19.10-1_i386.deb
sudo dpkg -i fglrx-control_8.19.10-1_i386.deb

```
Because the control didn't want to go until the driver-fglrs was in.

Now as I sit and write this, the machine is rebooting, and yep, I heard the Fred Flinstone stumble bongo sound, so it came up, now to fglrxinfo it and see if it took...

Bingo.


Thank you. Finally.

---

### Post by UrbanFallout on 2005-11-16
First off thanks for the how to and advice.

This applies to anyway with the AMD64 version of breezy installed.

Just wanted to give one last correction to the howto, which hould save someone a couple of hours.

The howto says you should use the version 8.18.8 rather than 8.19.10.
However the bundle for 8.18.8 is missing a few files. So you need to download both the 8.18.8-**i386** and 8.18.8-**x86_64** versions of this file.

Each of these files bundles a set of scripts as well as the actual drivers, so happily they may be unbundled and fixed.
So instead of running
sudo sh ./ati-driver-installer-8.19.10-x86_64.run --buildpkg Ubuntu/breezy
Try the code below.

```


sudo sh ./ati-driver-installer-8.18.8-i386.run --extract i386
sudo sh ./ati-driver-installer-8.18.8-x86_64.run --extract x86_64

sudo cp i386/packages/Ubuntu/debian/70fglrx x86_64/packages/Ubuntu/debian/70fglrx
sudo cp i386/packages/Ubuntu/debian/fireglcontrol.desktop x86_64/packages/Ubuntu/debian/fireglcontrol.desktop
sudo cp i386/packages/Ubuntu/debian/fireglcontrol.kdelnk x86_64/packages/Ubuntu/debian/fireglcontrol.kdelnk
sudo cp i386/packages/Ubuntu/module/postinst x86_64/packages/Ubuntu/module/postinst

cd x86_64
sudo sh packages/Ubuntu/ati-packager.sh --buildpkg breezy
cd ..
ls

```
You will now some .deb packages listed.

Continue installing these as per previous post.

Hope this helps
Nick

---

### Post by mlomker on 2005-11-16
[QUOTE=BLTicklemonster]I dont mean to be a bother, but if mesa stuff doesn't work[/QUOTE]

It's software 3D for cards that don't have a proper dri driver for hardware acceleration.  If you're okay with 300 fps then there's no need to install the fglrx driver.  The average business user that just surfs the web and types emails doesn't need hardware 3D.

---

### Post by mlomker on 2005-11-16
[QUOTE=rhipwell]Thanks again[/QUOTE]

You need to run **dmesg | grep fglrx** shortly after your failed start to find out what the problem is with the module loading....either that or look through /var/log/kern.log.  You also didn't post the output of the search command...do you have an fglrx.ko on your drive?  Hopefully there's only one and it's in the correct directory.

---

### Post by mlomker on 2005-11-16
[QUOTE=UrbanFallout]The howto says you should use the version 8.18.8 rather than 8.19.10.[/quote]

I did that for a while until I had time to test it.  I run 32-bit, so I need to set aside a couple hours to reload a couple of times and thoroughly test on 64-bit.  The 8.19.10 seems to work fine and I updated the how-to a day ago.

> However the bundle for 8.18.8 is missing a few files. 

That's fixed in 8.19.10.  It's difficult to keep the how-to's in synch when each version of the driver has a different problem. 

That particular problem came up in 8.18.6.  We had solved it in this thread but I never put it in the how-to because I had hoped that ATI would get the patch into their download sooner.

---

### Post by BLTicklemonster on 2005-11-16
I have it going on my son's now, but the graphics suck. Is there anything I can do? I notice an ATI think in applications, but it doesn't have anything useful in it.

the textures in UT are missing. all maps are almost like I made them in the editor and didn't put textures on them.

---

### Post by mlomker on 2005-11-16
> 
sudo apt-get install gcc-3.4


That's the first item listed on my apt-get line, so that would be redundant.

> 
sudo apt-get install g++-3.4


I don't have that installed/didn't need it.  Did you **apt-get update/upgrade** prior to following the how-to?  That wasn't clear from your post.  I always do a fresh load from CD and then update.  I test each of the how-to's four times on my machine (twice on 32-bit and twice on 64-bit) prior to posting them.  That can't account for hardware differences, but that's the best that I can do with what I've got.

I am glad that you got it going.  :cool:

---

### Post by mlomker on 2005-11-16
> the textures in UT are missing. all maps are almost like I made them in the editor and didn't put textures on them.

You'll want to check the gaming boards here or the [Rage3D]("http://www.rage3d.com/board") forum.  

I don't play games, myself, so testing with glxgears is as far as I go with it.

---

### Post by mlomker on 2005-11-16
[QUOTE=BLTicklemonster]Because the control didn't want to go until the driver-fglrs was in.
[/QUOTE]

I updated that.  That's a change that I meant to make the other day but forgot about it.  The packages will install fine but will generate an error message if installed out of order.

---

### Post by BLTicklemonster on 2005-11-16
[QUOTE=mlomker]That's the first item listed on my apt-get line, so that would be redundant.



I don't have that installed/didn't need it.  Did you **apt-get update/upgrade** prior to following the how-to?  That wasn't clear from your post.  I always do a fresh load from CD and then update.  I test each of the how-to's four times on my machine (twice on 32-bit and twice on 64-bit) prior to posting them.  That can't account for hardware differences, but that's the best that I can do with what I've got.

I am glad that you got it going.  :cool:[/QUOTE]

I hear you, but until I physically installed gcc, it I got errors on that first line.

Yes, updated, always before doing something new.

---

### Post by sociocolorado on 2005-11-17
i run the scripts apparently without problems, but after reboot the command "fglrxinfo" displays this:

```

@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

any idea?

PS: sorry, my english is ugly ;)

---

### Post by mlomker on 2005-11-17
> any idea?


Look for error messages in /var/log/kern.log and /var/log/Xorg.0.log.

---

### Post by yyagol on 2005-11-18
Well finaly i menage to install the fglrx on my machine
```
$ uname -a
Linux breezy 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
$ lspci|grep ati
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

```
what i did was :
```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
```
Then the only driver that did work for me was the old fglrx 8.8.25 with Hoary
and i did not get that bright screen
so i downloaded it from the [www.ati.com]("http://www.ati.com")
and did 
```
$ sudo alien fglrx_6_8_0-8.8.25-1.i386.rpm
$ sudo dpkg -i fglrx-6-8-0_8.8.25-2_i386.deb
$ sudo nano /etc/X11/xorg.conf
```
and change the "ati" with "fglrx" and then reboot
it worked now i got TV and i got good screen but when i try to
look for the module i found this :
```
$ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
$ glxinfo
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
~$ lsmod | grep fglrx
~$

```

i dont care for it couse its working
i could not belive it so i did another reboot
and bigo it is working...i dont know how but its a fact so as for me
as long as its working let ther be love..:D

---

### Post by mlomker on 2005-11-18
[QUOTE=yyagol]Well finaly i menage to install the fglrx on my machine
[/quote]

The 8.8.25 driver will not compile on Breezy, so I doubt that it is working properly.  TV-out does work with the standard ATI driver, so I suspect that is what you are running.  You'd have to look at the /var/log/Xorg.0.log to see what is being loaded.

---

### Post by sociocolorado on 2005-11-19
[QUOTE=mlomker]Look for error messages in /var/log/kern.log and /var/log/Xorg.0.log.[/QUOTE]

thanks...

i found the error below ( in the file /var/log/Xorg.0.log )

```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.18.8
(II) fglrx(0):     Date: Oct 25 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d37000 at 0xb7b49000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

other previous error in: "sudo module-assistant a-i fglrx"
```

Target package file
/usr/src/fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb already
exists, not rebuilding!
Selecting previously deselected package fglrx-kernel-2.6.12-9-386.
(Reading database ... 96036 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-9-386 (from .../fglrx-kernel-2.6.12-9-386_8.18.8-1+2.6.12-9.23_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.12-9-386:
 fglrx-kernel-2.6.12-9-386 depends on xorg-driver-fglrx (= 8.18.8-1); however:
  Version of xorg-driver-fglrx on system is 8.19.10-1.
dpkg: error processing fglrx-kernel-2.6.12-9-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.12-9-386

I: Direct installation failed, trying to post-install the dependencies

```

version 8.18.8???
why not 8.19.10??? :confused:

---

### Post by yyagol on 2005-11-19
This module is driving me crazy i just cant
make it to run properly.
by diging in to it i found out that this module need **glibc-2.2** or 2.4
when i tryed to install it with no X it says that i am runing a **glibc-2.1**
i try to look for **glibc-2.2** but could not get it enyware
any idea ?

---

### Post by rhipwell on 2005-11-19
Wahoo! Full reinstall of breezy, following the how-to worked! 

glxgears has 1232 FPS 
fgl_glxgears has 120 FPS 

Thanks a bunch Mlomker!

---

### Post by mlomker on 2005-11-19
[QUOTE=sociocolorado]version 8.18.8???[/QUOTE]

Which did you download?  Did you previously have 8.18.8 installed?  The error does indicate a mixture of files.  Perhaps you should remove the three packages and verify that the /usr/src/fglrx.tar.bz2 file is gone (that's what module-assistant compiles)...and then reinstall the DEBS again.

---

### Post by mlomker on 2005-11-19
[QUOTE=yyagol]i try to look for **glibc-2.2** but could not get it enyware
any idea ?[/QUOTE]

The package you're trying to install wasn't made for Ubuntu.  Ubuntu calls that package libc6 and it's at version 2.3.5.

---

### Post by brkl on 2005-11-19
So how do I do this when I'm trying to do a fresh install of Breezy, but the video drivers that come with the DVD don't seem to support my X800XL ( "(EE) Screen not found" or something like that)? I hear these new drivers should fix that. I get the exact same error with the 64-bit and 32-bit versions. 

I don't have an internet connection because it won't configure by DHCP (it's PPPoE). 

It refuses to install the packages you ask to install (won't find them). Actually I haven't tried this when installing from the 64-bit dvd (as opposed to the 32-bit cd).

I can download files to a hd and mount it, if that helps.

---

### Post by mlomker on 2005-11-19
[QUOTE=brkl]So how do I do this when I'm trying to do a fresh install of Breezy, but the video drivers that come with the DVD don't seem to support my X800XL ( "(EE) Screen not found" or something like that)? [/QUOTE]

That error usually is due to an incorrect xorg.conf file but I haven't heard of that happening on a fresh install.  Do you have a VGA controller on your system board that isn't disabled?  Otherwise, I'm not sure what that could be.

Have you tried **sudo dpkg-reconfigure xserver-xorg**?  The default driver should be ATI but you could try VESA.

You can download packages from [packages.ubuntu.com]("http://packages.ubuntu.com") and install them using **dpkg -i**.

---

### Post by brkl on 2005-11-19
Sorry, I think the correct error message is this:
(EE) No devices found

I had the same problem with the LiveCD and several other people seem to have it too. I'm going to try installing again now.

Specs:
AMD Athlon64 3200+
1gb ram
ATI X800XL 256mb

EDIT:
Ok, vesa works for now.

---

### Post by JimmyJazz on 2005-11-19
Okay I followed the guide and everthing went fine but when I restarted my computer the screen was flickering and distorted very bad.  I am using an ATI mobility 9000 on a HP zt3000 with a 1280 x 800 resolusion.  Please help!

---

### Post by yyagol on 2005-11-19
[QUOTE=mlomker]The package you're trying to install wasn't made for Ubuntu.  Ubuntu calls that package libc6 and it's at version 2.3.5.[/QUOTE]

well i found out that the libc6 is using glibc-2.3.5 on breezy and still
when i run the ati-installer script it says i'm using glibc2.1
mabye i need to try installing the package from [[COLOR="RoyalBlue"]the original[/COLOR]]("http://packages.ubuntu.com/breezy/base/libc6") to see 
if it change somthing ?

---

### Post by mlomker on 2005-11-20
[QUOTE=JimmyJazz]Okay I followed the guide and everthing went fine but when I restarted my computer the screen was flickering and distorted very bad.  I am using an ATI mobility 9000 on a HP zt3000 with a 1280 x 800 resolusion.  Please help![/QUOTE]

Review the /var/log/kern.log and Xorg.0.log files for errors.  The driver may be misdetecting the resolution or refresh rate, assuming you have a default /etc/X11/xorg.conf file.

---

### Post by mlomker on 2005-11-20
[QUOTE=yyagol]well i found out that the libc6 is using glibc-2.3.5 on breezy and still
when i run the ati-installer script it says i'm using glibc2.1
[/QUOTE]

Please start another thread for this--it's not related to this how-to.

---

### Post by JimmyJazz on 2005-11-20
[QUOTE=mlomker]Review the /var/log/kern.log and Xorg.0.log files for errors.  The driver may be misdetecting the resolution or refresh rate, assuming you have a default /etc/X11/xorg.conf file.[/QUOTE]

can you look at my log here:
[http://jimmyjazz.homeip.net:808/Xorg.0.log.old.txt](http://jimmyjazz.homeip.net:808/Xorg.0.log.old.txt)

I'm not really sure I see any errors but I may not be looking for the right things.

---

### Post by adam.tropics on 2005-11-20
Not sure if this will help anyone, but having setup fglrx a few times now (on toshiba laptop (radeon xpress200m)), I have found after installing, using the dpkg-reconfigure, rather than the ati setup for xorg.conf avoids all the headaches every time. Solves all the 'mesa' stuff, then manually edit for widescreen (1280*800). This has proved for me to be the most consistant method.

Thanks mlomker for your seemingly tireless efforts for everyone.

---

### Post by treanus on 2005-11-20
Hello All,

just used this howto to get X running on a fresh install of ubuntu that would not boot up X since the vga card is an ATI radeon X700.
The howto WORKS fine. X is now up and running.:D 

Have 1 problem though::( 
**Console switching (ctrl-alt-F1), log-out, or killing X server (ctrl-alt-backspace) results in a black screen**, i.e. my lcd screen goes into power-save mode (LCD says "no input signal"). Nothing works, I cannot get back to X with ctrl-alt-f7. Only thing I can do is to reboot with crtl-alt-del.

HELP please!

---

### Post by ElfLord on 2005-11-21
I have been reading about the driver problems for a while now, pretty much all this week.  I'm not a complete newbie to linux, I just switched from slackware for my new CPU. :D  I have the 64-bit kernel (2.6.12-9-amd64-generic) and have tried to use the ubuntu built-in fglrx and ati drivers as well as the drivers from ati's website.  So far, every one has worked and allowed me to use a GUI, however, I still have yet to get 3D acceleration.  Is this a problem with the drivers and something that I cannot fix?  So far, I have gotten every single error people have talked about on the forum and just seem to be jumping from one error to another.  The solution I'm sticking with is using the 8.19.10 drivers from ati's website.

current error:

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EBUSY"

if I disable the use of the InternalAGPGART, I get an

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"

and it just uses the MESA drivers in fglxinfo.

glxgears -printfps
1392 frames in 5.1 seconds = 272.326 FPS

I'm running an Athlon64 2.2Ghz with an AGP Radeon 9600 PRO.

Has anybody succesfully used this driver, with 3D support, on a 64-bit system?

Heh, and this is my first post, so HI! :D

---

### Post by mlomker on 2005-11-21
[QUOTE=JimmyJazz]I'm not really sure I see any errors but I may not be looking for the right things.[/QUOTE]

I don't see anything wrong there, either.  Have you tried a lower resolution to see if it'll work?  My only guess would be that your system BIOS isn't reporting the right refresh rate, etc.  Beyond making sure your system BIOS is the latest, I'm not sure what to do about that.

---

### Post by mlomker on 2005-11-21
[QUOTE=adam.tropics]I have found after installing, using the dpkg-reconfigure, rather than the ati setup for xorg.conf avoids all the headaches every time. [/QUOTE]

It must be unique to your machine.  Using that is actually not entirely safe with non-Ubuntu drivers because that process can overwrite the ATI files with Ubuntu ones...Septor stated that it does more than just create an xorg.conf file.  aticonfig has worked fine on many machines for me....there's also on [online fglrxconfig]("http://www.objorkum.com/scripts/fglrxconfig/") that works well.

---

### Post by mlomker on 2005-11-21
[QUOTE=treanus]**Console switching (ctrl-alt-F1), log-out, or killing X server (ctrl-alt-backspace) results in a black screen**, i.e. my lcd screen goes into power-save mode (LCD says "no input signal"). Nothing works, I cannot get back to X with ctrl-alt-f7. Only thing I can do is to reboot with crtl-alt-del.
[/QUOTE]

Please post in another thread for issues that aren't install-related.  There are known issues with trying to open a second instance of X, but I've never had a problem switching to a text console and then back again.

---

### Post by mlomker on 2005-11-21
[QUOTE=ElfLord]Has anybody succesfully used this driver, with 3D support, on a 64-bit system?
[/QUOTE]

Of course.  I couldn't write a how-to with references to 64-bit peculiarities if it didn't work on my machine.  If you've already downgraded the libdri.a file as in my how-to then you have another issue.  Please start a new thread for troubleshooting it.

You should also do a search on the Rage3d forum with your error(s).  The developers hang out on there...

---

### Post by ElfLord on 2005-11-21
[QUOTE=mlomker]Of course.  I couldn't write a how-to with references to 64-bit peculiarities if it didn't work on my machine.  If you've already downgraded the libdri.a file as in my how-to then you have another issue.  Please start a new thread for troubleshooting it.

You should also do a search on the Rage3d forum with your error(s).  The developers hang out on there...[/QUOTE]

Yea, I downgraded the libdri.a file, still DRI initialization failure.  Looks like I'm over to the Rage3d forum. thank you for all you have done, it really is invaluable.

---

### Post by pachequin on 2005-11-22
Hi everyone! after doing the howto I missed the wireless module, i didn't have the madwifi file located on volatile directory is it safe to install linux-restricted-modules after the application of the how to?

thanks for any help.

---

### Post by sterghios on 2005-11-22
Hey all, 

Please spare a moment for a highly confused linux noob trying to enable TVOUT on a X850XT PE. 

Of all the approaches mentioned across the forums, mlonker's is the least destructive with respect to the Xserver crashing. I initially attempted the installer approach, but fglrxconfing failed to detect my card by the end of the configuration. 

Having followed mlonker's howto to the letter, I got stuck at the last step, the aticonfig --initial, receiving an error saying that line 448 in xorg.conf contained "for", an unacceptable parameter. The peculair thing was that "for" was not found in that line, but in the preceding line, and commented, and therefore ought not to affect the code, correct?

Rebooting resolved the error, however, my fglrxinfo ouput remained the same, clearly not reading the card properly:

**fglrxinfo**
sterghios@elric:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


**This is my current xorg.conf:**
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SDM-HX73"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X850 XT PE (R481)"
	Monitor		"SDM-HX73"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

**The previous xorg.conf from the installer was:**
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"gb"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "ATI Technologies, Inc. Radeon X850 XT PE (R480)"
    VendorName  "ATI Technologies, Inc."
    BoardName   "Radeon X850 XT PE (R480)"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "X850"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "ati"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

    BusID       "PCI:0:10:0"

    VideoRam    256

    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "ati"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                             "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "clone" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "TVFormat"                   "PAL-I"     
    Option "TVStandard"                 "VIDEO"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
#    BusID "PCI:1:0:0"    # no device found at config time
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###




I am at a complete loss about what I am doing wrong - perhaps teh driver edition (8.19.10), I understand from the 300 or so previous posts that the howto was not written for it. Nonetheless, I find it a tad extreme that the installer cannot recognise the card. 

This all from a fresh installation of Breezy by the way.

Please provide some insight if you can.

All the best, 

Sterghios

---

### Post by Maverick911 on 2005-11-22
Wow!

29,098 views and 319 replies!! Guess I'm not the only one who wants their ATI graphics card to work properly.

My Problem:

I have an HP laptop with ATI mobility radeon 9200. I ran glxgears -printfps and got 1595 fps with the ATI driver that ubuntu installed.

I used automatix to download and install the fglrx driver. When I ran glxgears my fps had dropped to 150fps and the gears motion was jerky. I had to uninstall to get back to the 1595fps that I had before installing fglrx.

Can someone tell me what the problem was?

---

### Post by mlomker on 2005-11-22
[QUOTE=Maverick911]I had to uninstall to get back to the 1595fps that I had before installing fglrx.
[/QUOTE]

This is the help thread for my how-to (link is on the first post).  You should post about Automatix in their sub-board or start another thread for other issues.

I doubt you're going to do better than 1600 fps and I'd recommend leaving it alone.  Laptop video cards are a lot slower than desktops.  My Mobility 9700 Pro averages 2350 on glxgears.

---

### Post by BLTicklemonster on 2005-11-23
Okay, I took the nvidia out of this machine, dropped in the ati from the other machine, and tried installing it.

on reconfigure, chosing ati, xserver wouldn't boot, so I had to chose vesa, but once I did, the installation went without a glitch/hitch.

Except that I can only get an assumed fps of 900 or so in glxgears.


I lost my mouse settings (logitech) but I guess I can redo them no problem.

The motherboard my son is using in the other machine is not all that hot. The asus he was using with is xp1900 geeked out, and I had to put the xp1900 on a lesser board, so that was probably the problem all along. 

I'll drop the ubuntu drive back in it with the nvidia later and see if it gets going. Knowing that mobo, it probably won't, lol.

I think he's going to ask for a nicer mobo for Christmas anyway...

---

### Post by mlomker on 2005-11-23
[QUOTE=pachequin]Hi everyone! after doing the howto I missed the wireless module, i didn't have the madwifi file located on volatile directory is it safe to install linux-restricted-modules after the application of the how to?
[/QUOTE]

Momentarily, I guess, but if you reboot with it installed your video will stop working.

---

### Post by mlomker on 2005-11-23
[QUOTE=sterghios]Please spare a moment for a highly confused linux noob trying to enable TVOUT on a X850XT PE. 
[/QUOTE]

I've never been able to get TV out to work on my laptop, but that may just be my laptop.

For the xorg.conf you can try using the [online generator.]("http://www.objorkum.com/scripts/fglrxconfig/")

---

### Post by Goggy1 on 2005-11-24
I followed the How-To and I still can't get 3D acceleration, and games like Supertux are very choppy.

glxinfo
```
ricky@Snake:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
```

ldd /usr/bin/glxinfo
```
ricky@Snake:~$ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ee2000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e6c000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7e42000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7e20000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cf2000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7c32000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c25000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c13000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c0f000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7b29000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7b1e000)
        /lib/ld-linux.so.2 (0xb7f92000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7b1b000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7b17000)

```

xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

No errors from /var/log/Xorg.0.log

---

### Post by MoidPale on 2005-11-24
[QUOTE=Septor]Okay try doing this before running your app.
```

export LIBGL_DRIVERS_PATH=/usr/X11R6/lib/modules/dri:/usr/X11R6/lib32/modules/dri

```
][/QUOTE]

I tried with the new 8.19.10 driver with linux 2.6.12-10. I had to do the same hack in firegl_public.c to get rid of the mtrr-problem. Xorg says direct rendering is enabled. But when i run glxgears i still get:

libGL: XF86DRIGetClientDriverName: 8.19.10 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: undefined symbol: _glapi_get_proc_offset)
libGL: OpenDriver: trying /usr/X11R6/lib32/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib32/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib32/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.19.10 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib/modules/dri/fglrx_dri.so: undefined symbol: _glapi_get_proc_offset)
libGL: OpenDriver: trying /usr/X11R6/lib32/modules/dri/fglrx_dri.so
libGL error: dlopen /usr/X11R6/lib32/modules/dri/fglrx_dri.so failed (/usr/X11R6/lib32/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: fglrx_dri.so

fglrx_dri.so is located in /usr/X11R6/lib/modules/dri  so i really don't see the problem (except : undefined symbol: _glapi_get_proc_offset)

---

### Post by janp on 2005-11-24
Greetings !
I've used this how-to on my HP NX9110

I get the following errors:

1. When I run fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

The notebook have the Ati Mobility Radeon 9000IGP chipset.

Can anyone point me in any direction on how to get DRI enabled and working on this chipset.

Dearly appreciated

Jan

---

### Post by adam.tropics on 2005-11-24
Half on topic, half not! After using the how to, and having made the copy of madwifi thing, it's copied ok, and fglrx is fine, but it doesn't seem to find the madwifi driver again?? I've had this before, but can't remember how to fix it. BTW the reason for the repeat was the kernel update. Should i post this somewhere else or is it a common one??

---

### Post by mlomker on 2005-11-24
[QUOTE=Goggy1]No errors from /var/log/Xorg.0.log[/QUOTE]

There has to be an error in that file or kern.log, otherwise it isn't installed properly.  The other outputs that you provided aren't applicable anymore...the library issues are long resolved.

---

### Post by mlomker on 2005-11-24
[QUOTE=MoidPale]fglrx_dri.so is located in /usr/X11R6/lib/modules/dri  so i really don't see the problem (except : undefined symbol: _glapi_get_proc_offset)[/QUOTE]

I'm not sure how you went about installing the driver, but some approaches will make it so that only root has permissions to those files.  Try running **sudo glxgears -printfps** to see if you get a different result.

---

### Post by mlomker on 2005-11-24
[QUOTE=janp]Can anyone point me in any direction on how to get DRI enabled and working on this chipset.
[/QUOTE]

You need to look in /var/log/Xorg.0.log and kern.log for errors.  The how-to gets the drivers installed but that doesn't mean they'll work.  Start by doing some searches on whatever error you find.

---

### Post by mlomker on 2005-11-24
[QUOTE=adam.tropics]I've had this before, but can't remember how to fix it. BTW the reason for the repeat was the kernel update. Should i post this somewhere else or is it a common one??[/QUOTE]

Try **sudo depmod -a**

---

### Post by Goggy1 on 2005-11-24
[QUOTE=mlomker]There has to be an error in that file or kern.log, otherwise it isn't installed properly.  The other outputs that you provided aren't applicable anymore...the library issues are long resolved.[/QUOTE]

I see. I've provided the logs.  Any help is appreciated.

[http://www.uploadtemple.com/view.php/1132855142.txt](http://www.uploadtemple.com/view.php/1132855142.txt) kern.log
[http://www.uploadtemple.com/view.php/1132855167.txt](http://www.uploadtemple.com/view.php/1132855167.txt) Xorg.0.log

---

### Post by janp on 2005-11-24
[QUOTE=mlomker]You need to look in /var/log/Xorg.0.log and kern.log for errors.  The how-to gets the drivers installed but that doesn't mean they'll work.  Start by doing some searches on whatever error you find.[/QUOTE]

Cool! Thanks for the help so far. I did a cat on both files and grepped for fglrx. 

In Xorg.0.log I found the following that seems odd:

(--) fglrx(0): Chipset: "MOBILITY RADEON 9000/9100 IGP (RS300M 5835)" (Chipset =  0x5835)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x006b)
[COLOR="Red"](--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI[/COLOR]
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardwa re.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled

In kern.log I found the following that seems odd:

Nov 24 19:58:44 localhost kernel: [4294795.633000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Nov 24 19:58:44 localhost kernel: [4294795.633000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Nov 24 19:58:44 localhost kernel: [4294795.633000] [fglrx] Kernel AGP support doesn't provide agplock functionality.

Will do some searches on these, again any suggestions welcome.

Thanks
Jan

---

### Post by E-werd on 2005-11-24
```
ewerd@breezy:~$ sudo dpkg -i xorg-driver-fglrx_8.19.10-1_i386.deb (Reading database ... 172021 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.19.10-1 (using xorg-driver-fglrx_8.19.10-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on xserver-xorg (>= 6.99.99); however:
  Version of xserver-xorg on system is 6.8.2-77.
dpkg: error processing xorg-driver-fglrx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xorg-driver-fglrx

```

Erm... what do I do about this problem?

---

### Post by adam.tropics on 2005-11-24
> Try sudo depmod -a

Did that, no change and iwconfig still finds nothing:

adam@ubuntu:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

adam@ubuntu:~/Desktop$ iwconfig ath0
ath0      No such device

??

---

### Post by shadow07 on 2005-11-25
Ok.  For all of those that have had nothing but problems with installing ATI's crappy driver, I have found the perfect way.  For me atleast.

I would love to hear feedback from those that are having problems to try the following steps.  You will need to make sure you have the following packages already installed on your machine:

build-essential
linux-headers-386
g++3.4
module-assistant
```

A)  Extract the ati-installer files: ./ati-driver-installer-<version>-i386.run --extract
B)  Change into the installer directory: cd fglrx-install
C)  Build the packages: sudo ./ati-installer.sh <driver_version> --buildpkg Ubuntu/breezy
This should build the appropriate deb packages and place them in your home directory.
D)  cd ~
E)  sudo dpkg -i xorg-driver-fglrx_<driver_version>-1_i386.deb
F)  sudo dpkg -i  fglrx-kernel-source_<driver_version>-1_i386.deb
G)  sudo dpkg -i  fglrx-control_<driver_version>-1_i386.deb
H)  After installing the three packages above, you will need to run 'sudo module-assistant update'
I)  Then, 'sudo module-assistant a-i fglrx'
J)  Run fglrxconfig and build your x confing file
K)  Reboot
L)  Log in and run fglrxinfo, and you should not see Mesa, but ATI

```

I can tell you that I did this on a brand new install on an HP Compaqnc8000 laptop that has an ATI Radeon 9600 GPU.  I did install and run Automatix prior to installing the ATI driver.  I tried 3 times just running and installing the ATI Loki installer.  It would run just fine.  But, the ATI fglrx driver would never load.  I would continuously get the following logged in /var/log/Xorg.0.log:

```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8c80000 at 0xb7ad6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

---

### Post by Skoezie on 2005-11-25
Yesterday used the how-to to install the new drivers. What a difference!

The fps in Glxgears are 10 times higher then with the standard drivers. And America's Army & ET are finally running smoothly.

Great how-to! :cool:

---

### Post by MoidPale on 2005-11-25
Ok, i've got it working now. I did a complete new install of breezy, followed the How-To and got the "no mtrr's available" message in dmesg. I builded the kernel-module again but hacked the firegl_public.c-file by changing CONFIG_MTRR with XCONFIG_MTRR.  Rebooted and voila dri is working. So there was probably something wrong because i've tried to many different things to get it working. 


[QUOTE=mlomker]I'm not sure how you went about installing the driver, but some approaches will make it so that only root has permissions to those files.  Try running **sudo glxgears -printfps** to see if you get a different result.[/QUOTE]

---

### Post by mlomker on 2005-11-25
[QUOTE=Goggy1]I see. I've provided the logs.  Any help is appreciated.
[/QUOTE]

This error suggests that ATI doesn't support acceleration on your card:

```

(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"

```

If there's a workaround then the folks on the Rage3D forum would be your best bet.

---

### Post by mlomker on 2005-11-25
[QUOTE=janp]Cool! Thanks for the help so far. [/QUOTE]

Those errors are normal.  You'll need to examine the whole Xorg.0.log file.

---

### Post by mlomker on 2005-11-25
[QUOTE=MoidPale]CONFIG_MTRR with XCONFIG_MTRR. So there was probably something wrong because i've tried to many different things to get it working.[/QUOTE]

Yeah, it's a bug in the driver.  I've heard about this solution a couple of times already, so I assume that somebody must have filed a bug report by now.  MTRR errors are motherboard related, afaik.

---

### Post by mlomker on 2005-11-25
[QUOTE=shadow07]Ok.  For all of those that have had nothing but problems with installing ATI's crappy driver, I have found the perfect way.  For me atleast.[/quote]

The only significant difference between that and my how-to is how you edited the xorg.conf file.  I know from experience that fglrxconfig will not work properly for many systems.  My how-to has been tested by thousands of people at this point...

---

### Post by mlomker on 2005-11-25
[QUOTE=E-werd]
 xorg-driver-fglrx depends on xserver-xorg (>= 6.99.99); however:
  Version of xserver-xorg on system is 6.8.2-77.
[/QUOTE]

That's new...perhaps ATI changed the driver (again).  I'll test a fresh download.

---

### Post by Goggy1 on 2005-11-25
[QUOTE=mlomker]This error suggests that ATI doesn't support acceleration on your card:

```

(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"

```

If there's a workaround then the folks on the Rage3D forum would be your best bet.[/QUOTE]

Thanks, I'll do that. That is a weird error though because I could play UT2004 on this laptop on Windows and its ATI drivers.

---

### Post by shadow07 on 2005-11-25
[QUOTE=mlomker]The only significant difference between that and my how-to is how you edited the xorg.conf file.  I know from experience that fglrxconfig will not work properly for many systems.  My how-to has been tested by thousands of people at this point...[/QUOTE]

Well, I am one of those "thousands of people" you refer to and the How To did not work for me.

I know How To's do not work for everyone.  I just wanted to let people know about how I got it to work on my machine.  An, just so you know, I have tested this on 5 machines thus far.  And the only way I can get the ATI drivers to install consistantly is with the method I have posted.

---

### Post by mlomker on 2005-11-25
[QUOTE=Goggy1]That is a weird error though because I could play UT2004 on this laptop on Windows and its ATI drivers.[/QUOTE]

Linux is the Harry Potter of operating systems...they'll keep us locked under the stairwell until we're old enough to kick their butts.

---

### Post by mlomker on 2005-11-25
[QUOTE=shadow07]And the only way I can get the ATI drivers to install consistantly is with the method I have posted.[/QUOTE]

In my Hoary how-to's I used fglrxconfig as my recommended solution.  It resulted in tons of people complaining that it didn't work.  ATICONFIG is the solution that ATI is using going forward and it has worked on all of the machines that I support at work.  

If you've ever modified your xorg.conf file by hand then you're going to get different results, of course.  The how-to was written with a clean install (which is currently using the ATI driver) in mind.  I can't account for every possible configuration out there...

You're always welcome to write/post your own how-to (then you can deal with the support of it), but if you post in my thread and I disagree with your advice then you really can't expect me to leave it unchallenged.

---

### Post by mlomker on 2005-11-25
[QUOTE=adam.tropics]Did that, no change and iwconfig still finds nothing:
[/QUOTE]

You could always build it from source using this [how-to]("http://www.ubuntuforums.org/showthread.php?t=75451").

---

### Post by mlomker on 2005-11-25
[QUOTE=mlomker]That's new...perhaps ATI changed the driver (again).  I'll test a fresh download.[/QUOTE]

I retested the process and didn't experiece the dependency problem that you did.  What did you have installed prior to attempting  this install?  I wonder if it isn't the result of installing a previous DEB.

General advice:  Search for **fglrx** in Synaptic and write down all of the package names.  Ctrl-Alt-F2 to a console.  **sudo killall gdm** (or **kdm** if you use KDE).  Do an **sudo apt-get remove** for each package and then try your dpkg installs again.  **sudo reboot** when you are done.

---

### Post by sterghios on 2005-11-26
[QUOTE=mlomker]I've never been able to get TV out to work on my laptop, but that may just be my laptop.

For the xorg.conf you can try using the [online generator.]("http://www.objorkum.com/scripts/fglrxconfig/")[/QUOTE]


Thanks mlonker, do you think its safe to use this with the latest edition of the driver on ATi's site?

---

### Post by todo on 2005-11-26
Hmm,

I'm having fun trying to figure this out to.

I'm using an older version of kubuntu, 5.04.  I followed the info on this page and got to this step,

sudo module-assistant a-i fglrx.

The output was:
The source tarball could not be found!
Package fglrx-kernel-source not installed?
Running "m-a -f get fglrx-kernel-source" may help.

I checked the /usr/src directory and saw the tarball file, fglrx.tar.bz2 there.  Is there a way of specifying where to look for the source file?

---

### Post by almahtar on 2005-11-26
Mlonker, I'm never going to get used to your name.  Thanks for all you're doing.  Ubuntu is a rad OS and the userbase rules: so helpful and friendly.  I tried following the howto for both the old drivers (8.18.8) and the new (8.19.10).  3D accelleration is as of yet not working for me.  I exhausted all my information resources before bugging people with a public post.

System specs:
HP Pavillion zv6000 notebook.
Breezy AMD64, ATI Mobility Radeon XPress 200M

Xorg.0.log:
```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x001eb000 at 0x2aaaaab45000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```


locate fglrx.ko:
```

/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd
/lib/modules/fglrx/build_mod/fglrx.ko
/lib/modules/fglrx/fglrx.ko
/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/char/drm/fglrx.ko
/lib/modules/2.6.12-9-amd64-generic/misc/fglrx.ko
```


dmesg | grep fglrx
```
[fglrx] Maximum main memory to use for locked dma buffers: 423 MBytes.
[fglrx] module loaded - fglrx 8.19.10 [Nov  9 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 6912 using kernel context 0
```

kern.log just has the same thing (with different process numbers, of course) over and over

dmesg | grep AGP is uninformative
lspci shows that my hardware is recognized (thanks to that one guy's advice of "update-pciids")

glxinfo:
```
glxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```


If anyone has any ideas they are welcome and greatly appreciated.

---

### Post by shadow07 on 2005-11-27
[QUOTE=mlomker]In my Hoary how-to's I used fglrxconfig as my recommended solution.  It resulted in tons of people complaining that it didn't work.  ATICONFIG is the solution that ATI is using going forward and it has worked on all of the machines that I support at work.  

If you've ever modified your xorg.conf file by hand then you're going to get different results, of course.  The how-to was written with a clean install (which is currently using the ATI driver) in mind.  I can't account for every possible configuration out there...

You're always welcome to write/post your own how-to (then you can deal with the support of it), but if you post in my thread and I disagree with your advice then you really can't expect me to leave it unchallenged.[/QUOTE]

The problem was never with using fglrxconfig.  The problem was always with the driver compiling correctly and loading properly with the kernel.  I even posted the output of the log file showing the error.  I have seen this error NUMEROUS times.  Not just with my machines.  But, with others out in the world running not only Ubuntu/Kubuntu, but other Debain distros.

I'm not saying your HowTo is incorrect or wrong.  I am merely pointing out something I have used successfully AFTER trying your HowTo.

Come on.  I'm not trying to piss on your thread.  I am just trying to share the love.:cool:

---

### Post by shadow07 on 2005-11-27
@almahtar:

have you tried my method in this thread?  It's post #338 on page 34 of this thread.  I was having the very same issue you were having.  Specifically the part in the Xorg.0.log stating "(WW) fglrx(0): Kernel Module version does *not* match driver."  This problem was resolved for me with what I posted.

I am using the latest ATI drivers:  v8.19.10

---

### Post by almahtar on 2005-11-27
I think I'll give that a try.  I finally got a sacrificial partition set aside for experiments like that.  I'll probably be too busy all week to give it a shot though :-(

Tell you what, if it works I'll mail you a cookie.  Mmm... cookies.  No guarantee it'll arrive in edible state...

---

### Post by gui-guru on 2005-11-27
Hi!

Your "how to" make my card to work :) THANX !

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

```

my platform kubuntu, 2.6.12-10-amd64,..

but i have another problem. 
when i try to start composite in x.org

```

Section "Extensions"
   Option "Composite" "Enable"
EndSection

```

ane restart x, mesa again ?
when remove these lines from x.org and restart, again ATI 
:confused: 

Anybody have this problem ?

---

### Post by gui-guru on 2005-11-27
i;m found the answer :mad: 

At the moment, the driver will automatically disable direct rendering if you enable the Composite extension. This will be noted in your /var/log/Xorg.0.log file with a line like this:

   (II) fglrx(0): Composite extension enabled, disabling direct rendering

To get 3D acceleration back, simply comment or remove the line in your xorg.conf that loads the Composite extension

---

### Post by Cuppa-Chino on 2005-11-27
I get some really weird output in my Xorg.0.log file...
it apparently is trying to open a whole host of cards and fails... is this normal.. could be the reason for my system freezes?:( 


```
(II) fglrx(0): UMM Bus area:     0xd8701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xd8701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed

```
... it keeps counting cards until
```

drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card253
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8fbb000
(II) fglrx(0): [drm] mapped SAREA 0xf8fbb000 to 0xb7b6f000
(II) fglrx(0): [drm] framebuffer handle = 0xd8000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686-smp
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfbee0000
(II) fglrx(0): [agp] Mode=0x1f004a1b bridge: 0x8086/0x2570
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f004b1a
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f004312)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf9201000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
```

---

### Post by binks on 2005-11-27
ok i give up i have tried every differnt install inc the autogenerated xorg.conf 
and i still fail to get fglrx in info i still get mesa 
```


(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:15:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-206829
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 PRO (RV360 4152) found
(
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "single"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
(**) fglrx(0): Option "TVFormat" "NTSC-M"
(**) fglrx(0): Option "TVStandard" "VIDEO"
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9600 PRO (RV360 4152)" (Chipset = 0x4152)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0xc002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfe9f0000
(--) fglrx(0): ROM-BIOS at 0xfe9c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: TEO  Model: 9086  Serial#: 0
(II) fglrx(0): Year: 2004  Week: 17
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37  vert.: 28
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.324   greenX: 0.275 greenY: 0.593
(II) fglrx(0): blueX: 0.143 blueY: 0.065   whiteX: 0.280 whiteY: 0.311
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 202.5 MHz   Image Size:  350 x 260 mm
(II) fglrx(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 95 kHz, PixClock max 240 MHz
(II) fglrx(0): Monitor name: RELISYS TE988
(II) fglrx(0): Serial No: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 1
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 36 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 +hsync
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.19  1024 1088 1200 1376  768 769 772 809
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz
(II) fglrx(0): Modeline "800x600"   29.61  800 816 896 992  600 601 604 635 +hsync
(**) fglrx(0):  Default mode "800x600": 84.0 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"   83.95  800 856 944 1088  600 601 604 643
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"   72.85  640 680 752 864  480 481 484 527
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449 -hsync -vsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525 -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416 -hsync
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497 -hsync
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  600 601 602 625 -hsync
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  600 601 605 742 -hsync
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  480 481 482 501 -hsync
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  480 491 493 525 -hsync
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  400 406 407 417 -hsync -vsync
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  400 457 459 524 -hsync -vsync

(--) fglrx(0): Display dimensions: (370, 280) mm
(--) fglrx(0): DPI set to (70, 69)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.16.20
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): cpuSpeedMHz: 0x00000aef
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: yes
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	(II) fglrx(0): UMM Bus area:     0xe0501000 (size=0x07aff000)
(II) fglrx(0): UMM area:     0xe0501000 (size=0x07aff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit

drmOpenDevice: node name is /dev/dri/card93
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card94
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card95
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card96

d
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card254
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8d26000
(II) fglrx(0): [drm] mapped SAREA 0xf8d26000 to 0xb7b53000
(II) fglrx(0): [drm] framebuffer handle = 0xe0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfe9f0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EBUSY"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d26000 at 0xb7b53000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(WW) fglrx(0): Failed to set up write-combining range (0xe0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 7419
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "Protocol" "ImPS/2"
(**) Mouse: Device: "/dev/input/mice"
(**) Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Mouse: ZAxisMapping: buttons 4 and 5
(**) Mouse: Buttons: 5
(**) Option "CoreKeyboard"
(**) Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Keyboard: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse" (type: MOUSE)
(II) Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by mlomker on 2005-11-27
[QUOTE=sterghios]Thanks mlonker, do you think its safe to use this with the latest edition of the driver on ATi's site?[/QUOTE]

It worked the last time that I tried it.  You can always save a copy of your current config.

---

### Post by mlomker on 2005-11-27
[QUOTE=todo]I'm using an older version of kubuntu, 5.04.  I followed the info on this page and got to this step,
[/QUOTE]

No, that's where it should be. You can try **man module-assistant** for the options.

I have a [how-to ]("http://www.ubuntuforums.org/showthread.php?t=65276")for the older 8.16.20 drivers on Hoary.

---

### Post by mlomker on 2005-11-27
[QUOTE=almahtar]If anyone has any ideas they are welcome and greatly appreciated.[/QUOTE]

```

/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/char/drm/fglrx.ko

```

It looks like you didn't remove the 8.16.20 driver completely because this file should not be there.  Did you remove all of the old packages prior to installation of this new driver?

Try deleting the file, run **sudo depmod -a**, and reboot to see if the same problem occurs.

---

### Post by mlomker on 2005-11-27
[QUOTE=shadow07]The problem was always with the driver compiling correctly and loading properly with the kernel.  I even posted the output of the log file showing the error.  I have seen this error NUMEROUS times. [/quote]

I didn't see anything in your posting that would alter compiling behavior.  Perhaps you could point it out to me.  GCC, headers, and module-assistant are the only things required to compile the kernel modules...afaik.  **module-assistant prepare** downloads the headers.

I couldn't find your post with the output...unfortunately there's no good way on this board to search within a thread.

---

### Post by mlomker on 2005-11-27
[QUOTE=Cuppa-Chino]I get some really weird output in my Xorg.0.log file...
it apparently is trying to open a whole host of cards and fails... is this normal.. could be the reason for my system freezes?:( 
[/QUOTE]

No, that's normal from 8.18.8 onward.

---

### Post by binks on 2005-11-27
i have just tried to make a deb package from the ati installer and i get this error ```
/tmp/fglrx ~/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.19.10-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
	cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
fi
for i in preinst postinst prerm postrm ; do \
  if [ -f /tmp/fglrx/debian/driver.$i ]; then \
    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" /tmp/fglrx/debian/driver.$i > \
      /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
  fi; \
done
dh_testdir
dh_testdir
 fakeroot debian/rules binary
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found
~/fglrx-install
[Error] Generate Package - error generating package : Ubuntu/5.10

```
if anyone could point me i would be so thankfull
binks

---

### Post by Robocoastie on 2005-11-27
the ati-installer.xxx.run installer generates .deb packages for you. The step-by step instructions this thread is about explain how to do that.

I've found so far that the most common reason for the steps not working is because some of the packages the step-by-step refers to download can only be downloaded if the "universe and multiverse" repositories are enabled. In fact perhaps the how-to should be modified to make that clear that the first step you need to do is go enable those. If after installing Ubuntu you can't get to X in the first place then use vi to edit your /etc/X11/xorg.conf file to change the driver to vesa then startx and enable those repositories. Then you can proceed with the steps.

---

### Post by veloct on 2005-11-28
**[COLOR=red]mlomker:[/COLOR]** So there is no gain in performance in comparison with the 8.16.20 drivers? I'm just wondering if I should upgrade to 8.19.10 although the 8.16.20 drivers are working fine with my Radeon 9550 card. Thanks

---

### Post by binks on 2005-11-28
ok so i followed the howto with this thread and everything goes fine untill fglrxinfo still shows mesa
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux x1-6-00-50-ba-be-84-ab 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 18:50:27 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Server Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "ATI Graphics Adapter"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(==) FontPath set to "/usr/share/X11/fonts/misc"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80f2 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00
(cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AR [Radeon 9600] rev 0, Mem @ 0xe0000000/28, 0xfe9f0000/16, I/O @ 0xc000/8, BIOS @ 0xfe9c0000/17
(--) PCI: (1:0:1) ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) rev 0, Mem @ 0xd0000000/28, 0xfe9e0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.19.10
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.19g1                           
(II) ATI Proprietary Linux Driver Build Date: Nov  9 2005 17:51:16
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.19.1-driver-lnx-226030
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 PRO (RV360 4152) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[6] -1	0	0xfeaff400 - 0xfeaff5ff (0x200) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[11] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[12] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[13] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[14] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[15] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[16] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[19] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[26] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[27] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[29] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[33] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[34] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[35] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[37] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8213828
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[6] -1	0	0xfeaff400 - 0xfeaff5ff (0x200) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[11] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[12] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[13] -1	0	0x40000000 - 0x400003ff (0x400) MX[B]
	[14] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[15] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[16] -1	0	0xfe9e0000 - 0xfe9effff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfe9c0000 - 0xfe9dffff (0x20000) MX[B](B)
	[19] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[20] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[27] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[28] -1	0	0x0000d880 - 0x0000d8ff (0x80) IX[B]
	[29] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[30] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[31] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[32] -1	0	0x0000ee80 - 0x0000eebf (0x40) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[34] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[36] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[37] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[38] -1	0	0x0000ef20 - 0x0000ef3f (0x20) IX[B]
	[39] -1	0	0x0000ef00 - 0x0000ef1f (0x20) IX[B]
	[40] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "(null)"
(**) fglrx(0): Option "HSync2" "unspecified"
(**) fglrx(0): Option "VRefresh2" "unspecified"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "no"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON 9600 PRO (RV360 4152)" (Chipset = 0x4152)
(--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0xc002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfe9f0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V350
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/X11R6/lib/modules/linux/libdrm.a
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: TEO  Model: 9086  Serial#: 0
(II) fglrx(0): Year: 2004  Week: 17
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37  vert.: 28
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.638 redY: 0.324   greenX: 0.275 greenY: 0.593
(II) fglrx(0): blueX: 0.143 blueY: 0.065   whiteX: 0.280 whiteY: 0.311
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #1: hsize: 1024  vsize 768  refresh: 85  vid: 22881


(II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 202.5 MHz   Image Size:  350 x 260 mm
(II) fglrx(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) fglrx(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 95 kHz, PixClock max 240 MHz
(II) fglrx(0): Monitor name: RELISYS TE988
(II) fglrx(0): Serial No: 0
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 500/297MHz @ 50Hz [enable load balancing]
(**) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 47 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814 +hsync
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.19  1024 1088 1200 1376  768 769 772 809 +hsync
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (370, 280) mm
(--) fglrx(0): DPI set to (87, 92)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.19.10
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x00000aef
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: yes
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:

(II) fglrx(0): UMM Bus area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit

(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8da1000
(II) fglrx(0): [drm] mapped SAREA 0xf8da1000 to 0xb7aa1000
(II) fglrx(0): [drm] framebuffer handle = 0xe0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-9-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfe9f0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8da1000 at 0xb7aa1000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "Protocol" "ImPS/2"
(**) Mouse1: Device: "/dev/input/mice"
(**) Mouse1: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Mouse1: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Mouse1: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Mouse1: ZAxisMapping: buttons 4 and 5
(**) Mouse1: Buttons: 5
(**) Option "CoreKeyboard"
(**) Keyboard1: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard1: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xfree86"
(**) Keyboard1: XkbRules: "xfree86"
(**) Option "XkbModel" "pc105"
(**) Keyboard1: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Keyboard1: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Keyboard1: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard1" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse1" (type: MOUSE)
(II) Mouse1: ps2EnableDataReporting: succeeded

```

---

### Post by binks on 2005-11-28
still getting errors please someone 

```
II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-9-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfe9f0000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8da1000 at 0xb7aa1000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
(**) Option "dpms"
```

```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 18:50:27 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Server Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "ATI Graphics Adapter"
(**) |-->Input Device "Mouse1"
(**) |-->Input Device "Keyboard1"
(==) FontPath set to "/usr/share/X11/fonts/misc"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7
```

```
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.19.10
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.19g1                           
(II) ATI Proprietary Linux Driver Build Date: Nov  9 2005 17:51:16
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.19.1-driver-lnx-226030
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset RADEON 9600 PRO (RV360 4152) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[6] -1	0	0xfeaff400 - 0xfeaff5ff (0x200) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeac0000 - 0xfeadffff (0x20000) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
```

---

### Post by dezier on 2005-11-28
If i have understand it correctly this driver, contrary to the driver in the Ubuntu repository, supports Xinerama? I have tried to find relevant information about this, and sure i found information (to much!), but I need to know if others have got Xinerama working with these drivers. Would really like to know if it's worth installing this driver (which is, atleast for me, a risktaking as it works OK, although not perfect, as it is now).

---

### Post by mlomker on 2005-11-28
[QUOTE=dezier]If i have understand it correctly this driver, contrary to the driver in the Ubuntu repository, supports Xinerama?[/QUOTE]

If that is allowing more than one display then the Breezy driver does provide it.  If you have any questions then look at the FAQ's on ATI's website.  The repo versions are nothing more than packaged versions of the ATI driver...in other words, Ubuntu isn't adding or removing any functionality.

---

### Post by mlomker on 2005-11-28
[QUOTE=binks]fakeroot: command not found
[/QUOTE]

Make certain that the **fakeroot** package is installed.  You can use Synaptic or **sudo apt-get install fakeroot**

---

### Post by mlomker on 2005-11-28
[QUOTE=Robocoastie]because some of the packages the step-by-step refers to download can only be downloaded if the "universe and multiverse" repositories are enabled. In fact perhaps the how-to should be modified to make that clear that the first step you need to do is go enable those. If after installing Ubuntu you can't get to X in the first place then use vi to edit your /etc/X11/xorg.conf file to change the driver to vesa then startx and enable those repositories. Then you can proceed with the steps.[/QUOTE]

Someone mentioned to me a week ago that **module-assistant** was in Universe and I added that to the how-to.  I suppose I *could* put it in bold or link to another how-to regarding sources, but I opted to include a link to my own sources.list file in order to save some time.

I'm open to suggestions on that, but I'm not inclined to recreate other people's how-to's in my own....this isn't a how-to about apt repositories.

---

### Post by mlomker on 2005-11-28
[QUOTE=binks]
```

xf86_EINVAL

```[/QUOTE]

You'll probably also find an MTRR error in /var/log/kern.log.  The problem is BIOS/motherboard related.  You can look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=70173") and find more about it on the [Rage3D forum]("http://www.rage3d.com/board/forumdisplay.php?f=61").

---

### Post by mlomker on 2005-11-28
[QUOTE=veloct]I'm just wondering if I should upgrade to 8.19.10 although the 8.16.20 drivers are working fine with my Radeon 9550 card. Thanks[/QUOTE]

I wouldn't.  The new drivers just have a new set of problems.

---

### Post by dezier on 2005-11-28
[QUOTE=mlomker]If that is allowing more than one display then the Breezy driver does provide it.  If you have any questions then look at the FAQ's on ATI's website.  The repo versions are nothing more than packaged versions of the ATI driver...in other words, Ubuntu isn't adding or removing any functionality.[/QUOTE]

Yes, i forgot to mention, I use Xinerama now with the Breezy drivers. But I have also tested the drivers in the repository, and i noticed better 2d performance (have problem with xorg using much cpu, described here [http://ubuntuforums.org/showthread.php?t=18197)](http://ubuntuforums.org/showthread.php?t=18197)). The driver in the repository does support dual screens to some extent though, but it don't allow you use two drivers and move windows between the screens. Eh, its hard to explain, but i'm sure my dual screen fellows know what i'm talking about. (Simply it's not good enough.) I will have a look in the FAQ. Thanks.

Edit: Perhaps i wasn't clear enough. The reason Xinerama isn't supported by the repo driver is that it's an older version of the driver. Xinerama support came with version 8.18.10 or something like that. (Now i just have to figure out how to get Xinerama work, but atleast i know that it should be theoretical possible to get it up and running.)

Edit 2: I figured out how to get it work similiar to Xinerama. Wasn't hard, just issued $ sudo aticonfig --dtop=horizontal --overlay-on=1 . With this option windows will maximize to whatever screen they are on (i have heard that this shouldn't be the case when using ATI:s Big Desktop option, but they seem to have made some improvements). This setup is NOT Xinerama, so if you try it out, it may be so you don't get some features provided by it. It works fine for me though, so i'm satisfied.

---

### Post by Inspector Hector on 2005-11-29
There is a small inconsistency in the howto.
The ati-installer creates the packages in /tmp. So these lines
```

sudo dpkg -i xorg-driver-fglrx_8.19.10-1_i386.deb
sudo dpkg -i fglrx-control_8.19.10-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.19.10-1_i386.deb

```
should look like this (not necessary if you assume download path is /tmp of course)
```

sudo dpkg -i /tmp/xorg-driver-fglrx_8.19.10-1_i386.deb
sudo dpkg -i /tmp/fglrx-control_8.19.10-1_i386.deb
sudo dpkg -i /tmp/fglrx-kernel-source_8.19.10-1_i386.deb

```

By the way, you could also add a line like this, to make it even more easy to use your instructions.
```

wget -c https://a248.e.akamai.net/f/674/9206/0/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.19.10-i386.run

```

Hope this is valid and usable - i am just a user. And thanks for the guide.

---

### Post by binks on 2005-11-29
mlomker you fixed my problem but it wasnt with installing fakeroot id dont that subsequently it was actually the mtrr fault 

:D :D :D :D :D  big thanks cheers im now happy (ok for a while im normally grumpy:eek: )

---

### Post by mlomker on 2005-11-29
[QUOTE=Inspector Hector]There is a small inconsistency in the howto.
The ati-installer creates the packages in /tmp. 
[/quote]

It never has for me.  The DEBS are created in the current directory:

```

Generating package: Ubuntu/breezy
/tmp/fglrx ~/test/fglrx-install
Package /home/mlomker/test/xorg-driver-fglrx_8.19.10-1_i386.deb has been successfully generated
Package /home/mlomker/test/xorg-driver-fglrx-dev_8.19.10-1_i386.deb has been successfully generated
Package /home/mlomker/test/fglrx-kernel-source_8.19.10-1_i386.deb has been successfully generated
Package /home/mlomker/test/fglrx-control_8.19.10-1_i386.deb has been successfully generated
Package /home/mlomker/test/fglrx-sources_8.19.10-1_i386.deb has been successfully generated
~/test/fglrx-install
Removing temporary directory: fglrx-install
mlomker@mlomkernote:~/test$ ls
ati-driver-installer-8.19.10-i386.run
fglrx-control_8.19.10-1_i386.deb
fglrx-installer_8.19.10-1_i386.changes
fglrx-kernel-source_8.19.10-1_i386.deb
fglrx-sources_8.19.10-1_i386.deb
xorg-driver-fglrx_8.19.10-1_i386.deb
xorg-driver-fglrx-dev_8.19.10-1_i386.deb
mlomker@mlomkernote:~/test$

```

> 
```

wget -c https://a248.e.akamai.net/f/674/9206/0/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.19.10-i386.run

```


Nope, that can't be done.  Try it from a box other than your own once.  The fact that it is **https** means that the certificate is unique to your connection.  I spent hours trying to find a workaround and there isn't one.  ATI did that on purpose to make linking impossible.

Thanks for your comments, though.  I do try to keep the how-to accurate and the community helps to make that happen.

---

### Post by petri on 2005-11-30
My .debs are created in the current directory. In a .tmp and then they disappear while "Removing temporary directory: fglrx-install" . 
Can't find the .debs nowhere on the hd??? :)

---

### Post by mlomker on 2005-11-30
[QUOTE=petri]Can't find the .debs nowhere on the hd??? :)[/QUOTE]

You should build them again and pay attention to the output.  As you can see in post 381, it provides the full path to the file when it creates it.  My assumption would be that they failed to build and that's why they aren't there.

---

### Post by arpunk on 2005-11-30
What about putting the .debs somewhere online? wouldnt be easier that way?. Ive tried to build the drivers, 15 times in a row, i installed gcc-4.0 before 3.4, i thought i could simply *export CC=gcc-3.4* and that would work alright, but i get a total system freeze when i boot up the box again (when it should display gdm).

Funny thing is the debs and all generate correctly and i can even see that fglrx.ko is compiled with gcc-3.4 according to modinfo. So thats why it would be very helpful if someone puts **working** drivers for fglrx somewhere online.

---

### Post by mlomker on 2005-12-01
[QUOTE=arpunk]Ive tried to build the drivers, 15 times in a row, i installed gcc-4.0 before 3.4, i thought i could simply *export CC=gcc-3.4* and that would work alright, but i get a total system freeze when i boot up the box again (when it should display gdm).[/quote]

If you can't Ctrl-Alt-F2 to a terminal then building the driver is not the problem--hard freezes are hardware issues.  If you can get to a terminal then the log files should provide some details.

You don't have to make the DEBS to install the driver--you can just **sudo ./ati-whatever.sh** and run it directly.  That's what ATI suggests that you do.  My how-to builds the DEBS because it's easier to see when errors occur than with their approach.

I've tried hosting the DEBS before but it's too much hassle.  ATI updates the driver regularly and few people have adequate bandwidth to host the files.  Having a couple thousand Ubuntu users download 10 MB of files over your link costs real money (or totally ties it up with a slow link).

---

### Post by hedone on 2005-12-01
Ok now this one might be stupid... but anyway... 

In this ati howto there is 
**# sudo apt-get remove linux-restricted-modules-$(uname -r)**
and than installation gets src that should be right... 

in my case I use 686 kernel for P4 3,2 HT (smp runs to slow as u know), but installation gets 386 srces... so my kernel modul is for 386 kernel or what???

is that my problem with **ati radeon 9000 igp**?????

---

### Post by Inspector Hector on 2005-12-01
Hm, again, it's only in /tmp.

```

mkdir test
cd test
~/test$ mv ../ati-driver-installer-8.19.10-i386.run .

~/test$ sudo sh ./ati-driver-installer-8.19.10-i386.run --buildpkg Ubuntu/breezy
Password:
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.19.10....................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/test/fglrx-install
~/test/fglrx-install
Removing temporary directory: fglrx-install

~/test$ sudo dpkg -i xorg-driver-fglrx_8.19.10-1_i386.deb
dpkg: Fehler beim Bearbeiten von xorg-driver-fglrx_8.19.10-1_i386.deb (--install):
 kein Zugriff auf das Archiv: Datei oder Verzeichnis nicht gefunden
Fehler traten auf beim Bearbeiten von:
 xorg-driver-fglrx_8.19.10-1_i386.deb

~/test$ ls -l
-rw-r--r--  1 max  max  63744416 2005-11-29 21:25 ati-driver-installer-8.19.10-i386.run
-rw-r--r--  1 root root     1311 2005-12-01 20:48 fglrx-installer_8.19.10-1_i386.changes

```

The timestamp is correct.

```

max@grim:~/test$ find / -name xorg-driver-fglrx_8.19.10-1_i386.deb
/tmp/xorg-driver-fglrx_8.19.10-1_i386.deb

~/test$ ls -l /tmp
-rw-r--r--  1 root root 6242678 2005-12-01 20:48 xorg-driver-fglrx_8.19.10-1_i386.deb

```

Well, i have no idea. Anyway, it worked for me, thanks again. 
Oh and sorry about the wget thing. Could have been avoided by testing.

---

### Post by huckem on 2005-12-02
mlomker-
Just a note to say: THANK YOU!  I have been trying to get my Radeon 9500 Pro to produce 3D accelerated graphics in ANY form of Linux for about a year.  Thanks to you and your how-to (yeah, everything worked perfectly after following the how-to) I now have been running Unreal Tournament at a higher FPS than my XP machine which is a dual core AMDx2 3800+ with a GeForce 6600 256MB card.....How this is possible with my setup I dont know, but thats the magic of Linux.   Anyhow, thank you again for such a helpful and successful how-to, and to all those ppl out there still trying----DON'T GIVE UP! the feeling of victory is sweet.  This mlomker person can help!  

-peace

---

### Post by mlomker on 2005-12-02
[QUOTE=hedone]is that my problem with **ati radeon 9000 igp**?????[/QUOTE]

I don't understand what you are asking.  That command removes the restricted-modules package for the currently running kernel.  The module-assistant command then builds the module for the currently running kernel.

---

### Post by maser on 2005-12-02
I could install the driver and I can play games now. Unfortunately it doesn't work well with my 1600x1200 monitor that I connected via DVI. In 1600x1200 mode, the monitor shows "no signal", and when I connect via VGA, it doesn't look too good. It works in 1024*768 mode (for both). 
I've got a Radeon 9800 Pro.

Can anybody help me with this?

Thanks
maser

---

### Post by mlomker on 2005-12-02
[QUOTE=maser]Can anybody help me with this?
[/QUOTE]

Please start another thread.  I'd also recommend the Rage3D forum....nothing but ATI users on there, so your odds are better on an answer.

---

### Post by steviecee on 2005-12-03
Thanks mlomker for starting an obviously very popular thread.

I am a newbie and used to running WindowsXP but got tired of its slowness and vulnerability with regard to security.

I have an ASUS Dual head graphics card which is compatible with ATI 9200 drivers and under Windows I liked the functionality of the windows ATI drivers - running in dual head mode, a 19" flat screen LCD and to the right, a 15" crt.

I was aware of the fglrx driver but being a newbie I was stuggling with its installation.

Then I came across this thread and hey presto it worked.  But......I could see that apparently, in order to configure my two monitors to work properly I would have to manually edit my XORG.CONF.

A couple of attempts at this failed and resulted in booting into command prompt only.  From this position I quickly learnt how to rename and copy my XORGBACKUP.CONF to the correct location but I was still no further forward.

I thought I'd do a bit of digging around the internet and did a search on fglrx.

EUREKA!!! ----- I found **fglrxconfig** an interactive command that generates a new XORG.CONF by asking a series of questions about your configuration and requirements.

I ran this in terminal and after a few attempts have got my set up running with dual screens successfully.  The only down side is I cannot find a way of moving windows between screens.

I could describe exactly which options I chose but as people have different configurations and requirements I think its best to experiment.  BUT DO NOT FORGET TO MAKE A BACKUP OF XORG.CONFIG.

Reproduced below is the Dual Screen Configuration stage of the process:

[COLOR="Blue"]FireGL Screen Layout
==============================================================================

------------------------------------------------------------------------------
| Maximum resolution for OpenGL operation                                    |
|                                                                            |
| - R200 chip family (Radeon 8500-9100 Pro, FireGL 8700/8800/E1):            |
|       2048x2048                                                            |
| - R300 chip family (Radeon 9500-9700 Pro, FireGL T2/Z1/X1/X2):             |
|       2560x2560                                                            |
------------------------------------------------------------------------------

Do you want to configure dual monitor support (y/n)? [n] y

Choose configuration from the list below

 1.  Single Head   (1 screen, second dark)
 2.  Mirror Mode   (2 screens - same content, identical refresh rate/resolution) 3.  Clone Mode    (2 screens - same content, allows for different refresh rates/resolutions)
 4.  Big Desktop   (2 screens - one framebuffer)
 5.  Dual Head     (2 screens - two drivers)

Enter the number for your configuration: [1][/COLOR]

I chose the Dual Head option but your requirements may be different.

I guess the upshot of this is that I feel unless you are very familiar with how XORG.CONF works, its dangerous and time consuming to experiment with manually editing it.

I put forward **fglrxconfig** as a valid option for those of us who are new to Linux and require a quick and easy way to set up their graphics driver.

I do not pretend to understand all the options for this command.  I selected the default for many.  If I get time I'll investigate what the implications are of using options other than the defaults and also I feel its worth looking at the resulting XORG.CONF which this command produces.

Thanks other contrbuters to this thread - I've finaly got my PC working the way I want it under Breezy which I have found to be far superior in many ways to my old setup.

---

### Post by hedone on 2005-12-03
[QUOTE=mlomker]I don't understand what you are asking.  That command removes the restricted-modules package for the currently running kernel.  The module-assistant command then builds the module for the currently running kernel.[/QUOTE]

by going through your how-to i get restricted-modules for 386 kernel. But as i was sayin' i'm usein' 686 kernel... and my card is stil on mesa... :(((

and yes... computer is slower if u use fglrx driver and mesa for openGL... :(((

i did manage to use fglrx on Fedora 4 when i did use it... but ubuntu is (at least for me) much better then Fedora... and fglrx is one of 3 things i still work on to make them go... yes... there is wake-up from sleep problem and card reader 5in1... for nx9110 HP that is (i think) all that u can imagine to work... 


hope u understand my Q now... as u can see my eng is not best there is... ;) sory for that!

---

### Post by mlomker on 2005-12-03
[QUOTE=steviecee]I put forward **fglrxconfig** as a valid option for those of us who are new to Linux and require a quick and easy way to set up their graphics driver.
[/QUOTE]

Yeah, I suppose that I could mention that in the how-to.  The problem is scope creep--if I start adding every possible detail to the how-to then it becomes difficult to read and scares people.  I've tried to keep it minimal.

---

### Post by mlomker on 2005-12-03
[QUOTE=hedone]by going through your how-to i get restricted-modules for 386 kernel. 
[/quote]

That isn't possible.  Nothing in the how-to installs that package.  Remove it using Synaptic if the command-line removal isn't working for you.

> But as i was sayin' i'm usein' 686 kernel... and my card is stil on mesa... 

Then you'll have to troubleshoot the problem.  Look for errors in /var/log/kern.log and Xorg.0.log.

---

### Post by hedone on 2005-12-03
[QUOTE=mlomker]Then you'll have to troubleshoot the problem.  Look for errors in /var/log/kern.log and Xorg.0.log.[/QUOTE]

i'm gonna do it again and i'll post my logs here... gimme a few minutes...

---

### Post by hedone on 2005-12-03
Here i am again... and this time with my logs... here they are...

---

### Post by hedone on 2005-12-03
Xorg.0.log is in att!



and my fglrxinfo:
hedone@hedone:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)



i can't see any problems... can u plz give me some solution? plz plz plz


thanx!!!

---

### Post by dezier on 2005-12-03
steviecee: With the Dual screen option, can you move windows between the screens? It shouldn't be possible without Xinerama (according to what i have heard and read). I had to use the aticonfig-command with the option of Big desktop to get it work similiar to Xinerama (i have noticed this work in Gnome, but not in Xfce, the latter want to maximize windows to both screens).

---

### Post by mlomker on 2005-12-03
The answer is here:

```

(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"

```

The driver doesn't support your particular card.  I'd recommend asking on the Rage3D board to see if there are any work-arounds.  Let me know if you find one because there are other people with that card.

---

### Post by hedone on 2005-12-03
What about change chip ID? how harmfull can taht be for my card? and yes... haw did the driver works on fedora then? i'm gonna go ask on rage 3d... and be back to u if u don't mind... 

and yes realy... how to change chip ID in my xorg? and thanx!!! realy!!!

conf is in att!

---

### Post by Cuppa-Chino on 2005-12-03
[QUOTE=hedone]
and yes realy... how to change chip ID in my xorg? and thanx!!! realy!!!
[/QUOTE]

actually quite simple (hey I managed it) - find out what ChipID you want to use at [http://pciids.sourceforge.net/iii/?i=1002]("http://pciids.sourceforge.net/iii/?i=1002")

I have Radeon 9500 ("L"-layout) from above link and hardware recognisation I can see it is a **R300 AD [Radeon 9500 Pro]** with ChipID **4144**

I ended up using **Radeon R300 ND [Radeon 9700 Pro]** with ChipID **4e44	** in my xorg.conf. I modified  the device section just after the BusID, by just *hashing out* vendor & device info and adding ChipID (with _0x_ infront as below)
```
BusID "PCI:1:0:0" # vendor=1002, device=4144
ChipID 0x4E45 
```

I presume that you are trying to get the yours to work so that would be after:


also see [change of ChipID in stuborn fglrx thread]("http://ubuntuforums.org/showthread.php?t=80215&page=2&highlight=chipid")```
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:5:0"    # vendor=1002, device=5835
    **[COLOR="Red"]ChipID 0x**_9999_[/COLOR] #replace 9999 with your choice of compatible ID
    Screen 0
EndSection
```

---

### Post by mlomker on 2005-12-03
[QUOTE=Cuppa-Chino]I presume that you are trying to get the yours to work so that would be after:[/QUOTE]

Yup, changing the ChipID is pretty easy.  I wanted the poster to ask on Rage3D because there is probably a technical reason that their card isn't supported.  Faking the driver in such an instance could render the machine very unstable...if it works at all.

---

### Post by steviecee on 2005-12-03
Dezier: steviecee: With the Dual screen option, can you move windows between the screens? It shouldn't be possible without Xinerama (according to what i have heard and read). I had to use the aticonfig-command with the option of Big desktop to get it work similiar to Xinerama (i have noticed this work in Gnome, but not in Xfce, the latter want to maximize windows to both screens).

Your right its not possible.  I'll try the aticonfig command.  Thanks for the sugestion.

---

### Post by koni2005 on 2005-12-05
Just one question:

Anybody in this thread using Ubuntu or Kubuntu Breezy for ppc? I'm trying to get xorg.drivers.fglrx installed on my G4 PowerBook. Am I wasting my time?

thanks...

---

### Post by hedone on 2005-12-05
well thanx for "how to" on change chip ID, but as Mlomker write... there must be some reason why my card is not supported... so it's better not to mess with... (i think)... 

and yes... IGP 9000 is listed in fglrxconfig... did u see that mlomker? I'm gonna ask Ati about that... maybe there is an answer to that...


And chuppa-chino... i can not find any suitable chip for my card... :(

---

### Post by hedone on 2005-12-05
Yes there is one more Q... what about radeon driver??? on rage 3d i'w get answer:

> You must use the radeon driver from X. I am pretty sure fglrx does not support DRI on IGP chipsets.... and after reading the manpage the radeon driver may not either...You may be outta of luck.... From the manpage ([http://www.die.net/doc/linux/man/man4/radeon.4.html](http://www.die.net/doc/linux/man/man4/radeon.4.html)) :

Quote:
radeon is a Xorg driver for ATI RADEON based video cards. It contains full support for 8, 15, 16 and 24 bit pixel depths, dual-head setup, flat panel, hardware 2D acceleration, hardware 3D acceleration (except R300 and IGP series cards), hardware cursor, XV extension, Xinerama extension.  


Try the radeon driver and if that does not help (see this thread for more information ( [http://www.rage3d.com/board/showthr...p?t=33836519%29](http://www.rage3d.com/board/showthr...p?t=33836519%29) ), bad luck... (my old compaq laptop with an IGP340 stays in Windows for this exact reason).



what about that driver? and where to get it?

---

### Post by Onthax on 2005-12-05
I go through the whole process find but when i run "fglrxinfo" i get

onthax@3way:~$ fglrxinfo
l```
ibGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

running  "LIBGL_DEBUG=verbose fglrxinfo" i get


```
libGL: XF86DRIGetClientDriverName: 8.19.10 fglrx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.19.10 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Permission denied)
drmOpenDevice: open result is -1, (Permission denied)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -13
drmOpenDevice: minor is 1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 2
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 3
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 4
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 5
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 6
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 7
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 8
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 9
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 10
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 11
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 12
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 13
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1003
drmOpenDevice: minor is 14
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1003
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

I confused and dont know where to go from here

i'm not using a 64 bit processor, and am using an ATI radeon 9800 Pro 128mb

---

### Post by whobutdrew on 2005-12-05
I am attempting to install the ATI fglrx drivers for my Radeon 9250 and when I run this command:

sudo modprobe fglrx

I get this message:

FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/volatile/fglrx.ko): Operation not permitted

Help please?

---

### Post by hedone on 2005-12-05
and why do u do modprobe fglrx??? did u install driver by mlomker's how to [http://ubuntuforums.org/showthread.php?t=78466]("http://ubuntuforums.org/showthread.php?t=78466")?????

---

### Post by whobutdrew on 2005-12-05
[QUOTE=hedone]and why do u do modprobe fglrx??? did u install driver by mlomker's how to [http://ubuntuforums.org/showthread.php?t=78466]("http://ubuntuforums.org/showthread.php?t=78466")?????[/QUOTE]

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver)

I was following that.   I'll follow yours if that's "better"

---

### Post by batalha on 2005-12-05
(linux rating warning: noob :P)

I've got a very strange error. The installation seems to be fine (though if you check my X log, I believe there are a few lines missing..), but when I start x I get a "no signal" warning! I'm quite sure this is well installed, so what's happening? Chip incompability? (Via pt880 pro, using agp on vga and dvi).

[http://ati.cchtml.com/show_bug.cgi?id=258](http://ati.cchtml.com/show_bug.cgi?id=258)

Please help! Can you detect anything wrong with the xlog? (anyone has one to compare?) Thanks in advance!

---

### Post by ivanhoe on 2005-12-05
I just wanted to say **THANKS** for HOW TO. Problem solved.:p

---

### Post by mlomker on 2005-12-05
[QUOTE=hedone]what about that driver? and where to get it?[/QUOTE]

Ubuntu calls it ATI.  It's the default driver.  Another way for saying that it doesn't support dri is: gonna be slow.

---

### Post by mlomker on 2005-12-05
[QUOTE=Onthax]I go through the whole process find but when i run "fglrxinfo" i get

onthax@3way:~$ fglrxinfo
l```
ibGL error: failed to open DRM: Operation not permitted
[/QUOTE]

I think you have some file permissions that are wrong.  Try **sudo fglrxinfo** once.  If that works then you need to look at the permissions on your files:

[code]
mlomker@mlomkernote:/usr/X11R6/lib/modules/extensions$ ls -l
total 3015
-rw-r--r--  1 root root   15928 2005-10-10 13:10 libdbe.a
-rw-r--r--  1 root root   29410 2005-10-10 13:10 libdri.a
-rw-r--r--  1 root root  151264 2005-10-10 13:10 libextmod.a
-rw-r--r--  1 root root 2331122 2005-10-10 13:10 libGLcore.a
-rw-r--r--  1 root root  481602 2005-10-10 13:10 libglx.a
-rw-r--r--  1 root root   24096 2005-10-10 13:10 librecord.a
-rw-r--r--  1 root root   38374 2005-10-10 13:10 libxtrap.a

```

---

### Post by mlomker on 2005-12-05
[QUOTE=whobutdrew]I was following that.   I'll follow yours if that's "better"[/QUOTE]

That's for Breezy's [included driver]("http://ubuntuforums.org/showthread.php?p=408111").  This thread is for supporting my how-to on the installation of the latest driver.

I think the only way to measure the quality of how-to is whether or not it works.  That one obviously didn't work for you.

---

### Post by mlomker on 2005-12-05
[QUOTE=batalha]Please help! Can you detect anything wrong with the xlog? (anyone has one to compare?) [/QUOTE]

It looked normal to me.  Have you verified that the driver is detecting the proper capabilities of the display?  You might want to try a modeline at a conservative resolution and refresh rate.

---

### Post by arpunk on 2005-12-05
Well, i tried the installation of the drivers, both kernel 386 (default) and 686-smp, and using a clean installation, the only thing i installed where the 686-smp kernel, and the tango icons. Then followed your guide *step by step*. I must say first, direct rendering is enabled with the default ati driver xorg provides, in my default installation, im playing enemy territory real good, however, my official ati drivers, didnt work out. Once installed, *before* GDM starts, computer gets frozen, so i ran the rescue mode and tried the fglrxconfig, same results. Here are my logs:

---

### Post by mlomker on 2005-12-05
[QUOTE=arpunk]direct rendering is enabled with the default ati driver xorg provides, in my default installation, [/quote]

MESA is software-based 3D.  I get about 500 fps from glxgears with it and 2350 from the fglrx driver.

The log that you posted uses the Radeon driver...nothing to see there.  If you're getting a hard lockup (Ctrl-Alt-F2 doesn't work) then there's some kind of hardware conflict.  If you can get to a prompt then you should save the /var/log/kern.log and Xorg.0.log somewhere for reference.

---

### Post by arpunk on 2005-12-05
Yes, i know, but remember my ati drivers doesnt work yet :/ (logs attached to my previous post), so i have to use mesa for now :S

---

### Post by mlomker on 2005-12-05
[QUOTE=arpunk]Yes, i know, but remember my ati drivers doesnt work yet :/ (logs attached to my previous post), so i have to use mesa for now :S[/QUOTE]

I know.  What I'm saying is that your Radeon log is not of any use in troubleshooting the *fglrx* driver.

You could try manually loading the fglrx driver with **sudo modprobe fglrx** and then looking in the kern.log file to see if you get errors.

---

### Post by arpunk on 2005-12-05
Well, since you said it was probably a hardware issue (i didnt get another console, so i assumed it was a hardware lock), i went to the bios, searching for logs and settings, and i found that my AGP apperture size was 64mb, i looked in the options and it was a drop box, and the max value was 256mb, which i assumed it was ok (my ati card has 256mb), changed, saved, rebooted and now i have:
```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1017 (X4.3.0-8.19.10)

$

```
fgl_glxgears shows me:
```

$ fgl_glxgears
Using GLX_SGIX_pbuffer
1495 frames in 5.0 seconds = 299.000 FPS
1768 frames in 5.0 seconds = 353.600 FPS
1774 frames in 5.0 seconds = 354.800 FPS
1768 frames in 5.0 seconds = 353.600 FPS
$

```
And glxgears shows me:
```

$ glxgears -iacknowledgethatthistoolisnotabenchmark
10150 frames in 5.0 seconds = 2029.844 FPS
10045 frames in 5.0 seconds = 2008.849 FPS
10251 frames in 5.0 seconds = 2050.191 FPS
10278 frames in 5.0 seconds = 2055.573 FPS
10391 frames in 5.0 seconds = 2078.014 FPS
5361 frames in 5.0 seconds = 1071.372 FPS
1026 frames in 5.0 seconds = 205.038 FPS
$

```
The dropdown was because i maximized the window, thus i thought it wouldnt make any difference but anyway, driver works, thanks mlomker for your patiente with all of us that want to get the driver working and get things screwed n_n, huge thanks.

EDIT: lol, enemy territory doesnt work :P, im gonna try to take a look at that.

---

### Post by Dropknee on 2005-12-05
I got a problem, when I try to log out, the screen goes black and I cant see the log in screen, same happen when I try to shutdown or reboot, the process for shutdown or reboot work just I cant see them.

any help??

---

### Post by Rinzwind on 2005-12-06
I used your faq and this post/how to: [http://www.ubuntuforums.org/showpost.php?p=119518&postcount=1](http://www.ubuntuforums.org/showpost.php?p=119518&postcount=1)
And I got the following: 

rinzwind@Diskworld:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

glxgears got me 3 turning hmm what you call them in  english? 
and fgl_glxgears for me the following:

> 
1678 frames in 5.0 seconds = 335.600 FPS
2176 frames in 5.0 seconds = 435.200 FPS
1719 frames in 5.0 seconds = 343.800 FPS
2747 frames in 5.0 seconds = 549.400 FPS
2990 frames in 5.0 seconds = 598.000 FPS
2759 frames in 5.0 seconds = 551.800 FPS
3005 frames in 5.0 seconds = 601.000 FPS
2964 frames in 5.0 seconds = 592.800 FPS
2748 frames in 5.0 seconds = 549.600 FPS
2042 frames in 5.0 seconds = 408.400 FPS 

So I would like to express my appreciation for helping me get this working (well it worked w/o a glitch I think 
and the cube -looks- speedy but are these number ok? 
I am using an X300 on a Dell Inspirion 9300.

*does another happy dance*

---

### Post by arpunk on 2005-12-06
Well, the only thing i can play is planetpenguin-racer, all other OpenGL games freeze my box, restart X (ctrl + alt + backspace) and heres what i get with *dmesg*:
```

[4294789.478000] mtrr: no MTRR for e0000000,400000 found
[4294789.478000] mtrr: no MTRR for e0400000,200000 found
[4294789.478000] mtrr: no MTRR for e0600000,100000 found
[4294789.478000] mtrr: no MTRR for e0700000,1000 found
[4294789.478000] [fglrx:firegl_rmmap] *ERROR* map 0xe6cb7e90 still in use (map_count=1)
[4294789.478000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xe6cb7e80 still mapped
[4294789.478000] [fglrx:firegl_rmmap] *ERROR* map 0xe6cb7e50 still in use (map_count=1)
[4294789.478000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xe6cb7e40 still mapped
[4294789.478000] [fglrx:firegl_rmmap] *ERROR* map 0xdfb44790 still in use (map_count=1)
[4294789.478000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xdfb44780 still mapped
[4294789.478000] [fglrx:firegl_rmmap] *ERROR* map 0xc1b215d0 still in use (map_count=1)
[4294789.478000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xc1b215c0 still mapped
[4294789.478000] [fglrx:firegl_rmmap] *ERROR* map 0xc1b21650 still in use (map_count=1)
[4294789.478000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xc1b21640 still mapped
[4294792.036000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4294792.037000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4294718.656000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4294718.656000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[4294718.656000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294718.979000] [fglrx] free  AGP = 256126976
[4294718.979000] [fglrx] max   AGP = 256126976
[4294718.979000] [fglrx] free  LFB = 116387840
[4294718.979000] [fglrx] max   LFB = 116387840
[4294718.979000] [fglrx] free  Inv = 134217728
[4294718.979000] [fglrx] max   Inv = 134217728
[4294718.979000] [fglrx] total Inv = 134217728
[4294718.979000] [fglrx] total TIM = 0
[4294718.979000] [fglrx] total FB  = 0
[4294718.979000] [fglrx] total AGP = 65536

```
And xorg logs says nothing wrong. I get the same error if i put the "UseInternalAGP" "yes" option in xorg.conf. Any ideas?

---

### Post by mlomker on 2005-12-06
[QUOTE=Dropknee]I got a problem, when I try to log out, the screen goes black and I cant see the log in screen, same happen when I try to shutdown or reboot, the process for shutdown or reboot work just I cant see them.
[/QUOTE]

Afraid not.  If you keep your system up-to-date in Synaptic then you might want to ask on the Rage3D board.  I get an interesting checkboard pattern every 10 shutdowns or so and I have to hit the power button.  

There are also known issues with trying to open a second X session.

---

### Post by mlomker on 2005-12-06
[QUOTE=Rinzwind]and the cube -looks- speedy but are these number ok? 
I am using an X300 on a Dell Inspirion 9300.
[/QUOTE]

Sounds good to me.  I have a Mobility 9700 Pro and I get about 415 fps.

---

### Post by mlomker on 2005-12-06
[QUOTE=arpunk] thanks mlomker for your patiente with all of us that want to get the driver working and get things screwed n_n, huge thanks.

EDIT: lol, enemy territory doesnt work :P, im gonna try to take a look at that.[/QUOTE]

MTRR errors are related to memory.  You should look on the Rage3D board...these issues are usually specific to the card/mobo combination and go away if you replace one or the other.  I'd start by checking that your BIOS is the latest but beyond that you'll want to check the other board.

---

### Post by arpunk on 2005-12-06
Well, ive googling and users on rage3d board have some similar issues, so now im wondering, how can i disable the kernels AGP gart in order to use fglrx's one? i tried to enable it on xorg.conf but it said it will use the kernel one since its enabled, any workaround on this? Using the *Option "mtrr"                       "off"* in xorg.conf still gives me this error: (this time, without the mtrr errors)

```

[4296440.530000] [fglrx:firegl_rmmap] *ERROR* map 0xf3593810 still in use (map_count=1)
[4296440.530000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf3593800 still mapped
[4296440.530000] [fglrx:firegl_rmmap] *ERROR* map 0xf3593290 still in use (map_count=1)
[4296440.530000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf3593280 still mapped
[4296440.530000] [fglrx:firegl_rmmap] *ERROR* map 0xf685b610 still in use (map_count=1)
[4296440.530000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf685b600 still mapped
[4296440.530000] [fglrx:firegl_rmmap] *ERROR* map 0xf35933d0 still in use (map_count=1)
[4296440.530000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf35933c0 still mapped
[4296440.530000] [fglrx:firegl_rmmap] *ERROR* map 0xf647f690 still in use (map_count=1)
[4296440.530000] [fglrx:firegl_free_buffer_queue] *ERROR* buffer qeue 0xf647f680 still mapped

```

---

### Post by mlomker on 2005-12-06
[QUOTE=arpunk]Well, ive googling and users on rage3d board have some similar issues, so now im wondering, how can i disable the kernels AGP gart in order to use fglrx's one? [/QUOTE]

You have to [compile your own kernel]("http://www.ubuntuforums.org/showthread.php?t=85064") without one.  It's a bit of an undertaking and an inconvenience every time that you have to upgrade something.  I've done it before, though.  I'd be surprised if it solved your issue...unless you've gotten some specific advice regarding that.

---

### Post by arpunk on 2005-12-06
[QUOTE=mlomker]You have to [compile your own kernel]("http://www.ubuntuforums.org/showthread.php?t=85064") without one.  It's a bit of an undertaking and an inconvenience every time that you have to upgrade something.  I've done it before, though.  I'd be surprised if it solved your issue...unless you've gotten some specific advice regarding that.[/QUOTE]
Well, i thought it was a different way of disabling that, ill leave that option till last since kernel compiling is a must if you want max customatization, i was planning to do it later on when new .15 get out. Ive done all the steps ATI users on rage3d forums done before and some of them even say its buggy drivers, i guess ill have to boot windows again if i wanna keep gaming. I know now, my next card will be nvidia ](*,)

---

### Post by Onthax on 2005-12-07
I now get


(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8cf8000 at 0xb7b7d000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000

slowly understand more about linux, but this is way over my head

---

### Post by Onthax on 2005-12-07
nevermind all fixed

did an apt-get install kernel-source-2.6.11 kernel-tree-2.6.11

and restarted the process, all worked from there

Thanks heaps for the awesome guide : - )

---

### Post by Fry-kun on 2005-12-07
idiocy deleted

---

### Post by mlomker on 2005-12-07
[QUOTE=Onthax]and restarted the process, all worked from there
[/QUOTE]

:cool:   The module must not have compiled for you the first time.

---

### Post by sociocolorado on 2005-12-08
thanks for help... the driver was installed successfully.


but... i have a problem:

clicking in menu **SYSTEM / LOCK SCREEN** and clicking in **SWITCH USER** the **SYSTEM CRASHES**...

any idea?
it's a bug?

PS: the problem appears in two machinnes with ubuntu 5.10 and ati driver 8.19.10...

sorry my english :(

---

### Post by tud on 2005-12-08
I have a problem, after running 
```
sudo apt-get remove linux-restricted-modules-$(uname -r)
```
my network card (D-Link DWL-650+ with acx100 driver) doesn't work anymore :( and so I can choose between new ati driver without network and old ati driver with network. :confused: 
Do you have any suggestion how to solve my problem?

Thanks :D

---

### Post by mlomker on 2005-12-08
[QUOTE=sociocolorado]it's a bug?
[/QUOTE]

That is known bug.  It's mentioned in ATI's release notes.

---

### Post by mlomker on 2005-12-08
[QUOTE=tud]Do you have any suggestion how to solve my problem?
[/QUOTE]

That's probably because you're using ndiswrapper and that module is a part of the restricted modules package.  You should download the **ndiswrapper-source** package and then use module-assistant to build that package as well:

```

sudo apt-get install ndiswrapper-source
sudo module-assistant a-i ndiswrapper
sudo depmod -a

```

---

### Post by Dropknee on 2005-12-09
New ATI Radeon 8.20.8 (12-8-05) is out, is time to check this out :)

---

### Post by Dropknee on 2005-12-09
Now the question is..... The automatic install work now on Ubuntu or we need the same HowTo for this??

---

### Post by BrokenFace on 2005-12-09
Just wanted to report that I was able to successfully install the newest ATI drivers ( 8.20.8 ) using this method. Fixed the issue I was having with widescreen resolutions.

Thanks a bunch mlomker, this has been bugging me for weeks. :p

---

### Post by giloth on 2005-12-09
When first installing this driver, I had issues with the brightness/gamma being way too bright. After some researching I found that it was because I had the TV-Out on my video card in use (the S-Video cable was plugged into my video card).

After I removed it and restarted, it worked beautifully. The issue is an ATI issue I believe, but not 100% positive.

---

### Post by Treviño on 2005-12-09
[quote=Dropknee]New ATI Radeon 8.20.8 (12-8-05) is out, is time to check this out :)[/quote] 
Good... In the [release notes]("http://www2.ati.com/drivers/linux/linux_8.20.8.html") there I read...:[INDENT][I][FONT=verdana][SIZE=2]Attempting to resume from system suspension no longer results in the system failing to respond.
  [/SIZE][/FONT][/I][/INDENT]Do you think that now SwSuspend2 would work well using this drivers? I mean... Will be supported fglrx modules? Anyone tried?

Thanks!

PS: Some benchmarks...: [http://www.phoronix.com/scan.php?page=article&item=340&num=1](http://www.phoronix.com/scan.php?page=article&item=340&num=1)

---

### Post by Dropknee on 2005-12-09
I got this error when try sudo module-assistant a-i fglrx:
dropknee@ubuntu:~$ sudo module-assistant a-i fglrx
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2
modules/
modules/fglrx/
modules/fglrx/debian/
modules/fglrx/debian/changelog
modules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/debian/rules
modules/fglrx/debian/control.template
modules/fglrx/debian/dirs.template
modules/fglrx/debian/postinst
modules/fglrx/agp3.c
modules/fglrx/agpgart_be.c
modules/fglrx/firegl_public.c
modules/fglrx/i7505-agp.c
modules/fglrx/nvidia-agp.c
modules/fglrx/agp_backend.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/drm_compat.h
modules/fglrx/drm.h
modules/fglrx/drm_os_linux.h
modules/fglrx/drmP.h
modules/fglrx/drm_proc.h
modules/fglrx/firegl_public.h
modules/fglrx/make.sh
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/Makefile
Target package file
/usr/src/fglrx-kernel-2.6.12-10-386_8.19.10-1+2.6.12-10.24_i386.deb already
exists, not rebuilding!
Selecting previously deselected package fglrx-kernel-2.6.12-10-386.
(Reading database ... 131643 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-10-386 (from .../fglrx-kernel-2.6.12-10-386_8.19.10-1+2.6.12-10.24_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.12-10-386:
 fglrx-kernel-2.6.12-10-386 depends on xorg-driver-fglrx (= 8.19.10-1); however:  Version of xorg-driver-fglrx on system is 8.20.8-1.
dpkg: error processing fglrx-kernel-2.6.12-10-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.12-10-386

I: Direct installation failed, trying to post-install the dependencies

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  fglrx-kernel-2.6.12-10-386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 586kB disk space will be freed.
Do you want to continue [Y/n]?

What I need to do???? Help pls

---

### Post by Turgon on 2005-12-09
Have installed the new 8.20.8 drivers. Ran into a lite problem when I typed this command:

sudo module-assistant a-i fglrx

It wouldnt build a new fglrx-kernel deb because of the old one. The old deb had to be deleted:

sudo rm /usr/src/fglrx-kernel-2.6.12-10-686_8.19.10-1+2.6.12-10.24_i386.deb

And after that everything worked like charm:)

---

### Post by Turgon on 2005-12-09
DropKnee:

Try this:

sudo rm /usr/src/fglrx-kernel-2.6.12-10-386_8.19.10-1+2.6.12-10.24_i386.deb

It should work after that.

Good luck!

---

### Post by Dropknee on 2005-12-09
Turgon thx for that, it works now :D. I think the HOWTO need to be updated with this.

Thx again you made my day :D ...... well..... night lol

---

### Post by satyam on 2005-12-10
Hi, guys. A little help needed. Maybe a lot.

I'm *trying* to install the 8.20.8 ATI driver on an AMD64 system. So, I followed the first couple steps of the HowTo, but ran into a snag - it can't find some of the libraries. (I'll attach the complete output from Terminal).

dpkg: /usr/x86_64-linux/lib/libc.so.6 not found.
dpkg: /usr/x86_64-linux/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux/lib/libdl.so.2 not found.
dpkg: /usr/x86_64-linux/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux/lib/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux/lib/libGL.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx'
/tmp/fglrx-install
Removing temporary directory: fglrx-install

This is even after I made a symlink in /usr called x86_64-linux, which points to /usr/lib. In /usr/lib, I know some of the files exist as required - some others don't have the correct number at the end (e.g. libc.so exists, but it's looking for libc.so.6)

e.g. when I go to /usr/lib and do
ls | grep libX11           I get
libX11.a
libX11.so
libX11.so.6
libX11.so.6.2.0

Any ideas, help, comments, will be greatly appreciated. The hardware acceleration on my video card is one of the last things I need to sort out.

Best regards,
satyam.

---

### Post by Robocoastie on 2005-12-10
Do you have 64bit or 32 bit Ubuntu installed? It looks to me like you're trying to install the 64bit ATI driver in a 32 bit OS which is why it can't find the 64 bit libs.

---

### Post by mlomker on 2005-12-10
[QUOTE=Dropknee]New ATI Radeon 8.20.8 (12-8-05) is out, is time to check this out :)[/QUOTE]

I've tried downloading it a half-dozen times and it keeps failing.  I'm not sure what's up with ATI's website but I'll be checking it out soon.  I did hear from one user who said that the same instructions worked fine.

Edit: Just tried again at both work and home and the download stops at 14.5 MB.  :mad:

---

### Post by mlomker on 2005-12-10
[QUOTE=Dropknee]Now the question is..... The automatic install work now on Ubuntu or we need the same HowTo for this??[/QUOTE]

As stated in the beginning of the how-to, automatic installer has worked since 8.18.x.  The issue is that it won't automatically install everything that you need to compile the kernel module--newbies aren't going to be able to figure that out.  There also isn't any uninstall option if you use their installer.

---

### Post by mlomker on 2005-12-10
[QUOTE=giloth]After I removed it and restarted, it worked beautifully. The issue is an ATI issue I believe, but not 100% positive.[/QUOTE]

Thanks for that!  I've heard a few people complain about gamma and I'll ask them about video-out next time.

---

### Post by mlomker on 2005-12-10
[QUOTE=Treviño]Do you think that now SwSuspend2 would work well using this drivers? I mean... Will be supported fglrx modules? Anyone tried?
[/QUOTE]

It was supposed to be fixed in 8.19.10 and it obviously wasn't.  ;)

The chatter I've seen on the Rage3D board would suggest that it still isn't working for a lot of people.

---

### Post by mlomker on 2005-12-10
[QUOTE=Dropknee]Turgon thx for that, it works now :D. I think the HOWTO need to be updated with this.[/QUOTE]

I suppose, but the how-to was always intended to start from a clean install of Breezy for a user that is currently on the ATI drivers.  They call that scope creep.  :)

I actually don't recommend simply deleting the file...you should remove the package (that's why we create DEBS!):

```

sudo apt-get remove fglrx-kernel-$(uname -r)

```

---

### Post by mlomker on 2005-12-10
[QUOTE=Robocoastie]Do you have 64bit or 32 bit Ubuntu installed? It looks to me like you're trying to install the 64bit ATI driver in a 32 bit OS which is why it can't find the 64 bit libs.[/QUOTE]

Right on.  They will need to download the driver for the version of Ubuntu that they are running and not the processor itself.

---

### Post by windowsrefund on 2005-12-10
Is the howto updated to reflect the status of working with the latest ATI installer? Hopefully, one wouldn't have to read 45 messsages just to find out what the correct steps are.


All the best...

---

### Post by mlomker on 2005-12-10
[QUOTE=windowsrefund]Is the howto updated to reflect the status of working with the latest ATI installer? Hopefully, one wouldn't have to read 45 messsages just to find out what the correct steps are.
[/QUOTE]

That's why the how-to is a single post--it keeps things clear and uncluttered.  Post #451 (7 back) states that I haven't been able to download the latest version.  I'll get it updated as soon as I can, but other people have reported that the process hasn't changed for the latest release.  

I don't appreciate the tone of your message.  I've spent hundreds of hours on this how-to and helping people get their drivers installed.  You don't have time to read a dozen posts?  You can guess my response to that.  :p

---

### Post by hedone on 2005-12-10
ok... me again... the new driver is out by ati and here is my first Q... what does that mean??? : ```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

what Xlib??? what XFree86-DRI??? and yes... did anybody try those drivers yet?

---

### Post by windowsrefund on 2005-12-10
[QUOTE=mlomker]  

I don't appreciate the tone of your message.  I've spent hundreds of hours on this how-to and helping people get their drivers installed.  You don't have time to read a dozen posts?  You can guess my response to that.  :p[/QUOTE]

Why so defensive? The question was a fair one considering the version numbers indicated in the howto. Just because you spent a hundred hours on this info doesn't mean I (or anyone else) should have to duplicate that effort if it can be avoided. 

Get off your high horse please.

---

### Post by mlomker on 2005-12-10
[QUOTE=windowsrefund]Why so defensive? [/quote]

Perhaps it was just they way you word things, but I have found both of your posts rude.  You seem to value your time above mine.  The only payment that I get for my time is the occassional 'thank you' and you seem to be giving the opposite.

This is the support thread for my how-to.  You're welcome to discuss whatever you like by starting another thread.

---

### Post by mlomker on 2005-12-10
.

---

### Post by patsi on 2005-12-10
I have the same problem ass hedon with the new drivers. Everything seems to load ok but i when i type fglrxinfo i get 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

and in /var/log/Xorg.0.log 

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

I have no ide why it wont work. The previus ati driver worked but I hoped i would get acpi sleep to work with the new drivers. If any body have succeded in geting the new drivers up and runing I would realy like to know how they did.

Cheers ;)

---

### Post by mlomker on 2005-12-10
[QUOTE=patsi]I have no ide why it wont work. The previus ati driver worked but I hoped i would get acpi sleep to work with the new drivers. If any body have succeded in geting the new drivers up and runing I would realy like to know how they did.
[/QUOTE]

What are you getting in /var/log/kern.log?  

It looks like I may get a copy, yet!  My download is half-way now...which is a miracle.

---

### Post by penvzila on 2005-12-10
I have a laptop with a Radeon 9700 Mobility, and I had to eventually run fglrxconfig to get it to work.  Just saying, even though in one of the howtos it says not to do that, if you have the same card I do and nothing else is working, give it a shot.

---

### Post by alonso on 2005-12-10
I was able to install fglrx 8.19.10 and 8.20.8 to the ubuntu breezy 2.6.12-10 kernel, using the instructions in 
[http://www.ubuntuforums.org/showthread.php?t=76116&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=76116&highlight=fglrx)

 but I'm having problems installing them to 2.6.12-9 with the swsusp2 patch from:
[http://www.ubuntuforums.org/showthread.php?t=75443&highlight=swsusp2](http://www.ubuntuforums.org/showthread.php?t=75443&highlight=swsusp2)

Any ideas?

 This is the error i'm getting when I'm doing **module-assistant a-i fglrx**:

```

dh_testroot
rm -f configure-stamp
rm -f fglrx.ko fglrx.mod.c *.o libfglrx_ip.a
rm -f .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
rm -rf patch
dh_clean
rm /usr/src/modules/fglrx/debian/control
rm /usr/src/modules/fglrx/debian/dirs
if [ -f /usr/src/modules/fglrx/debian/control.template ]; then \
	cat /usr/src/modules/fglrx/debian/control.template > /usr/src/modules/fglrx/debian/control; \
fi
if [ -f postinst ]; then \
	mv postinst fglrx-kernel-2.6.12.postinst; \
fi
dh_testdir
touch configure-stamp
dh_testdir
/usr/bin/make -C /usr/src/linux SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12-swsusp2'
  CC [M]  /usr/src/modules/fglrx/agp3.o
  CC [M]  /usr/src/modules/fglrx/nvidia-agp.o
  CC [M]  /usr/src/modules/fglrx/agpgart_be.o
/usr/src/modules/fglrx/agpgart_be.c: In function `__fgl_agp_init':
/usr/src/modules/fglrx/agpgart_be.c:8173: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/usr/src/modules/fglrx/agpgart_be.c: In function `__fgl_agp_cleanup':
/usr/src/modules/fglrx/agpgart_be.c:8183: warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)
/usr/src/modules/fglrx/agpgart_be.c: At top level:
/usr/src/modules/fglrx/agpgart_be.c:6077: warning: 'ati_gart_base' defined but not used
  CC [M]  /usr/src/modules/fglrx/i7505-agp.o
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c: In function `firegl_stub_putminor':
/usr/src/modules/fglrx/firegl_public.c:543: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/usr/src/modules/fglrx/firegl_public.c:545: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/usr/src/modules/fglrx/firegl_public.c: In function `firegl_stub_register':
/usr/src/modules/fglrx/firegl_public.c:565: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
/usr/src/modules/fglrx/firegl_public.c:596: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/usr/src/modules/fglrx/firegl_public.c: In function `fglrx_pci_suspend':
**/usr/src/modules/fglrx/firegl_public.c:660: error: invalid operands to binary ==**
/usr/src/modules/fglrx/firegl_public.c:678: error: incompatible types in assignment
/usr/src/modules/fglrx/firegl_public.c: In function `fglrx_pci_resume':
/usr/src/modules/fglrx/firegl_public.c:692: error: invalid operands to binary ==
/usr/src/modules/fglrx/firegl_public.c:703: error: invalid operands to binary ==
/usr/src/modules/fglrx/firegl_public.c:706: error: incompatible types in assignment
/usr/src/modules/fglrx/firegl_public.c: At top level:
/usr/src/modules/fglrx/firegl_public.c:717: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function `do_vm_kmap_nopage':
/usr/src/modules/fglrx/firegl_public.c:2610: warning: assignment makes pointer from integer without a cast
make[2]: *** [/usr/src/modules/fglrx/firegl_public.o] Error 1
make[1]: *** [_module_/usr/src/modules/fglrx] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12-swsusp2'
make: *** [build] Error 2

```

---

### Post by mlomker on 2005-12-10
[QUOTE=penvzila]I have a laptop with a Radeon 9700 Mobility, and I had to eventually run fglrxconfig to get it to work.  Just saying, even though in one of the howtos it says not to do that, if you have the same card I do and nothing else is working, give it a shot.[/QUOTE]

I actually present that as an option now because the new one is a lot nicer than it was in 8.16.x.  The reason that I don't lead with that for single-monitor installs is because it asks a whole lot of questions and some users get flustered.

FWIW, I have the same 'card' and mine works fine with aticonfig.

---

### Post by mlomker on 2005-12-10
[QUOTE=alonso] but I'm having problems installing them to 2.6.12-9 with the swsusp2 patch from:[/QUOTE]

I'm not sure what that patch does, but the whole point behind this ATI update is to fix suspend issues.  Patches usually only work with specific versions of files.

I just finished installing the latest drivers, myself, and they worked fine.  glxgears is showing a higher output but as they stress, 'it is not a benchmark' because video card vendors can tune the drivers to show higher numbers.

---

### Post by patsi on 2005-12-10
This is the only thing that can find in /var/log/kern.log that i think have any thing to do with fglrx driver.

Dec 10 23:09:55 localhost kernel: [4299897.985000] [fglrx:drm_alloc] *ERROR* [buflist] Allocating 0 bytes

Sorry fore bad english, not my nativ language. Hope this would be to some use to some one who knows linux better than I do, quiet new to this.

Cheers

---

### Post by mlomker on 2005-12-10
[QUOTE=patsi]Dec 10 23:09:55 localhost kernel: [4299897.985000] [fglrx:drm_alloc] *ERROR* [buflist] Allocating 0 bytes
[/QUOTE]

I found [this thread]("http://www.rage3d.com/board/showthread.php?t=33834557").  Are using suspend2?  Look at post #25.  Are you seeing those MTRR errors in your log?

You might want to post a message there.

---

### Post by aleyah on 2005-12-10
I've got a problem following the tutorial:

after the command
```
sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
```
these are the results:
> Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.20.8............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx /home/andrea/fglrx-install
/home/andrea/fglrx-install
Removing temporary directory: fglrx-install
root@ubuntu:/home/andrea#


and no .deb packages are created... where is my fault?

---

### Post by Turgon on 2005-12-10
[QUOTE=mlomker]I suppose, but the how-to was always intended to start from a clean install of Breezy for a user that is currently on the ATI drivers.  They call that scope creep.  :)

I actually don't recommend simply deleting the file...you should remove the package (that's why we create DEBS!):

```

sudo apt-get remove fglrx-kernel-$(uname -r)

```[/QUOTE]

Yeah, but when I tried to remove the DEB, but apt-get couldn't find it, so I just deleted the file. Havn't had any problems with that yet. 

Thanks for updating the gude!

---

### Post by Turgon on 2005-12-10
[QUOTE=aleyah]I've got a problem following the tutorial:

after the command
```
sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
```
these are the results:


and no .deb packages are created... where is my fault?[/QUOTE]

It looks like you are running as root. Try running the command in a normal terminal.

---

### Post by joepease on 2005-12-10
I previously did this tutorial before I updated with the new breezy kernel.  After I updated the kernel it blew the fglrx install of 8.18.  I went ahead and removed the drivers and followed the tutorial again, only this time with the 8.20.8 drivers and everything went through smoothly and installed correctly.  However, when I rebooted, the driver was listed as the mesa version of openGL and 3d acceleration.  When I went into my xorg log file I found this error:

(II) RADEON(0): [drm] drmOpen failed
(EE) RADEON(0): [dri] DRIScreenInit failed. Disabling DRI.

Anyone have any ideas on what's going on here?  Thanks.

---

### Post by penvzila on 2005-12-10
[quote=mlomker]I actually present that as an option now because the new one is a lot nicer than it was in 8.16.x. The reason that I don't lead with that for single-monitor installs is because it asks a whole lot of questions and some users get flustered.

FWIW, I have the same 'card' and mine works fine with aticonfig.[/quote] 
Ah, the howto must have changes since I last read it.  I think I'll try the latest one to see if hibernation really works.

---

### Post by sexualpotatoes on 2005-12-11
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


armyops
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error


any ideas?

P.S. I have PCI-E x800xl

---

### Post by aleyah on 2005-12-11
[QUOTE=Turgon]It looks like you are running as root. Try running the command in a normal terminal.[/QUOTE]
that was only a try, with a normal user the result is the same:
> andrea@ubuntu:~$ sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
Password:
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.20.8............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/fglrx-install
~/fglrx-install
Removing temporary directory: fglrx-install
andrea@ubuntu:~$

no DEB package was created, only a fglrx-installer_8.20.8-1_i386.changes is here

---

### Post by alonso on 2005-12-11
That patch adds swsusp2 support to ubuntu 2.6.12-9 kernel. I have found swsusp2 to work in my computer (HP nx8220), while the normal hibernate does not. The problem comes then that I cannot compile the fglrx drivers anymore.

Anybody else succeeded to build swsusp2 & fglrx combination, which works? 2.6.14-3 is not an option to me, since there is a bug, which prevents it to boot it in my laptop.

[QUOTE=mlomker]I'm not sure what that patch does, but the whole point behind this ATI update is to fix suspend issues.  Patches usually only work with specific versions of files.

I just finished installing the latest drivers, myself, and they worked fine.  glxgears is showing a higher output but as they stress, 'it is not a benchmark' because video card vendors can tune the drivers to show higher numbers.[/QUOTE]

---

### Post by patsi on 2005-12-11
Yes I got the new driver working. Don't realy know what I did but it's now working and sleep works as well. The thing that got it working was runing sudo dpkg-reconfigure xserver-xorg and select the fglrx driver and I loaded all moduels and now it works.
I also blacklisted intel_agp don't know if that hade anything to do with it but now it works so I won't bother trying to mess it up again.

:p

---

### Post by sexualpotatoes on 2005-12-11
are there any alternatives to the ati drivers that produce decent FPS?

---

### Post by mlomker on 2005-12-11
[QUOTE=aleyah]and no .deb packages are created... where is my fault?[/QUOTE]

That's really odd and I can't answer that question because there doesn't seem to be any error messages there.

---

### Post by mlomker on 2005-12-11
[QUOTE=penvzila]Ah, the howto must have changes since I last read it.  I think I'll try the latest one to see if hibernation really works.[/QUOTE]

Sure, I update it with each new release and when problems or a better way of doing things are discovered.

---

### Post by mlomker on 2005-12-11
[QUOTE=joepease](II) RADEON(0): [drm] drmOpen failed
(EE) RADEON(0): [dri] DRIScreenInit failed. Disabling DRI.
[/QUOTE]

That's the third post mentioning this error but nobody has posted what they are getting in /var/log/kern.log.  You'll also want to look in /var/log/Xorg.0.log.

I don't have the problem with my laptop.

You do have to re-do the **module-assistant a-i fglrx** step when you change kernels.  All kernel drivers are specific to that kernel version--that's what all that $(uname -r) stuff is in the how-to.

---

### Post by mlomker on 2005-12-11
[QUOTE=Turgon]Yeah, but when I tried to remove the DEB, but apt-get couldn't find it, so I just deleted the file. Havn't had any problems with that yet. 

Thanks for updating the gude![/QUOTE]

You should just open Synaptic and search on **fglrx** then.  The command-line is easier to use in how-to's but I use Synaptic to actually find things.

---

### Post by aleyah on 2005-12-11
[QUOTE=mlomker]That's really odd and I can't answer that question because there doesn't seem to be any error messages there.[/QUOTE]
isn't there a way to see if there was an error?

now i'm back to the easy fglrx installation  with synaptic an everything seems fine.

---

### Post by satyam on 2005-12-11
[QUOTE=mlomker]Right on.  They will need to download the driver for the version of Ubuntu that they are running and not the processor itself.[/QUOTE]

Hi guys.

Thanks for the input, but I *am* using the AMD64 version of Breezy. (I checked the Readme.diskdefines on the cd.) 

Of course, I had downloaded the x86_64 version of 8.20.8 from the ATI site. Maybe I'll have better luck with the i386 version. (But doggone it, it's the x86_64 I'd like to have working!)

Any suggestions?

Best regards,
satyam.

---

### Post by joepease on 2005-12-12
[QUOTE=mlomker]That's the third post mentioning this error but nobody has posted what they are getting in /var/log/kern.log.  You'll also want to look in /var/log/Xorg.0.log.

I don't have the problem with my laptop.

You do have to re-do the **module-assistant a-i fglrx** step when you change kernels.  All kernel drivers are specific to that kernel version--that's what all that $(uname -r) stuff is in the how-to.[/QUOTE]

Yeah, I redid the module-assistant step because xorg was complaining about the wrong version.  After doing so is when I got those errors about the "DRM open failed".

Looking in the kern.log I only find:

localhost kernel Symbols match kernel version 2.6.12.
localhost kernel No module symbols loaded - kernel modules nlocalhost kernel 

then a while laterI get messages from fglrx

localhost kernel [4294692.673000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
localhost kernel [4294692.396000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
localhost kernel [4294692.676000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
localhost kernel [4294692.396000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
localhost kernel [4294692.438000] [fglrx] ACPI power management is initialized.

Everything else in the log file looked normal with no errors...  Thanks for your help.  Let me know if you want to take a look at the full log files.

---

### Post by joepease on 2005-12-12
I beginning to wonder if this is a bug in the fglrx driver for this release...  the 8.16 driver had problems with the Radeon 9000 in my laptop before and wouldn't recognize the full resolution of my monitor at 1400x1050 which is why I upgraded.  I think I still have the 8.18 version, which worked before with the old kernel, and I might give that version a try when I get some more time.

---

### Post by LarryTheCow on 2005-12-12
Hey;

A buddy of mine went through the tutorial, and got the following error after issuing the command "sudo module-assistant a-i fglrx": ```
                                                                      
     &#9474; Installation of the fglrx-kernel-source source failed.
     &#9474;                                                                    
     &#9474; Ignoring this package. Maybe you need to add something to          
     &#9474; sources.list,                                                      
     &#9474; maybe the contrib and non-free archives.     
```

He is using the sources.list provided by the tutorial (minus the typos).

Any ideas?:confused:

---

### Post by mlomker on 2005-12-12
[QUOTE=aleyah]isn't there a way to see if there was an error?[/QUOTE]

Not that I know of, but I didn't write the scripts....it's ATI's installer.

---

### Post by mlomker on 2005-12-12
[QUOTE=joepease]Everything else in the log file looked normal with no errors...  Thanks for your help.  Let me know if you want to take a look at the full log files.[/QUOTE]

Start a new thread and attach the logs (you'll have to compress them).

---

### Post by mlomker on 2005-12-12
[QUOTE=LarryTheCow]He is using the sources.list provided by the tutorial (minus the typos).[/quote]

Oops, fixed the typos.

Did he **sudo apt-get update** after updating the sources.list?  I've seen the error before and it was because one of the packages wasn't installed.  The *prepare* step downloads the kernel headers and a few other packages.

---

### Post by riverfr0zen on 2005-12-12
Hey folks. I have a Compaq Presario X1000 with the ATI Mobility Radeon 9200. Pretty new to Ubuntu, so I tried the fglrx drivers that came with Breezy first. This didn't work - fglrxinfo always kept reporting the Mesa drivers. So, I followed the instructions for the latest ATI drivers. 

The install went fine (using fglrxconfig at the end) - no error messages - I did notice there was no option for 1280x800 in the config, but went with a lower mode temporarily. However, when I restarted X, the display is garbled, all messed up, flickering. I tried to reconfigure several times, using different HorizSync and VertRefresh settings (including ones I know worked on Fedora), and I also tried different display modes. Nothing seems to fix it, although the 'garbled-ness' of the display is different ;) I also noticed I get a HAL error when I load up X, but I'm not sure if that is related.

When using fglrxconfig, I pretty much went with the default values, except for some obvious stuff like mouse settings, etc.

The odd thing is, if I run glrxinfo in the garbled screen, it's the right info - also, if I run glxgears, the 3d framerate looks great. Just the display is messed up. 

Anyone have any tips/pointers? Need any more info from me? Appreciate any help. Thanks.

---

### Post by LarryTheCow on 2005-12-13
[QUOTE=mlomker]Oops, fixed the typos.

Did he **sudo apt-get update** after updating the sources.list?  I've seen the error before and it was because one of the packages wasn't installed.  The *prepare* step downloads the kernel headers and a few other packages.[/QUOTE]

He tried it again after making sure to do "sudo apt-get update"; same error.

---

### Post by mlomker on 2005-12-14
[QUOTE=LarryTheCow]He tried it again after making sure to do "sudo apt-get update"; same error.[/QUOTE]

Then I don't know.  You can always try running the .sh directly and skip the DEB creation.  It sounds like there's something wrong with the build environment on the box, though, in which case that won't work either.

If you can compile anything on the box then it should work.  Build-essential, gcc3.4, and the kernel headers are needed to build a kernel module and the steps for installing them are in the how-to.

---

### Post by mlomker on 2005-12-14
[QUOTE=riverfr0zen]Anyone have any tips/pointers? Need any more info from me? Appreciate any help. Thanks.[/QUOTE]

Sounds like a video card memory problem...I wonder if your system uses shared video memory.  You should check the logs to make sure you aren't getting MTRR errors.  A related [problem here]("http://www.ubuntuforums.org/showpost.php?p=568819&postcount=201").

If you find some relevant errors then you can search on the Rage3D forum...it's the best resource.

---

### Post by ckthomson on 2005-12-15
Heyaz,

I'm fairly new to Ubuntu (although I've been trying different distros  since about 2001) and am having a slight problem getting my ATI card to work properly after following the how-to.

My card is a Radeon 9600 XT All in Wonder (128mb version).  I wish to run it in a single monitor configuration with TV-Out disabled.  Monitor is a bog-standard Samtron st76V, which I generally run at 1280*1024@60hz (my eyes can only stand 60hz because I am a former Amiga user, so I'm used to the flicker).

When I installed the drivers using this How-to, everythign seemed to go OK.  No nasty surprises, everything booted clean.  Control panel shortcut even worked.

However, on loading *any* openGl-accellerated application, including fgl_glxgears, my session locks up.  Actually, that's not 100% accurate, as my mouse pointer can still be moved about, but I can't click anything and my keyboard doesn't respond either.

Here's my xorg.conf : 

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "S/T 76V"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Radeon 9600 XT All In Wonder"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon 9600 XT All In Wonder"
	Monitor    "S/T 76V"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

one of the things that puzzles me is a seeming lack of 32-bit color support, which I thought was standard nowadays. I'm honestly not 100% sure, but I swear the card doesn't support 24-bit under windows (16 or 32 only). I'll doublecheck when i boot back to "the bloat" in the morning.

If I could get this card working with 3d accelleration (doubly so if I could get the capture up and running, too) I would almost be set to ditch Win2k in favor of Ubuntu.

Please help (if you can)

---

### Post by mlomker on 2005-12-15
[QUOTE=ckthomson]one of the things that puzzles me is a seeming lack of 32-bit color support, which I thought was standard nowadays. I'm honestly not 100% sure, but I swear the card doesn't support 24-bit under windows (16 or 32 only). I'll doublecheck when i boot back to "the bloat" in the morning.
[/QUOTE]

I do a pretty good job at getting drivers installed for people, but the color question is a programming one and the lock-ups are a hardware issue (more than likely).  

You've already looked at the logs for errors?  **fglrxinfo** returns driver information without any errors?  My first suspicious would be video memory/BIOS compatibility.  Many of the hardware problems lately have been related to the BIOS not reporting the video memory to the driver properly (plug-and-play gone awry).

Your questions about driver capabilities can best be researched on the Rage3D board.

---

### Post by ckthomson on 2005-12-15
[QUOTE=mlomker]I do a pretty good job at getting drivers installed for people, but the color question is a programming one and the lock-ups are a hardware issue (more than likely).  

You've already looked at the logs for errors?  **fglrxinfo** returns driver information without any errors?  My first suspicious would be video memory/BIOS compatibility.  Many of the hardware problems lately have been related to the BIOS not reporting the video memory to the driver properly (plug-and-play gone awry).

Your questions about driver capabilities can best be researched on the Rage3D board.[/QUOTE]

What exactly am I looking for in the logs, and can said logs accessed using the Gnome System Log Viewer tool?  

fglrx info returns the following :

> wekko@f1sh:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

The "generic" part worries me a tad... it's a 9600XT All-In-Wonder card, which oddly enough get a completely seperate driver release under Windows ... must be to accommodate the capture circuitry.

AFAIK i have PnP Support turned off at BIOS level, and the card *generally* (but not always) reports correctly in Windows as being a 128mb card.  the only 2 exceptions were Everest and Electronic Arts' "EasyInfo" tool, which seemed to see double the video ram.  My Motherboard is an MSI KT6V, with a not-very-recent bios (I'm not comfortable flashing, either, which doesn't help).

Thanks in advance for any help you can provide, it's greatly appreciated.

And thanks for the info on where to find out about the driver capabilities.

------UPDATE-------

have examined a few of the logs, and the following seems to pertain to the video setup, however I have no idea whatsoever if any of this is correct.

> [B]From "/var/log/messages" :
[/B]
[I]Dec 15 13:56:03 localhost kernel: [4294687.336000] Linux agpgart interface v0.101 (c) Dave Jones
Dec 15 13:56:03 localhost kernel: [4294687.377000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Dec 15 13:56:03 localhost kernel: [4294687.401000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
Dec 15 13:56:03 localhost kernel: [4294687.401000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 15 13:56:03 localhost kernel: [4294687.401000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
Dec 15 13:56:03 localhost kernel: [4294687.460000] [fglrx] ACPI power management is initialized.
Dec 15 13:56:03 localhost kernel: [4294687.617000] ts: Compaq touchscreen protocol output
Dec 15 13:56:03 localhost kernel: [4294690.944000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Dec 15 13:56:03 localhost kernel: [4294694.095000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
Dec 15 13:56:03 localhost kernel: [4294694.121000] agpgart: AGP aperture is 128M @ 0xe0000000
Dec 15 13:56:03 localhost kernel: [4294694.464000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 15 13:56:03 localhost kernel: [4294694.728000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 15 13:56:03 localhost kernel: [4294695.543000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec 15 13:56:03 localhost kernel: [4294696.440000] gameport: EMU10K1 is pci0000:00:08.1/gameport0, io 0xec00, speed 1217kHz
Dec 15 13:56:03 localhost kernel: [4294698.419000] Real Time Clock Driver v1.12
Dec 15 13:56:03 localhost kernel: [4294698.527000] input: PC Speaker
Dec 15 13:56:03 localhost kernel: [4294698.730000] FDC 0 is a post-1991 82077
Dec 15 13:56:03 localhost kernel: [4294700.476000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Dec 15 13:56:03 localhost kernel: [4294700.496000] NET: Registered protocol family 17
Dec 15 13:56:03 localhost kernel: [4294703.027000] NET: Registered protocol family 10
Dec 15 13:56:03 localhost kernel: [4294703.027000] Disabled Privacy Extensions on device c02eb280(lo)
Dec 15 13:56:03 localhost kernel: [4294703.027000] IPv6 over IPv4 tunneling driver
Dec 15 13:56:03 localhost kernel: [4294704.608000] ACPI: Power Button (FF) [PWRF]
Dec 15 13:56:03 localhost kernel: [4294704.608000] ACPI: Power Button (CM) [PWRB]
Dec 15 13:56:03 localhost kernel: [4294704.608000] ACPI: Sleep Button (CM) [SLPB]
Dec 15 13:56:08 localhost kernel: [4294709.962000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Dec 15 13:56:08 localhost kernel: [4294709.962000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Dec 15 13:56:08 localhost kernel: [4294709.962000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Dec 15 13:56:08 localhost kernel: [4294709.962000] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
Dec 15 13:56:08 localhost kernel: [4294709.963000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Dec 15 13:56:08 localhost kernel: [4294709.963000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Dec 15 13:56:08 localhost kernel: [4294709.963000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Dec 15 13:56:08 localhost kernel: [4294709.963000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] free  AGP = 121909248
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] max   AGP = 121909248
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] free  LFB = 116387840
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] max   LFB = 116387840
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] free  Inv = 0
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] max   Inv = 0
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] total Inv = 0
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] total TIM = 0
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] total FB  = 0
Dec 15 13:56:08 localhost kernel: [4294710.006000] [fglrx] total AGP = 32768[/I]

---

### Post by mlomker on 2005-12-15
[QUOTE=ckthomson]The "generic" part worries me a tad... [/quote]

That's normal.

> My Motherboard is an MSI KT6V, with a not-very-recent bios (I'm not comfortable flashing, either, which doesn't help).

That's the first thing that I'd do.

> video setup, however I have no idea whatsoever if any of this is correct.

That much looks fine.  Look at /var/log/Xorg.0.log as well.

---

### Post by ckthomson on 2005-12-16
[QUOTE=mlomker]That's normal.



That's the first thing that I'd do.



That much looks fine.  Look at /var/log/Xorg.0.log as well.[/QUOTE]

I didn't see anything in Xorg.0.log that indicated much of anything wrong, although it looks like it might indeed be reporting the video ram size wrong. I've attached Xorg.0.log (compressed as .tar.bz).

I've been impatiently waiting on payday as I need a new case and stuff, I'm going to buy myself a floppy drive (passed it up last upgrade time in favor of cramming more ram into my system) and see what my mobo mfr offers in the way of bios upgrades.

I'm sorry in advance for the long wait between replies, but I work nights and sleep most of the day, so I have about 2x2-hour windows in which I can do stuff.  

Thanks again for your help.
Craig.

---

### Post by tL0z on 2005-12-18
Hello,

I'm having some problems with the tutorial. I've a AMD 64 3200+ and a ATI 9600 XT

Before have found it, I tried to install the drivers directly and it installed. But then, when I tried to check if the games ran well, I clicked on it but they didn't even open.

So I tried your tutorial. When I do that:

```
sudo apt-get remove fglrx-kernel-$(uname -r)
```

it says: "E: Impossível encontrar o pacote fglrx-kernel-2.6.12-10-amd64-generic". In English its: "Impossible to find the package fglrx-kernel-2.6.12-10-amd64-generic".

Can you please help me?

---

### Post by amohanty on 2005-12-18
Thats because they are not installed by default. I am guessing you only installed xorg-driver-fglrx??

AM

---

### Post by tL0z on 2005-12-19
I did what it says in the tutorial. However, I've tried to install the drivers that come with Ubuntu -> [http://ubuntuforums.org/showthread.php?t=105500](http://ubuntuforums.org/showthread.php?t=105500)

---

### Post by falaffelbar on 2005-12-19
[QUOTE=Dropknee]I got a problem, when I try to log out, the screen goes black and I cant see the log in screen, same happen when I try to shutdown or reboot, the process for shutdown or reboot work just I cant see them.

any help??[/QUOTE]

I got the same problem, quite annoying.
Is there any solution or have I missed anything ?

---

### Post by mlomker on 2005-12-19
[QUOTE=falaffelbar]Is there any solution or have I missed anything ?[/QUOTE]

Must be a driver bug.  My machine usually shuts down.  You can try asking on Rage3D...the developers hang out there.

---

### Post by Papa Shango on 2005-12-20
Alright, my ATI Mobility 9000 stopped working after a kernel update and I am unable to get it to work again.  I don't remember exactly what I did the first time, so I am trying the mlomker HOWTO.  When dpkging the xorg-driver-fglrx_8.20.8-1_i386.deb I get the following:

```
steve@ubuntu:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.20.8-1_i386.deb
(Reading database ... 114982 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.20.8-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx' clashes with `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx_8.20.8-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx_8.20.8-1_i386.deb
```

  I am fairly new to Ubuntu and Linux in general so any help would be greatly appreciated.

---

### Post by getaceres on 2005-12-20
I've got the same problem as aleyah:

```
jose@ubuntu:~/Aplicaciones/ati$ sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.20.8............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/Aplicaciones/ati/fglrx-install
~/Aplicaciones/ati/fglrx-install
Removing temporary directory: fglrx-install
jose@ubuntu:~/Aplicaciones/ati$ ls
ati-driver-installer-8.20.8-i386.run  fglrx-installer_8.20.8-1_i386.changes
jose@ubuntu:~/Aplicaciones/ati$
```

---

### Post by l0c0dantes on 2005-12-21
AAAAAHHHHH

Help me please, I can't get my ATI card to get recognized, i run flgrxinfo, and I keep getting this message

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Any help would be appricated

---

### Post by mlomker on 2005-12-21
[QUOTE=Papa Shango]  I am fairly new to Ubuntu and Linux in general so any help would be greatly appreciated.[/QUOTE]

I'm not sure why you're getting that...would depend upon what you had installed before.  I'd try **sudo apt-get update** and **sudo apt-get -f upgrade** and see if that clears it up.

You have to recompile/install the kernel driver when you change kernels.

---

### Post by mlomker on 2005-12-21
[QUOTE=getaceres]I've got the same problem as aleyah:
[/QUOTE]

If you figure it out then let us know.  I've been unable to recreate the problem.

You can skip the DEB creation and just run their .sh installer and see what happens.

---

### Post by mlomker on 2005-12-21
[QUOTE=l0c0dantes]Any help would be appricated[/QUOTE]

Look in /var/log/Xorg.0.log and kern.log for errors.

---

### Post by sexualpotatoes on 2005-12-21
can you put a "last updated on x/x/x" on the tutorial page so we can find out if maybe you fixed an error.

---

### Post by mlomker on 2005-12-22
[QUOTE=sexualpotatoes]can you put a "last updated on x/x/x" on the tutorial page so we can find out if maybe you fixed an error.[/QUOTE]

The board software automatically does that at the bottom of the post.  It current says 'Updated one week ago at 9:21 PM.'

I correct any errors that I know about.  What are you referring to?

---

### Post by Cobra78 on 2005-12-23
Hi, first i excuse for my terrible english :(

Second thing: i've noticed a strange thing when i execute "sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy"

The installer put the pakegs in /tmp, so i need to go in thath directory before using "sudo dpkg -i"; this is not mentioned in your guide, have you forgotten this?

---

### Post by getaceres on 2005-12-23
[QUOTE=Cobra78]Hi, first i excuse for my terrible english :(

Second thing: i've noticed a strange thing when i execute "sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy"

The installer put the pakegs in /tmp, so i need to go in thath directory before using "sudo dpkg -i"; this is not mentioned in your guide, have you forgotten this?[/QUOTE]
Thanks! They were in tmp. I wonder why they didn't copy to the installer directory.

---

### Post by newtech13 on 2005-12-23
Hi,

I'm upgrading from 8.19.10 to 8.20.8 and following strictly the procedure there is a dependency problem.
When I type : sudo module-assistant a-i fglrx
There is an error :

Sélection du paquet fglrx-kernel-2.6.12-9-686 précédemment désélectionné.
(Lecture de la base de données... 144030 fichiers et répertoires déjà installés.)
Dépaquetage de fglrx-kernel-2.6.12-9-686 (à partir de .../fglrx-kernel-2.6.12-9-686_8.19.10-1+2.6.12-9.23_i386.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de fglrx-kernel-2.6.12-9-686 :
 fglrx-kernel-2.6.12-9-686 dépend de xorg-driver-fglrx (= 8.19.10-1) ; cependant :
  La version de xorg-driver-fglrx sur le système est 8.20.8-1.
dpkg : erreur de traitement de fglrx-kernel-2.6.12-9-686 (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 fglrx-kernel-2.6.12-9-686

I: Direct installation failed, trying to post-install the dependencies


And finally I can't install properly 8.20.8

Any ideas ? :confused:

---

### Post by getaceres on 2005-12-23
[QUOTE=newtech13]Hi,

I'm upgrading from 8.19.10 to 8.20.8 and following strictly the procedure there is a dependency problem.
When I type : sudo module-assistant a-i fglrx
There is an error :

Sélection du paquet fglrx-kernel-2.6.12-9-686 précédemment désélectionné.
(Lecture de la base de données... 144030 fichiers et répertoires déjà installés.)
Dépaquetage de fglrx-kernel-2.6.12-9-686 (à partir de .../fglrx-kernel-2.6.12-9-686_8.19.10-1+2.6.12-9.23_i386.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de fglrx-kernel-2.6.12-9-686 :
 fglrx-kernel-2.6.12-9-686 dépend de xorg-driver-fglrx (= 8.19.10-1) ; cependant :
  La version de xorg-driver-fglrx sur le système est 8.20.8-1.
dpkg : erreur de traitement de fglrx-kernel-2.6.12-9-686 (--install) :
 problèmes de dépendances - laissé non configuré
Des erreurs ont été rencontrées pendant l'exécution :
 fglrx-kernel-2.6.12-9-686

I: Direct installation failed, trying to post-install the dependencies


And finally I can't install properly 8.20.8

Any ideas ? :confused:[/QUOTE]
Have you removed the old 8.19 drivers before installing the new 8.20 ones?

---

### Post by mlomker on 2005-12-23
[QUOTE=getaceres]Thanks! They were in tmp. I wonder why they didn't copy to the installer directory.[/QUOTE]

I've had a couple people say that happened to them, but it never has for me.  I updated the how-to to have people check there.

---

### Post by mlomker on 2005-12-23
[QUOTE=getaceres]Have you removed the old 8.19 drivers before installing the new 8.20 ones?[/QUOTE]

I don't know that language so I'm not quite sure what it says.  If you are upgrading using the same method then you have to be sure to remove the old kernel package before compiling the new one.

Search in Synaptic for **fglrx-kernel-2.6** and make sure that the old kernel package is removed before you run module-assistant.  The apt-get remove step mentioned in the how-to should have done that...

---

### Post by joepease on 2005-12-23
[QUOTE=newtech13]Hi,

I'm upgrading from 8.19.10 to 8.20.8 and following strictly the procedure there is a dependency problem.
When I type : sudo module-assistant a-i fglrx
There is an error :

S&#233;lection du paquet fglrx-kernel-2.6.12-9-686 pr&#233;c&#233;demment d&#233;s&#233;lectionn&#233;.
(Lecture de la base de donn&#233;es... 144030 fichiers et r&#233;pertoires d&#233;j&#224; install&#233;s.)
D&#233;paquetage de fglrx-kernel-2.6.12-9-686 (&#224; partir de .../fglrx-kernel-2.6.12-9-686_8.19.10-1+2.6.12-9.23_i386.deb) ...
dpkg : des probl&#232;mes de d&#233;pendances emp&#234;chent la configuration de fglrx-kernel-2.6.12-9-686 :
 fglrx-kernel-2.6.12-9-686 d&#233;pend de xorg-driver-fglrx (= 8.19.10-1) ; cependant :
  La version de xorg-driver-fglrx sur le syst&#232;me est 8.20.8-1.
dpkg : erreur de traitement de fglrx-kernel-2.6.12-9-686 (--install) :
 probl&#232;mes de d&#233;pendances - laiss&#233; non configur&#233;
Des erreurs ont &#233;t&#233; rencontr&#233;es pendant l'ex&#233;cution :
 fglrx-kernel-2.6.12-9-686

I: Direct installation failed, trying to post-install the dependencies


And finally I can't install properly 8.20.8

Any ideas ? :confused:[/QUOTE]

Ah, I evidently was having this same problem without even realizing it.  After reinstalling the divers for probably the 3rd time, I noticed that error.  It seems like the automatic installer has some issues with upgrading the fglrx module.  The solution for me was to use this command:
```

sudo module-assistant purge --force fglrx-kernel-source

```
then:
```

sudo module-assistant a-i fglrx

```
I noticed that even after the removal of the fgrlx-kernel-source package, the module-assistant still listed the fglrx-kernel-source as having binaries built.  I hope this all makes sense and it works for you.

Completely different topic now.  According to the readme that came with 8.20.8 drivers, the drivers support suspend now, right?  When I select suspend, then come out of it, all I get is a black screen.  Anyone have it working?  Thanks.

-Joe

---

### Post by veloct on 2005-12-24
I succesfully installed driver 8.20.8, no problems there.  This is a dual boot machine and when I rebooted to load linux this morning it started fine and dumped me to the command line, I reconfigured xorg and I was able to start x.  I'll investigate further on that, these drivers may not be quite right.  Here's part of my kern.log file from my last bootup, I have a 9550 with 256 mb of ram.  Looking at this part of the log, is it only picking up 32 mb? The AGP aperture on the motherboard is set to 128 mb.

[IMG]http://www.veloct.net/images/kern_log.png[/IMG]

Edit: I went back to the 8.16.20, we'll see what ATI comes up with next year. Otherwise it may be time for a new Nvidia card.

---

### Post by mlomker on 2005-12-24
[QUOTE=joepease]Anyone have it working?  Thanks.
[/QUOTE]

Not many.  There are a number of discussions about the driver on the Rage3D board.

---

### Post by mlomker on 2005-12-24
[QUOTE=veloct]Edit: I went back to the 8.16.20, we'll see what ATI comes up with next year. Otherwise it may be time for a new Nvidia card.[/QUOTE]

Do what you like, but memory aperature problems are always a motherboard BIOS problem...the BIOS is reporting the size wrong to the driver.  The driver has gotten very plug-and-play these days and if the BIOS isn't responding properly to driver inquiries then you're going to have trouble.  There are work-arounds on the Rage3D board...you'll find them in threads relating to MTRR errors.

You might want to start by verifying that your BIOS is the latest-and-greatest.  If you want to pursue it further then the Rage3D board is your best bet.  Odds are that someone running another distro has seen your problem...

---

### Post by veloct on 2005-12-25
The ATI control panel shows 256mb so I'm not too worried. 8.16.20 is the most stable one so far so I'll stick to that for now

When I issue 'lspci -v' it shows the correct memory amount.

---

### Post by ViGiLnT on 2005-12-25
I dont know if anyone had this problem yet, but ita a really long thread... ;)

I went through this How-To and everything went great.

The only problem is that when i had the original drivers from ubuntu, i could had a 1152x864 resolution with 75Hz and now the max availble is 60hz... How can I solve this ?
With this refresh rate i can harldy look at my monitor...

---

### Post by petri on 2005-12-25
Thanks mlomker! I finally got it working. My debs kept on vanishing (message number 381) and I got a little bit frustrated ;)  I've had missed "For me the DEB files are always created in the current directory, but some people have to change to /tmp to find them." on your [how-to]("http://ubuntuforums.org/showpost.php?p=423584") :-\" 

A question: is this good with AIW 8500 and a AMD1800+ 

petri@c-954fe255:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
6901 frames in 5.0 seconds = 1380.093 FPS
8213 frames in 5.0 seconds = 1642.536 FPS
9882 frames in 5.0 seconds = 1976.377 FPS
5813 frames in 5.0 seconds = 1158.832 FPS
8781 frames in 5.0 seconds = 1756.129 FPS
11427 frames in 5.0 seconds = 2285.304 FPS
10509 frames in 5.0 seconds = 2101.776 FPS
11677 frames in 5.0 seconds = 2335.222 FPS
11533 frames in 5.0 seconds = 2306.484 FPS
11229 frames in 5.0 seconds = 2245.782 FPS
11227 frames in 5.0 seconds = 2245.260 FPS
10574 frames in 5.0 seconds = 2114.729 FPS
10362 frames in 5.0 seconds = 2072.381 FPS
10318 frames in 5.0 seconds = 2063.544 FPS
10956 frames in 5.0 seconds = 2189.083 FPS

petri@c-954fe255:~$ glxgears -printfps
9082 frames in 5.0 seconds = 1811.534 FPS
9043 frames in 5.0 seconds = 1803.090 FPS
8991 frames in 5.0 seconds = 1792.249 FPS
9030 frames in 5.0 seconds = 1805.937 FPS
8035 frames in 5.0 seconds = 1606.930 FPS
8842 frames in 5.0 seconds = 1757.534 FPS
9683 frames in 5.0 seconds = 1936.536 FPS
6367 frames in 5.0 seconds = 1271.499 FPS
6817 frames in 5.1 seconds = 1336.505 FPS
7525 frames in 5.0 seconds = 1504.646 FPS
9225 frames in 5.0 seconds = 1839.318 FPS

and with

petri@c-954fe255:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
866 frames in 5.0 seconds = 173.200 FPS
511 frames in 5.0 seconds = 102.200 FPS
1214 frames in 5.0 seconds = 242.800 FPS
1132 frames in 5.0 seconds = 226.400 FPS
1245 frames in 5.0 seconds = 249.000 FPS
1238 frames in 5.0 seconds = 247.600 FPS
1071 frames in 5.0 seconds = 214.200 FPS
940 frames in 5.0 seconds = 188.000 FPS


fglrxinfo gives me:

petri@c-954fe255:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1030 (X4.3.0-8.20.8)

I did use my computer during these short tests.


BTW I did had to add this: Option "VideoOverlay" "on" in Section "Device" in xorg.conf to get it smoother. I wonder why?

---

### Post by mlomker on 2005-12-26
[QUOTE=ViGiLnT]With this refresh rate i can harldy look at my monitor...[/QUOTE]

Try [this how-to]("http://www.ubuntuforums.org/showthread.php?t=83973").  You'll probably need to use a modeline.

---

### Post by mlomker on 2005-12-26
[QUOTE=petri]"For me the DEB files are always created in the current directory, but some people have to change to /tmp to find them." on your 
[/quote]

It wasn't you--that was a recent update to the how-to since a number of people were having that problem.  I'm not sure why I can't recreate that problem (I have six Ubuntu machines at work and none of them do that).

> A question: is this good with AIW 8500 and a AMD1800+ 


Sounds fine to me.

> BTW I did had to add this: Option "VideoOverlay" "on" in Section "Device" in xorg.conf to get it smoother. I wonder why?

If you read through the Rage3D board you'll find a lot more of them.  My understanding is that the Overlay option is related to TV-out, but I don't know a lot about the various options.

---

### Post by petri on 2005-12-27
Thanks again mlomker! :razz:

---

### Post by clapton on 2005-12-27
I did the "How to", and the result of fglrxinfo is

> 
marco@2l33t4U:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)



And the result of glxgears is
> 
marco@2l33t4U:~$ glxgears -printfps
12984 frames in 5.0 seconds = 2596.705 FPS
12954 frames in 5.0 seconds = 2590.654 FPS
12966 frames in 5.0 seconds = 2593.101 FPS
12899 frames in 5.0 seconds = 2579.605 FPS


I take a look on my xorg.conf and I think that's something wrong
```

 Section "Monitor"
     73   Identifier   "lg 17''"
     74   HorizSync    31.0 - 70.0
     75   VertRefresh  50.0 - 100.0
     76   Option      "DPMS"
     77 EndSection
     78
     79 Section "Monitor"
     80   Identifier   "aticonfig Monitor 0"
     81 EndSection
     82
     83 Section "Device"
     84   Identifier  "ATI 9550"
     85   Driver      "ati"
     86   Option      "UseFBDev" "true"
     87   BusID       "PCI:1:0:0"
     88 EndSection
     89
     90 Section "Device"
     91   Identifier  "ATI Graphics Adapter 0"
     92   Driver      "fglrx"
     93   BusID       "PCI:1:0:0"
     94 EndSection

```
For me, newbie, seams that I've got 2 drivers installed. I need help on this thing.

I've got a 2nd problem, When my ubuntu starts, doesn't start the X, i've got to login, and use the startx command.

this is my inittab (resumed)

```
3
      4 # The default runlevel.
      5 id:2:initdefault:

```

I hope that somebody can help me.
sry for my bad written english:rolleyes:

---

### Post by mlomker on 2005-12-27
[QUOTE=clapton]For me, newbie, seams that I've got 2 drivers installed. I need help on this thing.[/quote]

That's normal...that's how aticonfig works.

> I've got a 2nd problem, When my ubuntu starts, doesn't start the X, i've got to login, and use the startx command.

There isn't anything about the driver install that can do that.  If you run gnome then I'd recommend doing a 'complete removal' of **GDM** in Synaptic and then reinstall it.

---

### Post by clapton on 2005-12-27
Thx a lot mlocker, my change NVIDIA to ati was harder on ubuntu, I hope can play now :)

---

### Post by Noctilux on 2005-12-27
The installation of the latest driver worked perfectly. fglrxinfo shows the new driver. I however did not manage to setup the BigDesktop. I used fglrxconfig. I am still working one screen and the other stays totaly brown.

I included my xorg.conf. I have an ATI Radeon 9700 pro card. If anybody else has this working with the same card (or the Xinerama configuration) I would like to see the xorg.conf file.

p.s. I still hope I am posting in the correct thread.

Thanks

RIchard.

```

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection



# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Option		"DPMS"
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:


# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "horizontal" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e44
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###


```

---

### Post by azumi on 2005-12-28
[QUOTE=mlomker]This is the thread for discussing [the how-to]("http://ubuntuforums.org/showpost.php?p=423584") for installing the latest ATI driver that is working for Ubuntu, and troubleshooting the results.[/QUOTE]

thx man, wrks fine on iBM T41p + UBUNTU 5.10

Linux runner 2.6.14.4 #1 PREEMPT Wed Dec 28 10:53:55 CET 2005 i686 GNU/Linux

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

but there is Pentium 4 (SSE2) , hw is Pentium M ...  its ok ?

---

### Post by mlomker on 2005-12-28
[QUOTE=azumi]but there is Pentium 4 (SSE2) , hw is Pentium M ...  its ok ?[/QUOTE]

I wouldn't worry about that.  Ubuntu thinks my card is a Mobility 9600 when it's a 9700.

---

### Post by mlomker on 2005-12-28
[QUOTE=Noctilux]p.s. I still hope I am posting in the correct thread.
[/QUOTE]

Please start a new thread.  You'll find many threads about dual-screen if you look in the Video & Sound forum or do a search.

---

### Post by splater on 2005-12-29
I installed the drivers of my ATI mobility 9700 and everything seems to work more or less fine but when I type fglrxinfo: I have Mesa instead of ATI ...


Someone has an idea ?

Thx

---

### Post by mlomker on 2005-12-29
[QUOTE=splater]I installed the drivers of my ATI mobility 9700 and everything seems to work more or less fine but when I type fglrxinfo: I have Mesa instead of ATI ...[/QUOTE].

> 
All platforms: Review the /var/log/kern.log and Xorg.0.log files if you experience problems. Those two files contain all of the useful error messages for troubleshooting.


---

### Post by splater on 2005-12-29
I have these errors in Xorg.0.log ... but it doesn't talk to me .... :(((
PLease help !

Thx

```


(II) fglrx(0): UMM Bus area:     0xd85e9000 (size=0x03a17000)
(II) fglrx(0): UMM area:     0xd85e9000 (size=0x03a17000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *


```

---

### Post by mlomker on 2005-12-29
[QUOTE=splater][drm] failed to load kernel module "fglrx"
[/QUOTE]

The module doesn't exist, so the module-assistant steps must have failed.

---

### Post by mm2000 on 2005-12-29
Hello.

I bought a laptop yesterday, and was thinking about (k)ubuntu and XP in dual boot.
I installed kubuntu, and everything seemed to be just fine. Until I am going to start X... :(

"X" yields this messeges:
---------------------------------------------------------------------------------------------------------------------------
...
using config file "/etc/x11/xorg.conf"
skipping "/usr/x11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found
skipping "/usr/x11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o" No symbols found
skipping "/usr/x11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o" No symbols found

skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o"
(EE) RADEON(0) [dri] DRIScreenInit failed. Display DRI no symbols found

Fatal Server error:
Caught signal 4, server aborting 
-------------------------------------------------------------------------------------------------------------------------------

I have no clue what can be wrong, i have also disabled dri, but then I get another errormessege.
I tried to boot with knoppix live, and that worked just fine, so I dont know what to do...

For instance, can anybody tell if my graphics-card is supported in linux?
-> ATI Radeon Xpress 200M

I would be really glad if someone could help me with this problem. I am completly new to ubuntu.

---

### Post by Fibre on 2005-12-29
Ok I've had a go at your sticky, but because of my lack of knowledge. I've hit a brick wall.

I've tried to have a go of cube and i'm only getting 20fps instead of about 190 fps or so. 

The question I have is how can I now revert back to my old drivers that where installed by Ubuntu in the first place. I've gone wrong somewhere around the universal repository some things received errors when I tried to do it with out enabling universal whatever simply because I didn't know how to do it and it wasn't explained in detail enough for my experience with this system.

So it's probably easier for me just to re-install my old drivers - at least I will get my speed back with my ati card for gaming etc.

If you can help plz do.

---

### Post by ckthomson on 2005-12-30
[QUOTE=ckthomson]I. . . . see what my mobo mfr offers in the way of bios upgrades.
[/QUOTE]

Update on my plight : Have installed both the "included" breezy ATI 3d drivers and the proprietary package under fresh installs of Breezy.  The results have been the same : initially, sloid framerate on 3d apps, but suddenly my screen goes black and my monitor's power light flashes green. It's not going into power-saver, that's a flashing yellow light.

When it's in this state I am unable to even pop up the monitor's menu to see what's going wrong.  Also, on suggestion of a friend i tried setting my video ram by hand (128mb card).  Both 128000kb and 131072kb (1024x128) yield the same results.

In regards to the bios update, I am running v1.9 of my board's bios (AMIBIOS), with the newest available version being V2.0, which (according to my mobo MFR's site) only provides fixes for CPU support, and mentions nothing of Video Ram or Linux in general.

This is causing me no end of hassle, as I'd really like to have decent 3d support on my Ubuntu machine. As it is I may have to resort to trying another distro (not fun) or going back to windows (agony in a box).

---

### Post by splater on 2005-12-30
[QUOTE=mlomker]The module doesn't exist, so the module-assistant steps must have failed.[/QUOTE]

I think I did all the steps and did go well ... Here are the results of the module-assistant steps.

Do you se something strange ?
Thx

```

splater@acer:~$ sudo module-assistant prepare
Password:
Kernel headers available in /usr/src/linux

Done!

splater@acer:~$ sudo module-assistant update

Updated infos about 68 packages

splater@acer:~$ sudo module-assistant a-i fglrx
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2
modules/
modules/fglrx/
modules/fglrx/debian/
modules/fglrx/debian/changelog
^[[Amodules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/debian/rules
modules/fglrx/debian/control.template
modules/fglrx/debian/dirs.template
modules/fglrx/debian/postinst
modules/fglrx/agp3.c
modules/fglrx/agpgart_be.c
modules/fglrx/firegl_public.c
modules/fglrx/i7505-agp.c
modules/fglrx/nvidia-agp.c
modules/fglrx/agp_backend.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/drm_compat.h
modules/fglrx/drm.h
modules/fglrx/drm_os_linux.h
modules/fglrx/drmP.h
modules/fglrx/drm_proc.h
modules/fglrx/firegl_public.h
modules/fglrx/make.sh
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/Makefile


```

---

### Post by mlomker on 2005-12-30
[QUOTE=splater]Do you se something strange ?
[/QUOTE]

Not really.  Check to see if the module is there:

```

sudo updatedb
locate fglrx.ko

```

---

### Post by mlomker on 2005-12-30
[QUOTE=mm2000]I tried to boot with knoppix live, and that worked just fine, so I dont know what to do...
[/QUOTE]

Did you follow my how-to or are you using the default drivers?  Perhaps you should switch back to the default ATI drivers for now.

```

sudo dpkg-reconfigure xserver-xorg

```

Pick ATI from the list.

---

### Post by mlomker on 2005-12-30
[QUOTE=Fibre]So it's probably easier for me just to re-install my old drivers - at least I will get my speed back with my ati card for gaming etc.
[/QUOTE]

The command to switch back to the default ATI drivers are in the last post (547).  You can remove each of the how-to's DEB packages from Synaptic (if you installed them) and then reinstall the linux-restricted modules package.

---

### Post by splater on 2005-12-30
[QUOTE=mlomker]Not really.  Check to see if the module is there:

```

sudo updatedb
locate fglrx.ko

```[/QUOTE]

I put that code but I don't see anything ...

```

splater@acer:~$ sudo updatedb
Password:
splater@acer:~$ locate fglrx.ko
splater@acer:~$

```


As you see nothing happend ...

---

### Post by Gentleman on 2005-12-31
Please someone help me out, I think I'm almost there...
[http://ubuntuforums.org/showthread.php?p=607198#post607198](http://ubuntuforums.org/showthread.php?p=607198#post607198)

After a clean Ubuntu-installation I updated my system and started to get fglrx working. I added the needed modules to ect/modules (agpgart ati-agp drm and radeon) I followed the how-to ([http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584))

No luck... X starts up fine but fglrxinfo tells me I am running the mesa drivers. When i checkted the fglrx-module I get:
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/misc/fglrx.ko): Operation not permitted

What do I have to do to load the fglrx-module and enable DRI?? Somehow I think the restricted modules have something to do with my problem.

AMD sempron 3000+
Ati Radeon Xpress 200m

---

### Post by splater on 2005-12-31
I succeeded !!!! it works !! Peharps it can help you Gentleman as my problem seemed to be similar.

I went to /lib/modules/fglrx/ and put

```

sudo build_mod/make.sh
sudo sh make_install.sh

```

and restart Xserver and that's it !!! Peharps mlomker you can explain why I needed to do that for the others.

Thanks again mlomker for your help !!!

---

### Post by mlomker on 2006-01-01
[QUOTE=splater]and restart Xserver and that's it !!! Peharps mlomker you can explain why I needed to do that for the others.
[/QUOTE]

That was either left over from an older version of the driver or you used ATI's installer, which puts the files in different places.  We use to have to do that when installing 8.16.20 on a Hoary machine.  That directory does not exist if you follow this how-to starting from a clean installation of Breezy.

**fglrxinfo** should give you the driver version.

---

### Post by mlomker on 2006-01-01
[QUOTE=Gentleman]What do I have to do to load the fglrx-module and enable DRI?? Somehow I think the restricted modules have something to do with my problem.[/QUOTE]

You should start by removing those modules from /etc/modules--they aren't needed nor in the how-to.  The error message you're getting is because you're trying to load more than one video driver.

If you get MESA then you need to look in /var/log/Xorg.0.log and kern.log for errors.  95% of the time the issue is related to the system board.

---

### Post by cRoMo on 2006-01-03
Such errors like "[drm] failed to load kernel module "fglrx"" are due to the lack of fglrx module in /lib/modules, indeed. Surprisingly the xorg-driver-fglrx package provides Xorg module only, without the aforementioned kernel module...  this module is provided by linux-restricted-modules-2.6.15-10-686 (or similar, according to your kernel version) package that you need to apt-get install manually, because it is not on the dependencies list of xorg-driver-fglrx.

---

### Post by limit223 on 2006-01-03
[QUOTE=splater]I succeeded !!!! it works !! Peharps it can help you Gentleman as my problem seemed to be similar.

I went to /lib/modules/fglrx/ and put

```

sudo build_mod/make.sh
sudo sh make_install.sh

```

and restart Xserver and that's it !!! Peharps mlomker you can explain why I needed to do that for the others.

Thanks again mlomker for your help !!![/QUOTE]


 Glad it worked to you!! I used to patch the headers from that module in order to make the driver installed in a new version of kernel... In this way I discovered that I can install the driver right from the module.

Note: Just to remind to everyone this installation won't work if you're main kernel headers doesn't have -s link in /usr/src/linux (I mean you have to have a symbolic link for your main kernel header in /usr/src/linux)
And, of course, won't work if ati driver is not installed first ( the driver installes those modules headers in /lib/modules/fglrx )

---

### Post by mlomker on 2006-01-04
[QUOTE=cRoMo]package that you need to apt-get install manually, because it is not on the dependencies list of xorg-driver-fglrx.[/QUOTE]

The restricted-modules package is installed by default with the kernel.  The only people that wouldn't already have linux-restricted installed are those that installed a non-default kernel by not using the proper metapackage.  On my machine, for example, I installed **linux-image-k7**.

The fact that it is installed by default is the reason that it has to be removed in this how-to.  If you don't then Breezy's 8.16.20 driver is going to overwrite your newer driver at every boot-up.

---

### Post by goodchild on 2006-01-04
I searched this thread and I didn't see this problem, but my apologies if it has been answered before.

Specs:

Normal Ubuntu Install
Newest Kernel 2.6.15 (1/3/06) (configured using the distribution default kernel's config file)
CK Patch 1 (1/3/06)
InitNG .5 (12/24/05)
Xfwm4 4.2.2-1ubuntu3

ATi Radeon Xpress200M
xorg 6.8.2-77
Installed according to the companion HowTo of this thread:
1. fglrx-kernel-2.6.15-ck1
2. xorg-driver-fglrx 8.20.8-1


The Situation:

Everything boots fine, beautifully in fact (by that I mean fast, and with no errors according to syslog, kern.log, and every device, etc working exactly as it should).

When I logout, shut down, restart, or suspend, the system freezes.

What I've tried:

According to [this thread on xfwm4]("http://ubuntuforums.org/showthread.php?t=102875"), this can be caused by the new window manager.  However, I've tried the solution and it doesn't affect the problem at all.  It also doesn't seem to be consistent with that issue, as my machine seems to be hardlocking - i.e., the machine is apparently completely unresponsive (n.b. that I only am guessing at this, but some of the signs are there:  keyboard leds unresponsive, ctrl-alt-del nonfuntioning, totally blank screen).  Also, killing X with ctrl-alt-backspace provokes the same freeze.

[At this point, I basically have to hold down the power button to turn it off (and I hate doing that - I'm sure that I'm screwing up the machine by doing that)]

I though maybe this was a symptom of InitNG, but the precise problem also occurs with System V, so I can eliminate that as well.

So I finally settled on the driver as the problem (thus, posting here).

The fix I've found is to use the ```
Option "no accel"
``` in my xorg.conf file, and this seems to fix the problem.  Of course, this also defeats the purpose of installing new drivers.

Does anyone know anything about this?  Any fix, or anything ?  I've tried searching ATi's site, but the navigation is confusing and I haven't seen anything relevant.

---

### Post by heftigrat on 2006-01-04
I have a similar problem as **goodchild**, only worse.  My system boots, but when Xorg starts period the system freezes, then I have to hit the reset button and choose "recovery" boot mode, edit xorg.conf by changing "ati" or "fglrx" (depending on which How-To I'm reading ;) ) to "vesa", and <ctrl>+<d> to finish starting Ubuntu & X.  I have tried so many times I am ready to chalk this up to my mobo being a POS, so this is my last attempt.  Here are my specs:

Mobo by Jetway:
Integrated ATi Radeon 9200 Graphics Core (9100 Pro IGP)
ATi Radeon XPress 200
Realtek Audio

AMD Athlon64 3200+
512M Corsair DDR400

Does anyone have any ideas?

---

### Post by goodchild on 2006-01-04
[QUOTE=heftigrat]I have a similar problem as **goodchild**, only worse.  My system boots, but when Xorg starts period the system freezes, then I have to hit the reset button and choose "recovery" boot mode, edit xorg.conf by changing "ati" or "fglrx" (depending on which How-To I'm reading ;) ) to "vesa", and <ctrl>+<d> to finish starting Ubuntu & X.  I have tried so many times I am ready to chalk this up to my mobo being a POS, so this is my last attempt.  Here are my specs:

Mobo by Jetway:
Integrated ATi Radeon 9200 Graphics Core (9100 Pro IGP)
ATi Radeon XPress 200
Realtek Audio

AMD Athlon64 3200+
512M Corsair DDR400

Does anyone have any ideas?[/QUOTE]

That sounds like a biatch.  Maybe try the Option "no accel" as it seems to work for me and we have fairly similar configurations.  (btw, this will make it basically so that the driver sin't working, as when this option is present, fglrs info will report you're using mesa, ie not the radeon drivers.)

---

### Post by heftigrat on 2006-01-04
[QUOTE=goodchild]That sounds like a biatch.[/QUOTE]

Indeed it is.  But if I employ the "no accel" option it sounds like I shouldn't even bother installing the drivers at all.  But I'll give it a shot.  Thanks for your input!  :D

---

### Post by mlomker on 2006-01-05
[QUOTE=goodchild]
Newest Kernel 2.6.15 (1/3/06) (configured using the distribution default kernel's config file)
[/QUOTE]

Your machine is too far from stock for me to have any suggestions.  The odd numbered kernels are considered developer-only and buggy.  I'm not sure why you chose to go with that.

In any case, the lockups on shutdown are common and happen on my box once every couple of days.  I have no doubt that it's a driver problem, but you'll have to hit the Rage3D board to explore it further...it's not a Ubuntu issue afaik.

---

### Post by DarkDancer on 2006-01-05
Whenever I try to follow the instructions, Ubuntu breaks and I have to reload (says something about not being able to load x-server on reboot).

---

### Post by ph8 on 2006-01-06
I'm so happy about this how-to - i've been trying to get my X300 to work on my laptop for months and after following this howto it works:

henri@serenity:~/Desktop$ fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

Very happy indeed. All you need to do now is replace all the wrong how-to's that i've been following out there! The Wiki would be a good place to link/make the new home of this howto  the link i was using before this which didn't work was [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Cheers,

Henri

---

### Post by ph8 on 2006-01-06
<Delete This Please>

---

### Post by jscat on 2006-01-06
I had followed this how to with out any luck, but I recently got a new MB. I was also getting the mesa driver problem. The old MB would not boot into Ubuntu without using the irqpoll in the boot line. I don't know if anyone else is using this command when they boot, but it may have something to do with the problem. My old MB was a P4B800SE. Good luck and thanks for the how-to.

Joe

---

### Post by pijalu on 2006-01-07
[QUOTE=mlomker]The odd numbered kernels are considered developer-only and buggy. [/QUOTE]
FYI: You are mixing things, the odd numbering for unstable/dev was the 2nd nb (eg: 2.3.x , 2.5.x) not the third, and there is no "dev only" version of 2.6 (aka 2.7) yet - The latest "stable" kernel is 2.6.15 ... but sure it's a bleeding edge one

---

### Post by limit223 on 2006-01-07
[QUOTE=goodchild]
When I logout, shut down, restart, or suspend, the system freezes.
[/QUOTE]
That's true: hardlocking problem affect restart, shutdown, suspend function in my machine and this is known bug
[http://ati.cchtml.com/show_bug.cgi?id=251](http://ati.cchtml.com/show_bug.cgi?id=251)
 Even is already issued a [patch]("http://lkml.org/lkml/2005/12/11/26") apparently to solve for i386, 64bit, it didn't acutally work for my smp kernel. To keep 3D and not many problem with the new kernel the better idea is to go back to ver 8.18.8 unless you don't want to try the new feature dri for ATI cards in XOrg7.0(some reported successfully)
[QUOTE=goodchild]
What I've tried:

According to [this thread on xfwm4]("http://ubuntuforums.org/showthread.php?t=102875"), this can be caused by the new window manager.  However, I've tried the solution and it doesn't affect the problem at all.  It also doesn't seem to be consistent with that issue, as my machine seems to be hardlocking - i.e., the machine is apparently completely unresponsive (n.b. that I only am guessing at this, but some of the signs are there:  keyboard leds unresponsive, ctrl-alt-del nonfuntioning, totally blank screen).  Also, killing X with ctrl-alt-backspace provokes the same freeze.
[/QUOTE]
Switching in console, I don't thing is related to this bug, rather may be you ommited to compile the new kernel with the destinated modules for it: vesafb, fbcon... See my post here:
[http://www.ubuntuforums.org/showpost.php?p=632701&postcount=228](http://www.ubuntuforums.org/showpost.php?p=632701&postcount=228)

---

### Post by baalzamonbarnes on 2006-01-08
[QUOTE=DarkDancer]Whenever I try to follow the instructions, Ubuntu breaks and I have to reload (says something about not being able to load x-server on reboot).[/QUOTE]
I'm having this problem too.  After following the directions in the howto, xwindows fails to start.  Here's my Xorg.0.log file.  Anyone have any ideas?

```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux oreilly-notebook 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  7 23:56:21 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,24c0 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,24c0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,24c0 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,24c0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 8086,24c0 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,0149 rev 02 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 14e4,4d64 rev 02 class 07,03,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4c57 card 1028,0149 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 14e4,4401 card 1028,0149 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:02:0: chip 14e4,4320 card 1028,0001 rev 02 class 02,80,00 hdr 00
(II) PCI: 02:04:0: chip 104c,ac44 card 4000,0000 rev 02 class 06,07,00 hdr 82
(II) PCI: 02:04:1: chip 104c,8029 card 1028,0149 rev 00 class 0c,00,10 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[4] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[5] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf6000000 - 0xfbffffff (0x6000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 3: bridge is at (2:4:0), (2,3,6), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xe8000000/27, 0xfcff0000/16, I/O @ 0xc000/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
	[1] -1	0	0xfaffb800 - 0xfaffbfff (0x800) MX[B]
	[2] -1	0	0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
	[3] -1	0	0xfaffe000 - 0xfaffffff (0x2000) MX[B]
	[4] -1	0	0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
	[5] -1	0	0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
	[6] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[7] -1	0	0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000b080 - 0x0000b0ff (0x80) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[13] -1	0	0x0000bc40 - 0x0000bc7f (0x40) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[15] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[16] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[21] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[22] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
	[1] -1	0	0xfaffb800 - 0xfaffbfff (0x800) MX[B]
	[2] -1	0	0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
	[3] -1	0	0xfaffe000 - 0xfaffffff (0x2000) MX[B]
	[4] -1	0	0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
	[5] -1	0	0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
	[6] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[7] -1	0	0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
	[8] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[9] -1	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000b080 - 0x0000b0ff (0x80) IX[B]
	[12] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[13] -1	0	0x0000bc40 - 0x0000bc7f (0x40) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[15] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[16] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[17] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[18] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[21] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[22] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfaff4000 - 0xfaff7fff (0x4000) MX[B]
	[6] -1	0	0xfaffb800 - 0xfaffbfff (0x800) MX[B]
	[7] -1	0	0xfaffc000 - 0xfaffdfff (0x2000) MX[B]
	[8] -1	0	0xfaffe000 - 0xfaffffff (0x2000) MX[B]
	[9] -1	0	0xf4fff400 - 0xf4fff4ff (0x100) MX[B]
	[10] -1	0	0xf4fff800 - 0xf4fff9ff (0x200) MX[B]
	[11] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[12] -1	0	0xf4fffc00 - 0xf4ffffff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xfcff0000 - 0xfcffffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b080 - 0x0000b0ff (0x80) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[20] -1	0	0x0000bc40 - 0x0000bc7f (0x40) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[22] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000170 (0x1) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.16.20
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9550 (M12 4E56), RADEON 9500 (R300 4144),
	RADEON 9600 TX (R300 4146), FireGL Z1 (R300 4147),
	RADEON 9700 PRO (R300 4E44), RADEON 9500 PRO/9700 (R300 4E45),
	RADEON 9600 TX (R300 4E46), FireGL X1 (R300 4E47),
	RADEON 9800 SE (R350 4148), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), FireGL V3100 (RV370 5B64),
	MOBILITY RADEON X300 (M22 5460), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	RADEON X800 XL (R430 554D), RADEON X800 (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62)
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:15:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-206829
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

---

### Post by mlomker on 2006-01-08
[QUOTE=ph8]i was using before this which didn't work was [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
[/QUOTE]

It can't be posted to the Ubuntu wiki.  The Ubuntu wiki is only for programs that come with Ubuntu.  The 'latest' drivers (by definition) did not come on the Ubuntu CD's. 

These docs are already cross-posted to the unofficial ATI wiki and the forum docs (in my sig).

---

### Post by mlomker on 2006-01-08
[QUOTE=pijalu]FYI: You are mixing things, the odd numbering for unstable/dev was the 2nd nb (eg: 2.3.x , 2.5.x) not the third, and there is no "dev only" version of 2.6 (aka 2.7) yet - The latest "stable" kernel is 2.6.15 ... but sure it's a bleeding edge one[/QUOTE]

Thanks for the correction.  You're right, I was thinking about the middle digit.

Anyone running a custom kernel will have the best luck with finding answers on the [Rage3D forum]("www.rage3d.com/board/forumdisplay.php?f=88").  That's where the real hot-rodders (Gentoo users, etc) congregate.  This thread, and arguably most of the Ubuntuforums, are geared toward mainstream users.

---

### Post by mlomker on 2006-01-08
[QUOTE=baalzamonbarnes]I'm having this problem too.  After following the directions in the howto, xwindows fails to start.  Here's my Xorg.0.log file.  Anyone have any ideas?
[/QUOTE]

It's detecting a 7500 and they aren't supported by this driver:

```

(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xe8000000/27, 0xfcff0000/16, I/O @ 0xc000/8

```

My guess is that you have an IBM laptop.  They call it a Radeon 9000 but it really isn't.  IBM uses old video chips, even on their new machines.

---

### Post by nicky75 on 2006-01-08
I have a problem, when I used ubuntu 5.04 fglrx worked fine, now I have a problem with Tuxkart and cube (and other big games, not with simpler games), the moviments are ok, but I don't see well (it's all confused), I have a Hercules AIW 8500 DV :confused:

Tuxkart screenshot [IMG]http://static.flickr.com/38/83916970_04dcfec63e.jpg?v=0[/IMG]

---

### Post by fancyydk on 2006-01-08
Thank you for the great HOW-TO. Mine works perfect!

I have a Compaq V2000Z (V2312US to be specific). It has Turion64 ML-28 with ATI Xpress 200M. When I first found this HOW-TO, I followed the steps described and stumbled across many problems. After I installed the proprietary driver from ATI, fglrxinfo still gave me MESA instead of ATI. After two days of struggling, I found out my problem. The problem was that I downloaded the wrong driver from the ATI website. I clicked on the link that said "Notebooks with ATI Graphics" when I was supposed to choose "RADEON 8500 Series and higher." When I realized that I made this mistake, I reread the HOW-TO and started over with the "RADEON 8500 Series and higher" driver. And voila, everything works now.

I just wanted to share this since I know I am not the only one who would make stupid mistakes like this ;) And thanks again mlomker, for such a great HOW-TO.

---

### Post by hannahol on 2006-01-09
I have followed the How-To that has you generate the .deb files and everything seemed to work correctly. However I now get this message:

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

Whenever I try to run any command like glxgears, etc. I've checked and there are sym-links in all the right places (/usr/lib and /usr/X11R6/lib) that should take care of this. My kern.log and Xorg.0.log don't show any error messages or things not loading.

I am running a Mobility 9700 on Amd 64 bit architecture. Like I said everything seems to be detected correctly all the way through. Just that one error message above.

thanks,
brendan

---

### Post by ZarathustraDK on 2006-01-09
Ok, I'm having immense trouble getting my Ubuntu to use fglrx. I've tried nearly all the different how-to's on how to configure it for the latest ATI-drivers, but it just wont budge, it always uses the mesa-drivers when I check, and glxgears act weird (flowing smoothly at the beginning, but then come to a near hault after a few seconds).

My comp :
P4 3,2 GHz
1024 mb Kingston ram
Radeon 9600 TX graphics card (RV350) (the one from the famous Aldi-computers)
Asrock 775Dual-915GL motherboard

My xorg.conf :
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load "GLcore"
	Load	"glx"
	Load	"dri"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
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
	Identifier	"ATI Technologies, Inc. Radeon 9700 (RV350 NF)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"off"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"on"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  	Option 		"UseInternalAGPGART" 	"yes"

# You don't actually need this next BusID bit - unless maybe you have dual monitors?
# I've removed it from mine (single monitor only) and all is well.
# I think it's a leftover from fxglrconfig - doh!
	BusID		"PCI:1:0:0" 
EndSection

Section "Monitor"
	Identifier	"MD1998PB"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9700 (RV350 NF)"
	Monitor		"MD1998PB"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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



On a sidenote, I got this graphicscard to work under hoary, but of course I can't remember what just did the trick back then.

What am I doing wrong this time?

Hope some people with greater understanding of this than me will reply ;)  And don't be shy to demand other info if you need it.

---

### Post by ZarathustraDK on 2006-01-09
Ok I tried using the "dmesg | grep fglrx"-command, and I get :

> henrik@ubuntu:~$ dmesg | grep fglrx
[4294712.280000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies , Starnberg, GERMANY' taints kernel.
[4294712.284000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294712.284000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
[4294712.336000] [fglrx] ACPI power management is initialized.
[4294713.152000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294713.152000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294713.152000] [fglrx] Kernel AGP support doesn't provide agplock functionalit y.
[4294713.152000] [fglrx] AGP detected, AgpState   = 0x00000000 (hardware caps of  chipset)
[4294713.153000] [fglrx:firegl_unlock] *ERROR* Process 8143 using kernel context  0


Any guess as to what might be wrong?

---

### Post by ZarathustraDK on 2006-01-09
Tried looking through my font-libraries and the following fonts (libraries) are missing which the xorg.conf is referring to :

"/usr/lib/X11/fonts/cyrillic"
"/usr/lib/X11/fonts/Type1"
"/usr/lib/X11/fonts/CID"

Are they needed? And if so, where do I get them?

---

### Post by arxor on 2006-01-09
Thanks to mlomker!
I just killed gdm and reinstalled the driver then I got it worked!

arxor@newtype:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

Wish everybody goodluck!

---

### Post by fangorious on 2006-01-10
I followed the HOWTO and it worked just fine for me. I have an HP nw8240 with a Fire GL V5000. The range of resolutions and refresh rates I can select in Screen Resolution Preferences has stuff missing though. Under windows, I can have a refresh rate up to 100, I'd be fine with 75, but I only get one choice: 60. As far as resolution. As far as resolution goes, Screen Resolution Preferences only lists one widescreen resolution: 1920x1200. I would like to use 1680x1050 (which I use under Windows). These are the resolutions I have in my xorg.conf (for all color depths)

"1920x1440" "1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"

Here's the resolutions I can select in the Screen Resolution Preferences

"1920x1200" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "1920x1080"

No idea why 1920x1080 is listed after 640x480. Only one Modeline was put in xorg.conf, and I commented it out

#Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841

And I have the HorizSyn set to 31.5-91.1 and the VertRefresh set to 60-100 (per the HP documentation for installing Linux).

---

### Post by kevin_hill54 on 2006-01-10
Wow! what a great How-To

I followed that to the letter with the latest 8.20.8 ATI drivers.

Flawless install and perfect video.

Must test the fps.

Thanks for the help.

Kevin

---

### Post by Dark Damo on 2006-01-10
> damo@OMG:~$ sudo sh ./ati-driver-installer-8.20.8-i386.run --buildpkg Ubuntu/breezy
sh: ./ati-driver-installer-8.20.8-i386.run: No such file or directory

Why am i getting this error? I downloaded ito ff the site and have put itin its own folder. ATI drivers the folder is called. How can i change directory with that?

---

### Post by Dark Damo on 2006-01-10
EDIT:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

I'm fine now :) Thanks for the tutorial. Its awesome and works. I just need to learn how to pay attention to details.

---

### Post by mlomker on 2006-01-11
[QUOTE=hannahol]fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
[/QUOTE]

The file should be in /usr/lib, but it's easy to mess that up by removing/reinstalling the driver a bunch of times...especially if you have some failed attempts at installs.

You should double-check your /etc/ld.so.conf and run **sudo ldconfig** to make sure the right libraries are linking (assuming it's there but you're still getting the error).

```

mlomker@mlomkernote:~$ sudo updatedb
Password:
mlomker@mlomkernote:~$ locate libGL.so.1
/usr/lib/i686/mmx/cmov/libGL.so.1
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/libGL.so.1
/usr/lib/libGL.so.1.2
/usr/share/fglrx/diversions/libGL.so.1.2
mlomker@mlomkernote:~$ ldd /usr/bin/glxgears
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0x4705a000)
...

```

---

### Post by mlomker on 2006-01-11
[QUOTE=nicky75]I have a problem, when I used ubuntu 5.04 fglrx worked fine, now I have a problem with Tuxkart[/QUOTE]

I can't help you with that--that's a driver problem and not an installation issue.  You could try starting another thread or searching on the Rage3D forum.  I don't play games, myself.

---

### Post by mlomker on 2006-01-11
[QUOTE=ZarathustraDK][4294713.153000] [fglrx:firegl_unlock] *ERROR* Process 8143 using kernel context 0[/QUOTE]

There are a variety of causes for that error and most of them are hardware-related.  The motherboard/video card/BIOS combination isn't working together.  You could try an older version of the driver or do some searches on "firegl_unlock using kernel context" on Google.  I'm not aware of any consistent solution.

---

### Post by mlomker on 2006-01-11
[QUOTE=fangorious]
#Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
[/QUOTE]

I'm trying to limit this thread to just the driver install and not related issues.  There are some how-to's for [refresh rate.]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by thefool on 2006-01-11
Finally got ATI drivers to work... here are some of the errors i had and how i fixed them:

Black / Blank Screen and Freeze Up (when starting Xwindows) even tho DRI loads:

Xorg.0.log: 
(II) fglrx(0): DRI initialization successfull!
and/or
kerl.log
agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode

Try Changing AGP multiplier  from 8x to 4x to 2x or 1x in BIOS


Error 02:  kern.log Mtrr Addressing error:

Try adding into xorg.conf under Device:
# === misc DRI settings ===
# disable DRI mtrr mapper, driver (fglrx) has its own code for mtrr
    Option	"mtrr" "off"  

Hope that helps some ppl

---

### Post by nilly on 2006-01-12
[QUOTE=thefool]Finally got ATI drivers to work... here are some of the errors i had and how i fixed them:

Black / Blank Screen and Freeze Up (when starting Xwindows) even tho DRI loads:

Xorg.0.log: 
(II) fglrx(0): DRI initialization successfull!
and/or
kerl.log
agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode

Try Changing AGP multiplier  from 8x to 4x to 2x or 1x in BIOS


Error 02:  kern.log Mtrr Addressing error:

Try adding into xorg.conf under Device:
# === misc DRI settings ===
# disable DRI mtrr mapper, driver (fglrx) has its own code for mtrr
    Option	"mtrr" "off"  

Hope that helps some ppl[/QUOTE]


So you got it up and running.. i have the same black screen/crash issue, as alot of us i guess.. i have a PCI-E X800XL so i cant change any agp settings in bios. i have an nforce4 motherboard with a Amd64 dualcore cpu.. and the X800 is an Asus with 512mb XL.. everything runs fine, and DRI starts up, no errors whatsoever in fglrx.log.. 

any tips?? anyone got it running on similar specs??

EDIT: Do i need any extra drivers, nforce drivers etc??..
The motherboard is Abit AX8SLI with nforce4, cpu AMD64 4200+ Dualcore.. gfx: Asus X800XL 512mb..

Anyone with Abit AX8SLI?
//nilly

---

### Post by Nailor on 2006-01-15
Don't know if it's mentioned allready, but I'll tell it anyway:

If you find errors in Xorg-log like
```

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"

```

Make sure your agp-modules have been loaded correctly. Do:

```

lspci | grep AGP
lsmod | grep agp

```
 
In my case the output is:
```

$ lspci | grep AGP
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
$ lsmod | grep agp
nvidia_agp              8412  1 
agpgart                34888  2 nvidia_agp,fglrx

```

Before I got all working lsmod showed only fglrx in the agpart-section. All I needed to do was load manually my agp driver using modprobe, eg.
```

sudo modprobe nvidia_agp

```

You can find out the different possible agp drivers by doing
```

ls /lib/modules/`uname -r`/kernel/drivers/char/agp

```

And remember to add the correct AGP-module to /etc/modules too! After loading module just restart X by pressing ctrl+alt+del.

Works like a charm now :)

---

### Post by mlomker on 2006-01-15
[QUOTE=nilly]and DRI starts up, no errors whatsoever in fglrx.log.. 
[/QUOTE]

The two log files are /var/log/Xorg.0.log and kern.log.  

The black screen issue could be because the driver is misdetecting the resolution/refresh rate of your monitor (which is logged in the Xorg.0.log file).  If that's the case then a modeline in your xorg.conf file might solve it.

---

### Post by rutger83 on 2006-01-20
Yesterday I downloaded the new ati drivers (ati-driver-installer-8.21.7-x86_64.run) and they work without the libdri.a downgrade. I also haven't had any problems with random crashes anymore, so I guess it worked thanks to this howto. (respect for you mlomker). :D :D

But I don't know wether HW acceleration is working. How can I check this, because the ati-config control panel doesn't work (as some/all of us know). The screensavers have pretty low fps.

Also the fglrxconfig doesn't work anymore, so I used a previous version of xorg.conf. Should I have installed more of the .deb files? I only installed the three of this howto, but there are also a fglrx-dev and a kernel-source installer. :confused: 

Thanks for the help and this great howto! ;)

---

### Post by zenlakin on 2006-01-20
in response to Burok's post #69. Is that instructions for getting the drivers installed for the 32 bit version or does it also work for the 64 bit version? I am able to get X to start if I edit my xorg.conf file and set no accel="True" But if it is set to no X won't start, I just get a black screen. And also when doing a fglrxinfo it is showing up as the mesa drivers still. Any ideas guys? Also I am very new to linux so I am just learning all of this stuff.

---

### Post by diffuser78 on 2006-01-20
That was helpful

[QUOTE=zenlakin]in response to Burok's post #69. Is that instructions for getting the drivers installed for the 32 bit version or does it also work for the 64 bit version? I am able to get X to start if I edit my xorg.conf file and set no accel="True" But if it is set to no X won't start, I just get a black screen. And also when doing a fglrxinfo it is showing up as the mesa drivers still. Any ideas guys? Also I am very new to linux so I am just learning all of this stuff.[/QUOTE]

---

### Post by RickKnight on 2006-01-20
I've followed this howto but I cannot get the ATi drivers to install correctly. The fglrx kernel module is not building. I've also tried installing the ati-driver-installer directly with the same result. The ati driver does work, but no acceleration due to no kernel module.

Here's the build log from the ati-driver-installer```
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.12-hybernate/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_init':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8173: warning: `pm_register' is deprecated (declared at include/linux/pm.h:106)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: In function `__fgl_agp_cleanup':
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:8183: warning: `pm_unregister_all' is deprecated (declared at include/linux/pm.h:116)
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/agpgart_be.c:6077: warning: 'ati_gart_base' defined but not used
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:579: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:581: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:565)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:601: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:564)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:632: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `fglrx_pci_suspend':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:696: error: invalid operands to binary ==
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:715: error: incompatible types in assignment
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `fglrx_pci_resume':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:729: error: invalid operands to binary ==
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:744: error: invalid operands to binary ==
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:747: error: incompatible types in assignment
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:758: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3509: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3510: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3511: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3512: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3513: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3514: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3515: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3516: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3518: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3528: warning: function declaration isn't a prototype
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `test_inter_module_interface':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3594: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3600: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:568)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_allocate_memory_phys_list':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3858: warning: passing arg 3 of pointer to function makes integer from pointer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_bind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3897: warning: passing arg 1 of pointer to function from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_unbind_memory':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3910: warning: passing arg 1 of pointer to function from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2148: warning: 'deferred_flush' defined but not used
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.
sforwk@w43wxp121:/usr/share/fglrx$
```
I'm running Kubuntu-5.10 with a full kubuntu patched kernel.

Any help?

Thanks, Rick Knight

---

### Post by andreizinca on 2006-01-20
Hello.
I have tried many ways of installing this bloody driver. No luck for me.

I have read that others with a Sapphire Atlantis Radeon 9600 have same problems as I do.

lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4e51
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4e71

sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/misc/fglrx.ko): No such device

I don't know what I should do in order to get some acceleration ? Maybe buy an NVidia ?

Thank you!

---

### Post by RickKnight on 2006-01-20
andreizinca,

Take a look at /usr/share/fglrx/fglrx-install.log. See if you have the same error I get.

Rick Knight

---

### Post by DMorton3 on 2006-01-21
andreizinca,

I am getting the same modprobe message as you with the 8.21 driver....for your unknown ATI device have you tried "sudo update-pciids" ?

---

### Post by andreizinca on 2006-01-21
[QUOTE=RickKnight]andreizinca,

Take a look at /usr/share/fglrx/fglrx-install.log. See if you have the same error I get.

Rick Knight[/QUOTE]

Hello Rick.

I have this message.

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.

I don't know why I have this message as I think I have built the kernel correctly.

---

### Post by andreizinca on 2006-01-21
[QUOTE=DMorton3]andreizinca,

I am getting the same modprobe message as you with the 8.21 driver....for your unknown ATI device have you tried "sudo update-pciids" ?[/QUOTE]

I think it detects it now..

sudo update-pciids
lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600]
0000:01:00.1 Display controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600] (secondary)

Thank you very much.

I will try now installing once again the fglrx driver.

I have tried 8.21 , 8.20 , now 8.16 (official in Breezy) and nothing

andrei@andreiz:~$ dmesg | grep fglrx
[4294765.735000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294765.739000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294765.739000] [fglrx:firegl_init] *ERROR* Device not found!

andrei@andreiz:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=1
reg02: base=0xc0000000 (3072MB), size= 128MB: write-combining, count=1

andrei@andreiz:~$ sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/volatile/fglrx.ko): No such device

andrei@andreiz:~$ sudo lspci -v
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited: Unknown device 0200
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 3
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at a000 [size=256]
        Memory at e9030000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

0000:01:00.1 Display controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600] (secondary)
        Subsystem: PC Partner Limited: Unknown device 0201
        Flags: 66MHz, medium devsel
        Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at e9020000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2

---

### Post by andreizinca on 2006-01-21
I have added the following line in Device

ChipID 0x4E50

and xorg loads now (without Direct rendering).

Still,
andrei@andreiz:~$ fglrxinfo
display: :0.0  screen:0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Xorg log says:

(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!
(WW) fglrx(0): * (maybe driver kernel module missing or bad)
(WW) fglrx(0): * 2D acceleraton available (MMIO)
(WW) fglrx(0): * no 3D acceleration available
(WW) fglrx(0): ***********************************************

---

### Post by Jay_Dogg on 2006-01-21
A good howto, this works with the new 2.81.7 driver as well. :D

Thank you, let's try Quake 4.

---

### Post by rippon on 2006-01-21
I installed usuing this how-to (on the newest driver version though) and I am getting 8500 FPS consistantly in glxgears, and that transfers to about 30-60 FPS in Americas Army on Medium - High Settings with my x800pro.

Happy enough.
(Is 8500fps in glxgears good?)
Thanks.

---

### Post by newclique on 2006-01-23
I am having ATI (AGP) problems on my K7 machine as well. Should I start a new thread or just jump into this one? I have tried both a 9250 and an 8500 in new installs of breezy badger and I get basically the same issue in both. I tried the latest drivers from ATI on the 9250, traced all the softlinks, etc. but to no avail. I just get garbage on the screen (usually) and a lockup if I load glx. Could it be my frame buffer? I want to try the VesaFB but I'm not sure how to activate it.

Thanks.

---

### Post by Nailor on 2006-01-23
[QUOTE=newclique]I am having ATI (AGP) problems on my K7 machine as well. Should I start a new thread or just jump into this one? I have tried both a 9250 and an 8500 in new installs of breezy badger and I get basically the same issue in both. I tried the latest drivers from ATI on the 9250, traced all the softlinks, etc. but to no avail. I just get garbage on the screen (usually) and a lockup if I load glx. Could it be my frame buffer? I want to try the VesaFB but I'm not sure how to activate it.
[/QUOTE]

Shouldn't the 9250 work just fine (even faster) with the open source radeon drivers? At least composite should be available with those.

---

### Post by newclique on 2006-01-23
[QUOTE=Nailor]Shouldn't the 9250 work just fine (even faster) with the open source radeon drivers? At least composite should be available with those.[/QUOTE]
I can only get the cards (either of them) to work in 2D (no 3D accel). I did manage at one time through pointing all of the softlinks for the GL libraries to the /usr/share/fglrx... .xlibmesa library to get the 9250 into X without blowing up but it still reported that GL was being done in software.

I guess my question would be this: If two cards using different driver versions (both with completely fresh breezy installs) both exhibited garbage on screen (like the video ram was not being accessed correctly - some pixels survived a warm boot) would that indicate that in breezy install was identifying my hardware incorrectly? I've spent about 40 hours on this because I really want to understand the whole ati driver setup process and I've really eliminated everything in my mind except a very low-level hardware driver like the AGPGART or something. I just do not know how to try something else on that level. Can I do a make menuconfig or does this version of linux have some other way of building? I want to literally select different combinations of hardware for the kernel to see if that is the problem.

Thanks.

---

### Post by mlomker on 2006-01-23
[QUOTE=krul]After deinstalling the driver the screen looks normal again.
[/QUOTE]

You'll want to check the Rage3D forum.  I've heard sporatic complaints from people about 'gamma' problems and I imagine that's what you're seeing.

---

### Post by krul on 2006-01-23
I have tried the ATI driver (Version 8.21.7), but after restarting my desktop, the screen looks terrible. It seems that the brightness is way too high. I really don't no if the driver doesn't works for me, or that it is just some configuration issue.:confused: 
After deinstalling the driver the screen looks normal again.

I have a ATI Radeon 9200SE.

---

### Post by aerials on 2006-01-24
Somehow I got my setup messed up:

I own a laptop and yesterday I was suddenly in the need for a wireless connection (in an internet cafe), but I figured out, that there was no device present for my wireless card (atheros chipset).
At home I figured out, that I didn't have the restricted modules installed. I quickly installed them, rebooted and there was my ath0 wireless device :)

But this morning when I boot up at school, I remark a white stripe of approx 80x5 pixels wandering around on my screen, a few pixels under my mouse pointer. 

I suspect a graphics problem and have a look at my Xorg.0.log where I find the following error:

> (II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d30000 at 0xb7b21000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

fglrxinfo output now suddenly gives me a mesa vendor string.

In fact, I have the fglrx driver 8.19.10 installed and working properly (that's why I hesitate to update). 
That 8.16.20 module must have come with the restricted modules I installed yesterday. How do I remove this module and keep my wireless device working which depends on restricted modules?

thx for any advice

---

### Post by Pancetilla on 2006-01-24
Got fed up with my Ati Radeon 9600 XT and its drivers. Subtitles in xine have disappeared since 8.16, totem doesn't even start and now KDE 3.3 crashes on my debian 3.1 whenever I log out...This afternoon I will buy a Nvidia 6200. It may be worse than my actual graphic card, but it is cheap and I will see if Nvidia is as problematic in my PC as ati. I've been struggling a year or so with Radeon, but I can't take anymore.

---

### Post by Gentleman on 2006-01-24
Can someone confirm me these new drivers work with the ati xpress 200m? (without uma enabled - was necessary with the 20.8 drivers)

---

### Post by DMorton3 on 2006-01-24
Ok. I tried 3 times to get this new ATI driver to work only to keep getting device not  found and crash.  My video card is an ATI Radeon X850 pro which according to the ATI release note is supported it finds the device on PCI 1:0:0, but sees another device ( same device ) on PCI 1:0:1....I will duplicate the crash and post my xorg log.  Any help is appreciated.  I am new to linux and seem to be learniing quickly thanks to ATI, but I'd like to move on to other aspects of the os.

From Xorg
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X850 PRO (R480 5D4F), RADEON X850 XT (R480 5D52),
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.21.7
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.21g1                           
(II) ATI Proprietary Linux Driver Build Date: Jan 14 2006 16:26:15
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.21.1-driver-lnx-238868
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found
lspci says
0000:01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]  4b4b
0000:01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850Pro] (Secondary) 4b6b

Any ideas why my hex doesn't equal their hex?

---

### Post by Pancetilla on 2006-01-24
It seems that actually X850 is NOT supported by the driver, whatever the liner notes say:

[rage3d forum]("http://www.rage3d.com/board/showthread.php?t=33842136&page=2")

---

### Post by rutger83 on 2006-01-24
I can, as I posted earlier these drivers work well for me. I have an onboard xpress 200 and I haven't had any problems anymore. I didn't have to disable anything

---

### Post by deadprez on 2006-01-24
Hi all. I have followed the instructions in the fglrx howto and installed 8.21.7 driver:
```
martin@bonk:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.5582 (8.21.7)
```

However, 3d acceleration dont seem to be working properly (it is extremely slow)

```
martin@bonk:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
3070 frames in 5.0 seconds = 614.000 FPS
3629 frames in 5.0 seconds = 725.800 FPS
3654 frames in 5.0 seconds = 730.800 FPS
```

People earlier in this thread said they are getting several thousand fps with this one? (I have 1024+256mb ram, amd athlon 2800+ cpu). tuxkart does appear to run 3d accelerated, but i get like 1fps or less when I try to run games thru cedega or wine.

I had the same results with the 8.20.8 driver.

/var/log/kern.log says (can this be the problem?):
```
Jan 24 13:43:27 localhost kernel: [4294707.843000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Jan 24 13:43:27 localhost kernel: [4294707.843000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Jan 24 13:43:27 localhost kernel: [4294707.843000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
```

Also, just doing things like creating a big  selection with the cursor on the desktop in gnome creates noticeable UI lag

---

### Post by jlynaugh on 2006-01-24
Thank you mlomker
I was about to give up on getting my video card working on my laptop.
I found your  "how-to:ATI fglrx driver latest version" - followed it to the letter(even though I had no clue what I was doing) and it worked!!! Thank you very much.

I have a gateway with AMD Turion64, ATI radeon xpress 200m, and a broadcom 
wifi chipset. I am a total newbie to linux - got the wifi working with ndiswrapper(that was an adventure to)-now I can actually start using the computer:D 

To anyone else struggling to get their system up-keep trying-there is alot of good info in the forums-if i can do it anyone can

joel

---

### Post by mlomker on 2006-01-24
[QUOTE=aerials]How do I remove this module and keep my wireless device working which depends on restricted modules?
[/QUOTE]

You need to compile the Madwifi drivers (there are other how-to's on the board for that).  The bottom of my how-to had a workaround for that driver that had worked for other people, but I don't have that card and can't test it.

---

### Post by mlomker on 2006-01-24
[QUOTE=Gentleman]Can someone confirm me these new drivers work with the ati xpress 200m? (without uma enabled - was necessary with the 20.8 drivers)[/QUOTE]

I'd recommend asking on the Rage3D board.  I'd like to keep this thread related to the install--this thread is too long already.

---

### Post by mlomker on 2006-01-24
[QUOTE=DMorton3]Any ideas why my hex doesn't equal their hex?[/QUOTE]

You'll find a [number of threads]("http://www.rage3d.com/board/showthread.php?t=33834517") about this on the Rage3D board.  You'll have to edit the driver file to add your hex.  That's outside of the scope of this howto.

---

### Post by mlomker on 2006-01-24
[QUOTE=deadprez]Also, just doing things like creating a big  selection with the cursor on the desktop in gnome creates noticeable UI lag[/QUOTE]

Slower 2D is a known problem with fglrx.  Your other issue is probably motherboard-related.  You could look in your kern.log to verify the speed of your AGP bus.

```

mlomker@mlomkernote:$ dmesg | grep AGP
[4294735.784000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

```

I'd recommend doing some Google searches to see if anyone else has run across an issue with your motherboard model and/or update the BIOS.

---

### Post by cor2y on 2006-01-24
Hi, followed the guide step by step.
Got the latest drivers to work.
However I lost xv , xine and mplayer have begun complaining and my video preferences have lost xv.

---

### Post by cmac on 2006-01-24
Your instructions on downloading the latest drivers from ATI and getting them up and running were right on. Thanks!

---

### Post by Fisslefink on 2006-01-25
Success!  Finally!

I have struggled with mlomker's [HOWTO]("http://ubuntuforums.org/showthread.php?t=78466"), but it's not mlomker's fault -- he did a great job, and his is absolutely the best tutorial I could find on the subject.



So, here's my story, with the hopes that someone will google it and be helped by it, or at least encouraged:



Hardware
------------
Motherboard:  Asus P4P800-E Deluxe
Video Card:  Rosewill ATI 9600SE 128Mb
RAM:  1024Mb




Attempt #1:  Kubuntu Hoary dist-upgraded to Breezy
--------------------

I followed mlomker's HOWTO exactly, and it did not work because module-assistant gave me a "kernel not configured" error.  

I discovered that the kernel sources were not properly linked (If you get this error, do an "ls -la" in your /usr/src/linux directory).  There were plenty of broken links, visible in red text in the terminal.  Some of them seemed to be circularly linked back to themselves!  

Apt-get installing new kernel headers and sources did not matter, and I could not "configure the kernel" using anything like "make menuconfig" because it returned "no makefile" type errors.  Frustrated, I reinstalled from scratch.  Perhaps someone with more kernel-compiling knowledge could have sorted out that mess, but I gave in.



Attempt #2:  Fresh installation (brand spanking new) of Breezy 5.10
 -------------------

Having walked down this road once before, I knew before I even started the HOWTO that I would to have to contend with this error eventually:

```
# dmesg|grep mtrr:
mtrr: type mismatch for e8000000,8000000 old: write-back new: write-combining
```

Nonetheless, I followed this HOWTO exactly, and had no trouble with module-assistant.  The install seemed to have worked flawlessly!  What a relief! 


After installing the drivers, I rebooted, hoping that it would "just work" (and it did not), I checked again for errors.

I ran:
**grep WW /var/log/Xorg.0.log** #and
**grep WW /var/log/Xorg.0.log** #and
**dmesg|grep mtrr**

The output confirmed that my card was being recognized, but the AGP port was not starting up correctly, so DRI was failling (I got the EINVAL error described elsewhere).

**fglrxinfo** showed that I was using Mesa drivers (boohoo)


I suspected mtrr was the problem, because of this line:

```
cat /proc/mtrr
 reg00: base=0x00000000 ( 0MB), size=984064MB: write-back, count=1
```
That's bad -- I don't have 1TB of memory.  MTRR is overlapping the video memory space, so nothing can be written there.  

To fix it, I first tried adding **video=vesafb:nomtrr** to my kernel line in /boot/grub/menu.lst, but that did not help.

```
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/sda5 ro quiet splash video=vesafb:nomtrr
```


So, I removed the "video=vesafb:nomtrr", and instead followed the HOWTO here:

[URL="http://ubuntuforums.org/showthread.php?t=115104"]
 General - HOWTO: ATI fglrx MTRR error fix[/URL]
That script did not work, for some reason, but it could have been a typo on my part.  Some more googling turned up this script, which is a bit more thorough:


```


#Paste this code block into a Konsole, hit Enter, and type in your password
#It wraps all the important commands up in a boot script:
sudo cat <<eof >/tmp/fix_mtrr
#!/bin/sh
# Combine all main memory mtrr ranges into a single register
echo "disable=0" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=2" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr
echo "disable=5" >| /proc/mtrr
echo "disable=6" >| /proc/mtrr
echo "base=0 size=**0x40000000** type=write-back" >| /proc/mtrr **#NOTE: Use 0x40000000 if you have 1GB of system memory, 0x80000000 if you have 2GB, 0x20000000 if you have 512Mb, 0x10000000 if you have 256Mb, and 0x08000000 if you have 128Mb, etc.**
eof
```
Note:  If you run these commands separately (not in a script), you will find that the computer gets reallllllly slow.   That's OK!  Keep going!

```

#Then run these commands separately:

sudo chmod +x /etc/init.d/fix_mtrr

cd /etc/rcS.d

sudo ln -s ../init.d/fix_mtrr S03fix_mtrr


```
Just remember to "chmod +x" the new file, as I have written above!  That nearly got me.  Test the script once to make sure it works, by running:
```
sudo /etc/init.d/fix_mtrr #to initialize the memory
cat /proc/mtrr. #to check the new settings

```

If you haven't rebooted, you should get something like
```
**cat /proc/mtrr**
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
```

After a reboot, you should get something different:
```

**cat /proc/mtrr**
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=5
reg02: base=0xf0000000 (3840MB), size= 128MB: write-combining, count=1
```

The script adds a few noticeable seconds to my boot time, but on the first reboot, fglrx worked like a charm!

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 2.0.5582 (8.21.7)
```


I wish you better luck than I had, but remember, it **can** be done!


Now for some tuxracer....

Fisslefink

---

### Post by yyagol on 2006-01-25
At last i understand what was my problem
Now i come to a new problem
with the help of **Fisslefink** and **mlomker** i manage to load fglrx
everything looks good but its not working good. i still have the bright screen
just like the fglrx is not loaded at all .
cat /proc/mtrr  gave this
```
reg00: base=0x00000000 (   0MB), size= 512MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=4
reg02: base=0xf0000000 (3840MB), size=  64MB: write-combining, count=1
```
lsmod | grep fglrx gave this
```
fglrx                 255524  7 
agpgart                34792  2 sis_agp,fglrx
```
dmesg | grep fglrx    gave me that
```
[4294693.341000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294693.345000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294693.346000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294825.012000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294825.012000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294825.012000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294825.012000] [fglrx] AGP detected, AgpState   = 0x1f004e1b (hardware caps of chipset)
[4294825.015000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[4294825.024000] [fglrx] free  AGP = 54800384
[4294825.024000] [fglrx] max   AGP = 54800384
[4294825.024000] [fglrx] free  LFB = 122679296
[4294825.024000] [fglrx] max   LFB = 122679296
[4294825.024000] [fglrx] free  Inv = 0
[4294825.024000] [fglrx] max   Inv = 0
[4294825.024000] [fglrx] total Inv = 0
[4294825.024000] [fglrx] total TIM = 0
[4294825.024000] [fglrx] total FB  = 0
[4294825.024000] [fglrx] total AGP = 16384

```
dmesg | grep mtrr  shows this after reboot
```
[4294683.778000] mtrr: MTRR 1 not used
[4294683.784000] mtrr: MTRR 2 not used
[4294683.791000] mtrr: MTRR 3 not used
[4294683.797000] mtrr: MTRR 4 not used
[4294683.804000] mtrr: MTRR 5 not used
[4294683.810000] mtrr: MTRR 6 not used
```
and the fglrxinfo shows that fglrx is well loaded
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)
```

now what is wrong ....i looked at the Xorg.0.log but ther are no errors
with no errors it is hard to understand the problem 
any idea ??

---

### Post by jimbo2150 on 2006-01-25
So far I have tried EVERYTHING that I could find (in the way of HOWTOs), and NOTHING has worked. I am a little disappointed, but guess I can live without 3D for a while. I hope this is fixed in Dapper (if it is an OS problem). FYI, I have the ATI X800.

Every time I change "ati" to "fglrx" it crashes X Window when loading Ubuntu and throws me to the text prompt (shows me a whole bunch of debugging info that for me means nothing since it does not seem to point out any one problem that is correctable).

I have uninstalled old drivers, installed ATI's new ones, tried the extra drivers in synaptic, and also tried most settings using each driver (in xorg.conf). Nothing worked.

At this point I assume that it is either a problem with compatability, a particular missing or wrong setting in xorg.conf, or the new driver is useless (which is what many have posted).

---

### Post by mlomker on 2006-01-26
[QUOTE=cor2y]However I lost xv , xine and mplayer have begun complaining and my video preferences have lost xv.[/QUOTE]

I'd recommend posting in the desktop forum about that.  I don't run gnome and I haven't had any issues with Kaffeine.  fglrx does have worse 2D performance but that's how it is.

---

### Post by mlomker on 2006-01-26
[QUOTE=yyagol]i manage to load fglrx
everything looks good but its not working good. i still have the bright screen
just like the fglrx is not loaded at all .[/QUOTE]

How are you getting the fglrxinfo output if you cannot get to a desktop?  What do you mean by *bright screen*?  If you're having a gamma issue then I'd recommend searching on the Rage3D board.  That's probably a driver problem and something that ATI would have to resolve.

---

### Post by mlomker on 2006-01-26
[QUOTE=jimbo2150]At this point I assume that it is either a problem with compatability, a particular missing or wrong setting in xorg.conf, or the new driver is useless (which is what many have posted).[/QUOTE]

You need to look in the error logs if want to figure it out and you don't mention having done that--even with a black screen it'll create the logs and you can Ctrl-Alt-F2 over to a console to look at them. 

There are a lot of issues related to the X800, such as the chipID not being recognized.  It's a case of the card being newer than the driver is.  The linux driver is always a generation behind the Windows driver.

---

### Post by Bandit on 2006-01-26
Hello Everyone,
I may have already missed the solution to this problem. This topic is looonngg.. :)

Well anyway. I have a Diamond S80 Radeon 9200SE (RV280) 128MB.
I have the 3D working after removing init10 from xorg.conf, but when using GLXGears or testing out my screen saver it works fine for the first 2 to 3 seconds and then gears or the screen saver start shuttering (shakeing) horribly. As per x.org the 6.8.2 ati drivers are supposed to support 3D up the the 9200 series @ 4xAGP. I have everything optimized best I can (DRI, AGPMode, etc..), but it still shakes like a 7.0 earthquake.
I used it in SuSE and it worked smoothly, not a speed deamon, but it worked.
But SuSE 10 is about as stable as windows.. 
So I quickly put Ubuntu back on my system :)

Here are my system specs:
Ubuntu Breezy 64bit.
Kernel 2.6.15.1-stardust2, Vanilla kernel I compiled last night..
Xorg 6.8.2, default Ubuntu.
AMD64 3000+
Diamond S80 Radeon 9200SE (RV280) 128MB DDR, 64bit. (DVI-D output)
2GB DDR400
Biostar K8M800-M7A mATX mobo.
380w Coolermaster P.S.
*other specs shouldnt matter...*

If anyone could point me in the right direction I would appriciate it.

Thanks,
Joey

---

### Post by mlomker on 2006-01-26
[QUOTE=Bandit]I used it in SuSE and it worked smoothly, not a speed deamon, but it worked.
[/QUOTE]

It is an old card, but I really can't help beyond installing the driver.  I do not recommend running 64-bit on a game machine.  All of the 64-bit code is more buggy than the 32-bit and you'll run into all kinds of compatibility problems wrt various libraries.

If fglrxinfo shows ATI and glxgears is above 1000 fps then there's probably a software bug somewhere.  You could try the Rage3D forum but I'd recommend giving 32-bit a try.

---

### Post by Bandit on 2006-01-26
Its a Radeon 9200SE, I just purchased it last week becuase I got sick of nVidia card crashing 6 times a day.
I know nVidias are faster for linux and better, but until 6.04 comes out I thought the Radeon would be better for a few months.
I am a huge stability nut, I dont like anything that crashes :)

Anyway, I just trying to figure out why it shuttering..
Do you think the rage3D forum would be better since its a Radeon 9200?

Thanks,
Joey

---

### Post by mlomker on 2006-01-27
[QUOTE=Bandit]Anyway, I just trying to figure out why it shuttering..
Do you think the rage3D forum would be better since its a Radeon 9200?
[/QUOTE]

That's the unofficial [ATI support forum]("www.rage3d.com/board/forumdisplay.php?f=61").  Developers are there and other people a lot smarter than I am (the Gentoo guys come to mind).

---

### Post by DazarGaidin on 2006-01-31
Hello, I have a radeon 9250.  Ubunto installs the driver for 9200 instead which allows me to do most things, except play my game (nwn).  The same thing happened in windows, where i of course just downloaded ctalyst driver and it updated the driver to 9250.  

Clearly this cant be done so easily on linux, so i try this how to.  I am a linux newbie and i think i messed something up.  Some errors were thrown such as (not installed) when i did the first few commands.   (sorry i cnt copy and paste the exact errors as i reinstalled unbuntu).  If i forged ahead i get file not found on some of the things etc.  

Now, if i have fresh install of unbuntu and its reading my card as a 9200, what do i do to get to step one of the tutorial.  Please be specific.  What directory should i be running those commands from?  What directory should i put that sources file he gives (do i have to use that)?  

After trying this tutorial with those erors etc, afterward i couldnt open synaptic it hit me with tons of errors  so i dont want to make the same mistake again.  

I dont want people to rewrite the tutorial for me ins tupid peoples terms but clearly i am missing somthing important :(

---

### Post by ~Speed on 2006-02-01
Hello,

mine card is x800 GTO2, ex-16, 256MB.

I followed instrucitons, but this error pops out (see below):

[I]speed@deepblue:~$ sudo sh ./ati-driver-installer-8.21.7-x86_64.run --buildpkg Ubuntu/breezy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.21.7........................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
./packages/Ubuntu/ati-packager.sh: line 51: dpkg-architecture: command not found
Error: unsupported architecture:
Removing temporary directory: fglrx-insta[/I]ll


What am I missing here, please?

tnx

:)

---

### Post by Bandit on 2006-02-01
[QUOTE=~Speed]Hello,

mine card is x800 GTO2, ex-16, 256MB.

I followed instrucitons, but this error pops out (see below):

[I]speed@deepblue:~$ sudo sh ./ati-driver-installer-8.21.7-x86_64.run --buildpkg Ubuntu/breezy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.21.7........................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
./packages/Ubuntu/ati-packager.sh: line 51: dpkg-architecture: command not found
Error: unsupported architecture:
Removing temporary directory: fglrx-insta[/I]ll


What am I missing here, please?

tnx

:)[/QUOTE]
Sounds like you didnt download the correct driver. 
Keywords here = Error: unsupported architecture:
If you are using AMD 64bit CPU get the corresponding driver.
If your using a 32bit CPU get the i386 drivers.

---

### Post by DazarGaidin on 2006-02-01
Why oh why doesnt it work?

I started to get excited, did the how to with no errors, everything seemed fine.  After the last reboot i get a different higher resolution but the same driver! :(  


```
integrity@store:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1041 (X4.3.0-8.21.7)

```

I have a radeon 9250 :( :( :(

I saved my console screen for most of it in a text file if you need me to post it..

---

### Post by mlomker on 2006-02-01
[QUOTE=DazarGaidin]I saved my console screen for most of it in a text file if you need me to post it..[/QUOTE]

It is working.  My own card comes up as a 9600 when it is a 9700.  It doesn't matter.  If your game isn't working then I'd recommend posting on the game board or the Rage3D board for help.  It's a driver problem...you've installed it correctly.

---

### Post by DazarGaidin on 2006-02-01
You are right!  I just said screw it and tried the game and it works now.  I guess it just calls it the wrong name :) 

yay!

---

### Post by ~Speed on 2006-02-01
[QUOTE=Bandit]Sounds like you didnt download the correct driver. 
[/QUOTE]

I dont think so.

Well, this is what it results in:
~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Hmm.
This is not my card.
:-k :-k :-k

Edited:
something is different, though. There was an ATI Control link added to menu...
Hmm.

---

### Post by marcan on 2006-02-02
After much tinkering and messing with libraries I finally got fglrx working on ubuntu amd64. glxgearsruns fine, fgl_glxgears runs fine too, fglrxinfo reports:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

```
However, I can't get support on 32bit apps working (specifically, I want wine, although neither a 32bit fgl_glxgears nor a 32bit glxgears work properly). 32bit glxgears is AWFULLY SLOW and a 32bit fglrxinfo reports:
```

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I've checked and tried 3 versions of libGL.so (and I'm pretty damn sure that I haven't got any other versions lying around - I checked and rechecked with ldd). Newer ATI drivers, what Breezy comes with, etc. Three different versions from three different places all "work" (ie the program links and runs fine) but report as Mesa. Why are 32bit apps using Mesa instead of hardware rendering? Anyone got 32bit apps under amd64 working?

---

### Post by dsierpin on 2006-02-02
> However, I can't get support on 32bit apps working (specifically, I want wine, although neither a 32bit fgl_glxgears nor a 32bit glxgears work properly). 32bit glxgears is AWFULLY SLOW

Same problem here.

---

### Post by ~Speed on 2006-02-02
[QUOTE=~Speed]
Well, this is what it results in:
~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Hmm.
This is not my card.
:-k :-k :-k

Edited:
something is different, though. There was an ATI Control link added to menu...
Hmm.[/QUOTE]

I was thinking, my card (ati radeon saphire was tweaked to "produce" 16 pipes instead of default 12 pipes.
Could this be a problem?

I think with a newly installed ATI drivers it should yield at leaset some result!

Hmm.

Any suggestions, please?

---

### Post by shade11 on 2006-02-02
I need desprate help!!! It doesn't install properly. I have an ATI mobility Raedon x300 and I don't know how to get it to work with fglrx. . . What do I do in order to make it work. Please help!:confused:

---

### Post by mlomker on 2006-02-02
[QUOTE=~Speed]I think with a newly installed ATI drivers it should yield at leaset some result![/QUOTE]

I'd recommend that you guys get on the Rage3D board.  I don't know that 32-bit apps on a 64-bit system are even supported.  I never took it beyond running glxgears on 64-bit.  I'd certainly recommend that any game player run 32-bit Ubuntu.

---

### Post by mlomker on 2006-02-02
[QUOTE=shade11]I need desprate help!!! It doesn't install properly. I have an ATI mobility Raedon x300 and I don't know how to get it to work with fglrx. . . What do I do in order to make it work. Please help!:confused:[/QUOTE]

You didn't provide any details about where you are running into trouble.  The quality of help that you receive online depends entirely upon how good you are at asking questions and providing relevant details.  This is the kind of post that most people would ignore.

---

### Post by LandyMan on 2006-02-02
Hi Mlomker,

I managed to get the old drivers installed (8.16), getting the results in fglrxinfo like I should. I checked the logs of 8.21, and nothing seems out of place, apart from an AGP warning (already enabled on the Kernel). I have also noticed that I dont have the fglrxconfig file.

Any ideas? Oh, I am running a HP notebook with an ATI Radeon 9100

Thanks

EDIT: Great HOW-TO's on the drivers. Thanks for the effort!

---

### Post by shade11 on 2006-02-02
[QUOTE=mlomker]You didn't provide any details about where you are running into trouble.  The quality of help that you receive online depends entirely upon how good you are at asking questions and providing relevant details.  This is the kind of post that most people would ignore.[/QUOTE]

Sorry, well anyway. I follow the instructions and it doesnt work. My screen turns to a 1024 x 768 resloution and it is all fuzzy. It doesnt work. Then my screen would sometimes go black after doing monitor autodetect; but it stays there.

I am running an ATI mobility raedon X300 (Ubuntu detects it as ATI mobility raedon M300.)

I asked my friend to help but he couldnt get it to work. I also installed the ATI driver from ATI but no luck.

If there is anything you need to know about it please tell me and I will give you the details.

---

### Post by ~Speed on 2006-02-03
[QUOTE=mlomker]I'd recommend that you guys get on the Rage3D board.  I don't know that 32-bit apps on a 64-bit system are even supported.  I never took it beyond running glxgears on 64-bit.  I'd certainly recommend that any game player run 32-bit Ubuntu.[/QUOTE]

mlomker hey :) I thank you for your help so far. :)

Well, the games are somethng I can live without easily. No problem.

I wander, though, how much display and performance quality I am (in fact, all of us) loosing here, being "just"on vesa drivers...

For example, I can't change refresh rate on monitor (at least not without reconfiguring xserver, again,and again, and yet again).
:cry::cry: :cry:

---

### Post by Gentleman on 2006-02-03
[QUOTE=~Speed]mlomker hey :) I thank you for your help so far. :)

Well, the games are somethng I can live without easily. No problem.

I wander, though, how much display and performance quality I am (in fact, all of us) loosing here, being "just"on vesa drivers...

For example, I can't change refresh rate on monitor (at least not without reconfiguring xserver, again,and again, and yet again).
:cry::cry: :cry:[/QUOTE]

Are all the needed kernel-modules loaded? (agpgart, ati-agp, drm, radeon) (I don't know for sure if these are the 4 needed modules)

---

### Post by ~Speed on 2006-02-03
[QUOTE=Gentleman]Are all the needed kernel-modules loaded? (agpgart, ati-agp, drm, radeon) (I don't know for sure if these are the 4 needed modules)[/QUOTE]

beats me.

how do I check out if they are, please?

---

### Post by dragonflyFZX on 2006-02-03
hi,

i am sorry if this problem has already come up in this discussion, but it has become such a long thread that i dont know where to start.  I experienced playback problems when i watch dvds.  When there is a lot of movement on the screen, it seems as if the images are made up of horizontal lines.  I tried different players, but all have the same problem.  I mentioned it on a dutch ubuntu forum, and someone told me he had the same problem and followed the thread that this thread is discussing.   Since i also have an ATI, i thought i would give it a go...  However, after following the advice, X fails to come up.  If i switch to a console (ctrl-alt-f1) and try to invoke X with startx, it gives an error 
(EE) no devices detected

fatal server error
no screens found

here are some relevant parts of the log file:
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.21.7
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.21g1                           
(II) ATI Proprietary Linux Driver Build Date: Jan 14 2006 16:26:15
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.21.1-driver-lnx-238868
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

I am running kubuntu breezy on a hp pavilion ze4300, which has, according to ubuntu, a ATI Technologies, Inc. Radeon 320M (RS200 IGP) card.  And i do have to admit that i dont know anything about the technical aspects of computer graphics, but i learn quickly :-? 

What could be the problem?

---

### Post by mlomker on 2006-02-03
[QUOTE=LandyMan]I managed to get the old drivers installed (8.16), getting the results in fglrxinfo like I should. I checked the logs of 8.21, and nothing seems out of place, apart from an AGP warning (already enabled on the Kernel). I have also noticed that I dont have the fglrxconfig file.[/QUOTE]

You're saying the latest didn't work but the 8.16.x does?  If that version does what you need it to then I wouldn't bother upgrading.

What was 8.21.x doing?  Your best bet for help is to start a new thread in Video & Sound and attach all of the logs and explain exactly what it is doing.  You can PM me a link to the post and I'll take a look at it.  I *have* seen a few cases where there is no obvious error but it still comes up MESA, but they're pretty rare.  If you look in kern.log and Xorg.0.log there's usually a clue.

---

### Post by mlomker on 2006-02-03
[QUOTE=shade11]Sorry, well anyway. I follow the instructions and it doesnt work. My screen turns to a 1024 x 768 resloution and it is all fuzzy. It doesnt work. [/QUOTE]

It sounds like the driver is misdetecting the refresh/resolution of your monitor.  Xorg.0.log will provide details about what it is trying to use.  You can look into using MODE lines if that's the case.

---

### Post by mlomker on 2006-02-03
[QUOTE=dragonflyFZX]ATI Technologies, Inc. Radeon 320M (RS200 IGP) card.  [/QUOTE]

Your card isn't supported because it's actually a 7000 mobile chipset and the driver is 8500+.  [A related thread.]("http://ubuntuforums.org/showthread.php?t=3289")

---

### Post by eprebys on 2006-02-03
The instructions were fantastic, thank you! But I have two remaining issues that are driving me crazy. I have a T42p IBM ThinkPad, running Breezy with the ATI card:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)

The install appears to have been successful. I am running a dual head setup, with a crt as the second monitor:

eric@communitize:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5582 (8.21.7)

display: :0.0 screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5582 (8.21.7)

eric@communitize:~$ dmesg | grep fglrx
[4294686.108000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294686.112000] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[4294686.112000] [fglrx] module loaded - fglrx 8.21.7 [Jan 14 2006] on minor 0
[4294718.551000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294718.551000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294718.551000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294718.551000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294718.552000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294718.761000] [fglrx] free  AGP = 252440576
[4294718.761000] [fglrx] max   AGP = 252440576
[4294718.761000] [fglrx] free  LFB = 114274304
[4294718.761000] [fglrx] max   LFB = 114274304
[4294718.761000] [fglrx] free  Inv = 0
[4294718.761000] [fglrx] max   Inv = 0
[4294718.761000] [fglrx] total Inv = 0
[4294718.761000] [fglrx] total TIM = 0
[4294718.761000] [fglrx] total FB  = 0
[4294718.761000] [fglrx] total AGP = 65536
[4294718.896000] [fglrx] free  AGP = 252440576
[4294718.896000] [fglrx] max   AGP = 252440576
[4294718.896000] [fglrx] free  LFB = 74424320
[4294718.896000] [fglrx] max   LFB = 74424320
[4294718.896000] [fglrx] free  Inv = 0
[4294718.896000] [fglrx] max   Inv = 0
[4294718.896000] [fglrx] total Inv = 0
[4294718.896000] [fglrx] total TIM = 0
[4294718.896000] [fglrx] total FB  = 0
[4294718.896000] [fglrx] total AGP = 65536


1. The madwifi driver no longer works. I followed the steps in the guide. Check out my dir:

eric@communitize:~$ ls -l /lib/modules/2.6.12-10-686/madwifi/
-rw-r--r--  1 root root 164851 2006-02-03 14:13 ath_hal.ko

What do I need to do to get it back?


2. When I start up, *sometimes* everything starts up correctly, as above. Sometimes, the lcd laptop screen comes up all fuzzy as though it was a crt screen running at a low resolution. When this happens, dmesg doesn't show anything relating to fglrx. There are no unusual errors in /var/log/Xorg.0.log. If I switch to another terminal and run 'sudo /etc/init.d/gdm stop;sudo/etc/init.d/gdm start', the problem is usually fixed. Sometimes I have to restart gdm several times. What could cause this? I don't think it is a physical connection thing because the problem is with the laptop screen (the second, crt monitor displays properly in 1600x1200.

3. I am also having a resolution problem which I logged here:
[http://ubuntuforums.org/showthread.php?t=83973&page=2](http://ubuntuforums.org/showthread.php?t=83973&page=2)

Thanks for any help!

---

### Post by eprebys on 2006-02-03
I realized that if you have time to help, you might want to see this as well:

[http://prebys.org/kern.log](http://prebys.org/kern.log)

This is particularly interesting:
Feb  3 14:15:36 localhost kernel: [4294686.156000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
Feb  3 14:15:36 localhost kernel: [4294686.157000] wlan: disagrees about version of symbol struct_module
Feb  3 14:15:36 localhost kernel: [4294686.157000] ath_rate_sample: disagrees about version of symbol struct_module
Feb  3 14:15:36 localhost kernel: [4294686.157000] ath_pci: disagrees about version of symbol struct_module

---

### Post by RavenOfOdin on 2006-02-03
Just in case anyone wants the latest set of ATI-distributed drivers for any reason:

[http://support.ati.com/ics/support/default.asp?deptID=894](http://support.ati.com/ics/support/default.asp?deptID=894)
[https://a248.e.akamai.net/f/674/0296/0/www2.ati.com/drivers/ati-driver-installer-8.21.7-i386.run](https://a248.e.akamai.net/f/674/0296/0/www2.ati.com/drivers/ati-driver-installer-8.21.7-i386.run)

---

### Post by shade11 on 2006-02-03
So I got the drivers installed and acceleration works, but then my resolution is at an ugly 1024 x 768. I know I checked resloutions that are higher than 1024 x 768 and it stays at this ugly resolution. So I un-installed it. I want it at 1028 x 800. (The resolution that works.) If you didn't read it already I have an ATI Mobility Raedon X300 on a Dell Inspiron 6000.

---

### Post by kdavison007 on 2006-02-04
After installing 8.21 I can't get DRI working. 

I get this error in my /var/log/Xorg.0.log:

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

Looks like this says that I should install linux-$arch or ubuntu-fglrx-$arch, but when I do:

sudo apt-get install ubuntu-fglrx-386 I get:


The following packages have unmet dependencies:
ubuntu-fglrx-386: Depends: xorg-driver-fglrx (= 8.20.8-1) but 8.21.7-1 is to be installed
Depends: fglrx-kernel-2.6.12-10-386 (= 8.20.8-1+2.6.12-10.26) but it is not going to be installed
E: Broken packages

---

### Post by stalefries on 2006-02-04
[quote=Anchovie]ldd /usr/X11R6/bin/fglrxinfo outputs...

```
linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/X11R6/lib/libGL.so.1 (0xb7e77000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7db7000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7da9000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c7b000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c69000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c66000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c63000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c5f000)
        /lib/ld-linux.so.2 (0xb7f23000)
``` 
ls -l /usr/X11R6/lib/libGL.so.1* outputs...

```
lrwxrwxrwx  1 root root     12 2005-10-15 06:34 /usr/X11R6/lib/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x  1 root root 773466 2005-10-11 10:49 /usr/X11R6/lib/libGL.so.1.2
``` 
=( I'll give step 20 a try then...

EDIT: Woot! It worked after I rebooted my computer! Whoops! =P[/quote]

That ls -l one reports no such directory. 

Also, from the X log, it seems that with the fglrx driver it can't find the display, but with the ATI driver, it does.

---

### Post by dninja on 2006-02-04
I've just followed the howto and got the drivers working but my fonts are now broken, it seems to be in gnome based apps, firefox and evolution most notably.

Someone else in this discussion complained of seeing this in their Xorg.0.log file, I'm seeing this as well:

```

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
        Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID" does not exist.
        Entry deleted from font path.

```

I'm also getting this at the end of the log

```

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

```

Is there an easy way to fix this?

---

### Post by adub on 2006-02-04
very excellent tutorial got my  ati xpress 200m working with the new drivers on my widescreen new laptop

my laptop is a hp dv5030us  btw which im loving at the moment

one thing i will point out i had to do the tutorial

then add drm in /etc/modules

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
drm
lp
mousedev
psmouse
sbp2
sr_mod



without doing the above it wouldnt work

---

### Post by seanwnz on 2006-02-05
Awesome your HowTo works just fine.

My 1024x768 resolution has disappeared, and I get the optimal 1280x800 for my notebook screen. Many thanks.

One suggestion - perhaps you need to edit the HowTo now in regards to removing the restricted-modules?
I ended up not removing them because I had so many dependencies on whatever was in that package. 

The latest driver release by ATI is working great despite me having that package installed plus my Atheros wireless is working great.

Just a suggestion  - perhaps I'm missing something else ...

---

### Post by mlomker on 2006-02-05
[QUOTE=eprebys]1. The madwifi driver no longer works. I followed the steps in the guide. 

What do I need to do to get it back?
[/quote]

That method was provided by a user quite some time ago but I don't have the card, myself.  Have you tried **sudo depmod**?

You could always install a newer version and not use Ubuntu's:  [How-to here]("http://www.ubuntuforums.org/showthread.php?t=105437").

Most questions, beyond installation, are best asked on the Rage3D board.  You could try a post on the Video & Sound forum, but the ATI power users are on the other board.

---

### Post by mlomker on 2006-02-05
[QUOTE=RavenOfOdin]Just in case anyone wants the latest set of ATI-distributed drivers for any reason:

[http://support.ati.com/ics/support/default.asp?deptID=894](http://support.ati.com/ics/support/default.asp?deptID=894)
[https://a248.e.akamai.net/f/674/0296/0/www2.ati.com/drivers/ati-driver-installer-8.21.7-i386.run](https://a248.e.akamai.net/f/674/0296/0/www2.ati.com/drivers/ati-driver-installer-8.21.7-i386.run)[/QUOTE]

Those are the same drivers installed in this how-to.  Linking to akamai doesn't work, which is why I have to provide navigation instructions in the how-to.

---

### Post by mlomker on 2006-02-05
[QUOTE=shade11]I want it at 1028 x 800. (The resolution that works.)[/QUOTE]

You're the first one that I've heard of with a resolution bug in the latest driver.  There were issues with Samsung LCD panels in the early 8.18 releases, which affected my own laptop.  The Xorg.0.log file would tell you what information your display was giving to the driver for screen size, refresh, and resolution.  If it isn't an issue with your xorg.conf file then it's either a BIOS issue with the display or a driver bug.  You should file a bug report with them if you've already asked about it on Rage3D.

[ATI Bugzilla.]("http://ati.cchtml.com/")

---

### Post by mlomker on 2006-02-05
[QUOTE=kdavison007]After installing 8.21 I can't get DRI working. 

I get this error in my /var/log/Xorg.0.log:

(WW) fglrx(0): Kernel Module version does *not* match driver.
[/quote]

This means that you didn't use module-assistant to build the kernel module.  The version can be seen by looking in kern.log when it loads.

> 
sudo apt-get install ubuntu-fglrx-386 I get:


I've never heard of that package and don't see it in Synaptic.  Did you use this how-to to build these packages or not?  You should be installing them with **dpkg**, not apt-get.

---

### Post by mlomker on 2006-02-05
[QUOTE=stalefries]That ls -l one reports no such directory. [/quote]

You're looking at very old posts.  There's no need to mess with ldd anymore.  We were using those tools to try to troubleshoot why things wouldn't work when Breezy was first released.  There's nothing wrong with the drivers anymore.

> Also, from the X log, it seems that with the fglrx driver it can't find the display, but with the ATI driver, it does.

If you're using one of the latest cards then the driver might not be finding the card.  There's some hex editing that you can do to work around that.  You'll find a lot more info on the Rage3D board.  I can only guess what your issue is without seeing the logs.

---

### Post by mlomker on 2006-02-05
[QUOTE=dninja]Is there an easy way to fix this?[/QUOTE]

Those errors are normal.  Breezy doesn't use those paths.

Here's what is in my xorg.conf:

```

Section "Files"

        # paths to defoma fonts
        FontPath     "/usr/share/fonts/truetype"
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/CID"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

```

---

### Post by mlomker on 2006-02-05
[QUOTE=adub]then add drm in /etc/modules

without doing the above it wouldnt work[/QUOTE]

I'm not sure what that module does, but it is video-related.  It isn't needed on my machine.

---

### Post by mlomker on 2006-02-05
[QUOTE=seanwnz]The latest driver release by ATI is working great despite me having that package installed plus my Atheros wireless is working great.

Just a suggestion  - perhaps I'm missing something else ...[/QUOTE]

That'd be nice if it were true, but that wasn't the case with the last version.  The install would break on every reboot and even if we disabled the responsible script the install would break on a kernel update.

---

### Post by dninja on 2006-02-05
So how can I fix the fonts in gnome apps? They have gone all square and small! I didn't have anything special setup before and haven't deliberatly installed any new fonts or font tools.

---

### Post by Zubzub on 2006-02-05
When I try to remove my stock drivers I get this error:

pkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: fout bij afhandelen van xorg-driver-fglrx (--remove):
 subproces post-removal script gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

so I cant seem to be able to remove my xorg drivers :s any suggestions?

---

### Post by mlomker on 2006-02-05
[QUOTE=Zubzub]so I cant seem to be able to remove my xorg drivers :s any suggestions?[/QUOTE]

You could use the --force-yes switch to make it ignore the warnings.  There's always some risk with using that option but I'm not aware of any other work-around for that error.  

Either your Breezy install was an upgrade or you at some point installed a non-Ubuntu fglrx driver--the stock driver on a clean install does not use a diversion, as far as I know.

---

### Post by mlomker on 2006-02-05
[QUOTE=dninja]So how can I fix the fonts in gnome apps?[/QUOTE]

I'd recommend asking on the Gnome desktop board and/or the Video & Sound forum.  I personally don't run Gnome and you're the first person to experience this problem.  I have done the driver install on clean Gnome/Ubuntu boxes as a test and didn't notice a problem.

---

### Post by Zubzub on 2006-02-05
yeah, I installed the ati drivers (more like tried to) without first removing the stock drivers, so I uninstalled the ati drivers and now I get this error...

/edit it still gives the error btw, should I continue installing the ati drivers or try to get rid of this error first?

---

### Post by mlomker on 2006-02-05
[QUOTE=Zubzub]/edit it still gives the error btw, should I continue installing the ati drivers or try to get rid of this error first?[/QUOTE]

You need to remove the old driver using the force switch.  **man apt-get** and **man dpkg** will show you the various switches.  

It is possible to hose your box by using force options, so the final decision is yours.

---

### Post by scorcha on 2006-02-05
well first, thanks to you mlomker for this great how-to ^^

now
i got an unknown device 554d and 556d with a fglrxinfo

so i started one more install
i didn't select the ati driver after the removal old fglrx driver
but i selected the vesa driver
reboot... and now work fine :D

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XL Generic
OpenGL version string: 2.0.5582 (8.21.7)

```

thanks one more time ;)

---

### Post by JeffV on 2006-02-05
I followed the Hot-To exactly and everything seemed to work except for one thing:  If I try to run fglrxconfig, it says the command name doesn't exist!  I have to use aticonfig.  Anyone know what the deal is hear?

---

### Post by kemosabe79 on 2006-02-05
I apologize if this has already been asked, but I dont want to go through 60+ pages to find out.;) 

Are the x1x00 series cards supported by this driver? Im having no luck getting a x1600XT running at all.

BTW: The HOWTO works fabulously on my brother's 9800XT.  Thanks mlomker!

---

### Post by dninja on 2006-02-06
[QUOTE=mlomker]I'd recommend asking on the Gnome desktop board and/or the Video & Sound forum.  I personally don't run Gnome and you're the first person to experience this problem.  I have done the driver install on clean Gnome/Ubuntu boxes as a test and didn't notice a problem.[/QUOTE]

I don't run gnome either, it is on apps such as firefox and evolution that I'm seeing problems. I thought that these were based on gnome libraries but I could be wrong.

I'll try asking in other places, see if anyone else has had these problems.

---

### Post by Goochi on 2006-02-06
There are also drivers available at [www.ati.com](www.ati.com) for linux.
What is the difference between the ones in the packages and the ones there ?

Thanks,
gOochi

EDIT:

Never mind that question
I tried installed and ended up with this error when creating the packages
```
dpkg-deb: parse error, in file `debian/-driver-fglrx/DEBIAN/control' near line 1:
 invalid package name (must start with an alphanumeric)
dh_builddeb: command returned error code 512
make: *** [binary] Error 1
```

Any ideas what this could mean ?

Thanks.

---

### Post by encompass on 2006-02-06
oopsee...  I have installed the driver and it doesn't seem to work... I have a shuttle zen with an ati9100 IGP  I don't think, after looking here, that there is much of a solution interms of a better driver...
BUT
is there a way to restore my setting back to what they were when I installed?  I would like the acceleration still... for my simple games.  I can't for the life of me get back the original DRI support working.  Any ideas?

---

### Post by hill on 2006-02-07
I followed this guide and installed everything. I can modprobe fglrx , it loads but when i do fglrxinfo i get
```

josh@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
I have attacked my xorg config.
I have also modded my device id from 4B4B to 4A4B so that it would work.

Thanks for any help.

---

### Post by mlomker on 2006-02-07
[QUOTE=JeffV]If I try to run fglrxconfig, it says the command name doesn't exist!  I have to use aticonfig.  Anyone know what the deal is hear?[/QUOTE]

Just like the error said--they've phased out fglrxconfig and replaced it with aticonfig.  If you already have a working xorg.conf file then there's no need to change it, otherwise the command that I have in the how-to should do it.

---

### Post by mlomker on 2006-02-07
[QUOTE=kemosabe79]Are the x1x00 series cards supported by this driver? Im having no luck getting a x1600XT running at all.[/QUOTE]

[No, they aren't supported yet.]("http://www.rage3d.com/board/showthread.php?t=33842601")

In case you guys don't know, Septor is the developer that packages the ATI drivers for Ubuntu.  If he says that it doesn't work then it *really* doesn't work.

---

### Post by mlomker on 2006-02-07
[QUOTE=dninja]I don't run gnome either, it is on apps such as firefox and evolution that I'm seeing problems.[/QUOTE]

Please check back with us, I'd appreciate any info that you find.  I also run Firefox but I don't use the default fonts, so perhaps that's why I didn't notice anything.  I prefer Nimbus.

---

### Post by mlomker on 2006-02-07
[QUOTE=encompass]I can't for the life of me get back the original DRI support working.  Any ideas?[/QUOTE]

No, it's really more than I can manage just to keep informed on the fglrx drivers.  I'd recommend starting a new post on one of the forums...you're more likely to find other 9100 IGP users elsewhere than in this thread.

---

### Post by mlomker on 2006-02-07
[QUOTE=hill]I followed this guide and installed everything. I can modprobe fglrx , it loads but when i do fglrxinfo i get
[/QUOTE]

The xorg.conf is rarely the problem.  It's usually a hardware issue and the errors are always in /var/log/Xorg.0.log and kern.log.  If you don't see anything then please attach those files to a new thread and PM me a link if you like.

---

### Post by x__dark on 2006-02-07
I followed this guide and it worked, the output of fglrxinfo said ATI Radeon 9600pro, etc, for my OpenGL. I then installed Enemy Territory and when I attempted to run it, the driver suddenly changed to Mesa3D again. What's the problem?

---

### Post by mlomker on 2006-02-08
[QUOTE=x__dark]the driver suddenly changed to Mesa3D again. What's the problem?[/QUOTE]

Are you saying that the fglrxinfo output changed?  It's probably a coincidence.  Regardless, the answer is in your log files.

---

### Post by joplass on 2006-02-08
This thread just saved my rear end big time.  I screwed up my xserver, I couldn't get back to it.  I simply used the first 4 commands and boom I am in business \\:D/ .
Thanks mlomker

---

### Post by kemosabe79 on 2006-02-09
[QUOTE=mlomker][No, they aren't supported yet.]("http://www.rage3d.com/board/showthread.php?t=33842601")

In case you guys don't know, Septor is the developer that packages the ATI drivers for Ubuntu.  If he says that it doesn't work then it *really* doesn't work.[/QUOTE]

Thanks mlomker! Your a scholar and a gentleman. I managed to get it working with the vesa drivers. Im patiently awaiting fglrx support.

---

### Post by LandyMan on 2006-02-09
[quote=mlomker]You're saying the latest didn't work but the 8.16.x does?  If that version does what you need it to then I wouldn't bother upgrading.
[/quote]
mlomker, with the 8.16 drivers the fglrxinfo came up right, but running gears completely hung my system, so I decided to try the new drivers.

I will get all my logs together, and start a thread as suggested!

thanks!

---

### Post by maxdevis on 2006-02-09
i'm sorry if the answer is in this thread somewhere, but i haven't read/red? the whole thread (70p)

i have a ati 9550.
I installed the drivers as said, but now when i play a dvd or an avi, there are like little stripes, so the picture is full of little squares. 
it's only when playing a movie.

someone same problem and a solution?

---

### Post by cricha5 on 2006-02-10
I installed the 21.7 ati drivers like the howto said and it worked.  It dod not work when I used the ati installer.  Now I'm trying to install the new 22.5 drivers using the same system, but I'm getting an error at the "a-i fglrx" part, the last part.  It says that it depends on the xorg source 21.7 stuff, but the 22.5 stuff is installed.  (sorry for the vagueness.  I'm at work and all the errors are at home.  I'll post the actual error message after work.)  Any ideas?

---

### Post by zodwallop on 2006-02-10
I just followed your tutorial, only I substituted the old drivers with 8.22.5 and it worked like a charm!  Thank you so much for the tut!  Btw, my card is a 9600xt.\\:D/

---

### Post by David Vallner on 2006-02-10
[QUOTE=mlomker]I've never heard of that package and don't see it in Synaptic.  Did you use this how-to to build these packages or not?  You should be installing them with **dpkg**, not apt-get.[/QUOTE]

Seveas' repository hosts these packages, I'm using those and am getting the same problem - for some reason only the old kernel module version seems to load, even if the fglrx-kernel package installed is the correct version, and nothing else what could be the old kernel modules seems to be in the package list to uninstall manually.

---

### Post by mlomker on 2006-02-10
[QUOTE=LandyMan]mlomker, with the 8.16 drivers the fglrxinfo came up right, but running gears completely hung my system, so I decided to try the new drivers.

I will get all my logs together, and start a thread as suggested!
[/QUOTE]

Scouring the logs is always a good idea, but hard hangs are always a hardware problem of one kind or another.  If you can't Ctrl-Alt-F2 to a console then you'll want to look at your BIOS or some other hardware incompatibility.

---

### Post by mlomker on 2006-02-10
[QUOTE=maxdevis]I installed the drivers as said, but now when i play a dvd or an avi, there are like little stripes, so the picture is full of little squares. 
it's only when playing a movie.
[/QUOTE]

fglrx will make 2D worse, in general.  I'd recommend that you start a thread in the Desktop forum regarding the particular software.  I'm really only interested in supporting the installation....if that's a driver bug or a bug in your player then that's outside of the scope of this how-to.

---

### Post by mlomker on 2006-02-10
[QUOTE=cricha5]It says that it depends on the xorg source 21.7 stuff, but the 22.5 stuff is installed.  (sorry for the vagueness.  I'm at work and all the errors are at home.  I'll post the actual error message after work.)  Any ideas?[/QUOTE]

I haven't installed those, yet.  I wait until someone asks that's how I know when a new version was released.  :)  I'll try installing it tomorrow when I have some free time.

---

### Post by FrankTM on 2006-02-10
it runs like an angel here
I did a fresh install using the installer

using my old config -always a good thing to backup- I was done in about 5 minutes
had to install some building programs like gcc-3.4 etc..

---

### Post by Cysman on 2006-02-11
[QUOTE=mlomker]This is the thread for discussing [the how-to]("http://ubuntuforums.org/showpost.php?p=423584") for installing the latest ATI driver that is working for Ubuntu, and troubleshooting the results.[/QUOTE]


Hi, sorry to bother but I think I have a dependency problem here: 

My version of xorg-driver-fglrx is 8.21.7-1, whatever that is.  Apparently, I need xorg-driver-fglrx 8.22.5-1.  How do I fix this?

Cysman

Selecting previously deselected package fglrx-kernel-2.6.12-10-386.
(Reading database ... 96827 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-10-386 (from .../fglrx-kernel-2.6.12-10-386_8.22.5-1+2.6.12-10.26_i386.deb) ...
dpkg: dependency problems prevent configuration of fglrx-kernel-2.6.12-10-386:
 fglrx-kernel-2.6.12-10-386 depends on xorg-driver-fglrx (= 8.22.5-1); however:
  Version of xorg-driver-fglrx on system is 8.21.7-1.
dpkg: error processing fglrx-kernel-2.6.12-10-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-kernel-2.6.12-10-386

---

### Post by Gentleman on 2006-02-11
I already asked this question a few times on this forum, maybe now someone can give me the answer with the (again) new release of the ati-fglrx-driver... Some months ago I suffered many problems with my ati xpress 200m on hp pavillion zv6000 laptop. After searching and asking a lot on forums I&#8217;ve found the only possible solution. I had to give 128mb of my memory (ram > UMA) to the graphic card which in fact already had 128mb sideport memory. This seemed to be purely a driver issue of ati and I wasn&#8217;t to happy loosing 128mb of my precious ram&#8230; (especially if I want to run vmware with the adobe cs-suite) My question is if this driver issue is already solved, therefore I think especially people with same the graphic card can answer me... I&#8217;m able to test this, but each time I modify these setting in the bios my system becomes very unstable and I have to reinstall my os. I really hope this issue will be solved someday, I tried to contact Ati but I always get the answer back they don&#8217;t support laptops for the moment&#8230;

---

### Post by Cysman on 2006-02-11
Ok, I just did a fresh install of Breezy, ran automtix and let the OS update itself.  Then, I started to follow your directions when I got this depressing messgage:

kenoutten@ubuntubedroom:~$ sudo apt-get remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
Package xorg-driver-fglrx is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
kenoutten@ubuntubedroom:~$ sudo apt-get remove fglrx-control
Reading package lists... Done
Building dependency tree... Done
Package fglrx-control is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
kenoutten@ubuntubedroom:~$ sudo apt-get remove linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  linux-386 linux-restricted-modules-2.6.12-10-386
  linux-restricted-modules-386
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 13.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 61624 files and directories currently installed.)
Removing linux-386 ...
Removing linux-restricted-modules-386 ...
Removing linux-restricted-modules-2.6.12-10-386 ...
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
kenoutten@ubuntubedroom:~$

I ran apt-get update and got the same message i.e., "Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems"

Do you know what is going on here?

Ken

---

### Post by mlomker on 2006-02-11
[QUOTE=David Vallner]Seveas' repository hosts these packages, I'm using those and am getting the same problem - for some reason only the old kernel module version seems to load, even if the fglrx-kernel package installed is the correct version, and nothing else what could be the old kernel modules seems to be in the package list to uninstall manually.[/QUOTE]

You could always do this to see if there is more than one file on your drive:

```

sudo updatedb
locate fglrx.ko

```

You did remove restricted-modules package?  It'll put Breezy's default drivers into a dynamic directory on every boot and they will override custom drivers.

---

### Post by mlomker on 2006-02-11
[QUOTE=Cysman]Hi, sorry to bother but I think I have a dependency problem here: 

My version of xorg-driver-fglrx is 8.21.7-1, whatever that is.  Apparently, I need xorg-driver-fglrx 8.22.5-1.  How do I fix this?
[/QUOTE]

I made the same mistake! lol.  You have to make sure that you install the **fglrx-kernel-source** package and not the **fglrx-sources** package that gets created...the later one is only the source for the control panel applet.

---

### Post by mlomker on 2006-02-11
[QUOTE=Gentleman]I tried to contact Ati but I always get the answer back they don’t support laptops for the moment…[/QUOTE]

I'd recommend asking on the Rage3D board--the developers are there along with some other very smart folks.  If it can be done then the answer will be on there.  

I want to keep this thread on-topic just for the install.  Goodness knows the driver has bugs...

---

### Post by mlomker on 2006-02-11
[QUOTE=Cysman]Do you know what is going on here?
[/QUOTE]

Yeah, you didn't have the fglrx driver installed yet so the first command failed (it isn't installed by default).  The other errors are either because your Internet connection is down or Ubuntu's repositories are flaky.  You could try a **sudo apt-get update**.

---

### Post by CompakDark on 2006-02-11
I've just installed the newest driver for my ATI Radeon 9200SE, but the output of fglrxinfo is still reading:

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I have another computer upstairs using the same driver for a 9600pro and I checked the xorg configuration and such, compared, everything seems in place. The fglrx module is loading on boot, it's listed in the /etc/modules file, but still no go. Any ideas?

---

### Post by tcodilean on 2006-02-11
Sorry guys If I kept posting in the wrong place! I apologise for this. I am happy with the driver that I have installed (the default that comes with breezy). I am only wondering whether a kernel upgrade will result in me having to reinstall/reconfigure this and if yes do I have to go through the entire procedure  or not.

My original post is here:

I would appreciate some help on this.
If I apply a kernel update will I have to reinstall/reconfigure the ATI fglrx drivers?
If yes, could any of you help me with a step by step tutorial? I am new to this and would not like to mess up something that runs OK!

Thanks!

I am running Breezy on a Thinkpad R50p

---

### Post by maxdevis on 2006-02-11
[QUOTE=mlomker]fglrx will make 2D worse, in general.  I'd recommend that you start a thread in the Desktop forum regarding the particular software.  I'm really only interested in supporting the installation....if that's a driver bug or a bug in your player then that's outside of the scope of this how-to.[/QUOTE]

nope,
i know it's in the drivers, because when i installed ubuntu it wasn't, after i installed this drivers, it was.
but i needed these, because with the default drivers, my tv-out didn't work.

---

### Post by OTll on 2006-02-12
Hey all,

I can't get my graphics card to work, although I feel I have tried anything I can try (=the things I know more or less what I'm doing; and I followed this, and other guides step by step). Anyone can help me out of it (step by step, what should I check and how etc.)? I followed the howto-guide with ati-driver-installer-8.22.5-x86_64.run, so for installation, I used:
```

$ ls *.deb
fglrx-control_8.22.5-1_amd64.deb
fglrx-kernel-source_8.22.5-1_amd64.deb
fglrx-sources_8.22.5-1_amd64.deb
xorg-driver-fglrx_8.22.5-1_amd64.deb
xorg-driver-fglrx-dev_8.22.5-1_amd64.deb

```

Thx a lot,
ks




And now time for some information:

AMD64 X2 processor, latest kernel
```

$ uname -r
2.6.12-10-amd64-k8-smp

```

ATI X700 graphics card (not recognized):
```

$ lspci | grep ATI
0000:05:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5e4f
0000:05:00.1 Display controller: ATI Technologies Inc: Unknown device 5e6f

```

My current xorg.conf uses a 'vesa'-driver, since I can't get ati or fglrx to work:
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X700 SE (RV410)"
        Driver          "vesa"
        BusID           "PCI:5:0:0"
        Option          "UseInternalAGPGART" "no"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Secondary (RV410)"
        Driver          "fglrx"
        BusID           "PCI:5:0:1"
        VideoRam        256
        Option          "UseInternalAGPGART" "no"
EndSection

```
and:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon X700 SE (RV410)"
        #Device         "ATI Technologies, Inc. Radeon Secondary (RV410)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
And also in my xorg.conf:
```

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
#       Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

```


```

Section "DRI"
        Mode    0666
EndSection

```

If I run fglrx info now:
```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

but dmesg and lsmod don't give any entry to fglrx:
```

$ dmesg | grep fglrx
$ lsmod | grep fglrx
$

```

the libraries:
```

$ ldd /usr/bin/glxinfo
        libGL.so.1 => /usr/lib/libGL.so.1 (0x00002aaaaabc2000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00002aaaaad82000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0x00002aaaaaeff000)
        libm.so.6 => /lib/libm.so.6 (0x00002aaaab039000)
        libc.so.6 => /lib/libc.so.6 (0x00002aaaab1bf000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00002aaaab3f6000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00002aaaab5d0000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00002aaaab6e2000)
        libdl.so.2 => /lib/libdl.so.2 (0x00002aaaab7f7000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00002aaaab8f9000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00002aaaabb02000)
        /lib64/ld-linux-x86-64.so.2 (0x00002aaaaaaab000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00002aaaabc0f000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00002aaaabd12000)

```

and I don't know if it's important, but for Xsession startup, I found this, pointing to lib32-modules:
```

/etc/X11/Xsession.d$ cat 10fglrx
LIBGL_DRIVERS_PATH=/usr/X11R6/lib/modules/dri
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/lib

if [ `uname -m` = 'x86_64' ]; then
  if [ -d /usr/X11R6/lib32/modules/dri ]; then
    LIBGL_DRIVERS_PATH=${LIBGL_DRIVERS_PATH}:/usr/X11R6/lib32/modules/dri
    LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/lib32
  fi
fi

export LIBGL_DRIVERS_PATH
export LD_LIBRARY_PATH

```

And something that bothers me somehow:
```

$ locate fglrx.ko
/lib/modules/fglrx/fglrx.ko
/lib/modules/fglrx/build_mod/2.6.x/.fglrx.ko.cmd
/lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
/lib/modules/fglrx/build_mod/fglrx.ko
/lib/modules/2.6.12-10-amd64-k8-smp/misc/fglrx.ko
/lib/modules/2.6.12-10-amd64-k8-smp/kernel/drivers/char/drm/fglrx.ko

```

I attached some Xorg.log-files when I use the 'ati', 'fglrx' (somehow, it seemed to work once 'fglrx.txt', but while starting gnome - gdm showed up fine - it crashed, and next time I started, or tried to start gdm, I got the other log), 'fglrx' (if I use fglrx now, system hangs 'fglrx2.txt', with only restart-possibility: the reset-button: everything is locked, including mouse and keyboard, and screen goes blank) and 'vesa' driver (the one that gives me at least some graphics :p ):
[ATTACH]6076[/ATTACH]
[ATTACH]6077[/ATTACH]
[ATTACH]6078[/ATTACH]
[ATTACH]6079[/ATTACH]

Oh yes, if I use aticonfig, it makes a xorg.conf file leading so similar log files such as 'fglrx2.txt' and system hangs...

---

### Post by OTll on 2006-02-12
update: 
```

$ sudo modprobe fglrx
$ lsmod | grep fglrx
fglrx                 513088  0
$ dmesg | grep fglrx
[  345.045209] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  345.047208] [fglrx] Maximum main memory to use for locked dma buffers: 1877 MBytes.
[  345.047638] [fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
$

```

But no change, still same problems:
[ATTACH]6082[/ATTACH]
[ATTACH]6083[/ATTACH]

[EMAIL="kurt.sys@gmail.com"]email me[/EMAIL]

---

### Post by mlomker on 2006-02-12
[QUOTE=tcodilean]Sorry guys If I kept posting in the wrong place! I apologise for this. I am happy with the driver that I have installed (the default that comes with breezy). I am only wondering whether a kernel upgrade will result in me having to reinstall/reconfigure this and if yes do I have to go through the entire procedure  or not.
[/QUOTE]

An upgrade to what?  A security upgrade will not be a problem.  If you intend to install a different kernel version then you will have to re-run the **module-assistant** commands again to build a new module.

---

### Post by mlomker on 2006-02-12
[QUOTE=CompakDark]it's listed in the /etc/modules file, but still no go. Any ideas?[/QUOTE]

You don't need to do that because X loads it.  In any case, you'll need to look in /var/log/kern.log and Xorg.0.log for errors.

---

### Post by Razorback on 2006-02-12
mlomker,
I am having difficulty in getting an ATI 9250 256 MB PCI card configured.  I have tried you how-to's but am having no luck.  My PC always hangs right before the login screen.  My PC is an older Compaq EP that has onboard Intel graphics.  It does not have an AGP slot and the ATI card is in one of the PCI slots, if this would matter.  What is the best way to attach an Xorg and Kernel log?  I would appreciate any help as to what I am doing wrong.

---

### Post by mlomker on 2006-02-12
Do you have more than one video card?  Your xorg.conf references 5:0:0 and 5:0:1 and all of the error messages that you've posted indicate that your xorg.conf file is incorrectly formatted.  

The driver in the misc directory is the one created by this how-to.  The other files must be from other attempts/methods of installation.  The modeles/fglrx directory doesn't get created when you install using DEB files.

I'd recommend starting with a fresh xorg.conf by renaming/deleting your current /etc/X11/xorg.conf and then run **sudo dpkg-reconfigure xserver-xorg** and configure it for the ATI driver.  After that completes then run the **sudo aticonfig --initial** command to add the settings for fglrx.

---

### Post by OTll on 2006-02-12
Hey again, thx for your answer...
I have only one video card, but in one of my attempts, it helped to put two in the xorg.conf. Well, anyway, I tried **sudo dpkg-reconfigure xserver-xorg**, and the ati-driver doesn't work (so it's of no use going on with the fglrx-driver, I suppose) - [ATTACH]6100[/ATTACH]. I'm still in vesa-mode - [ATTACH]6101[/ATTACH]. I guess I messed up some stuff with my previous attemps. Fresh install (of Ubuntu) may be possibly the best solution? Or should I try something else first...?
thx, OTll


[QUOTE=mlomker]Do you have more than one video card?  Your xorg.conf references 5:0:0 and 5:0:1 and all of the error messages that you've posted indicate that your xorg.conf file is incorrectly formatted.  

The driver in the misc directory is the one created by this how-to.  The other files must be from other attempts/methods of installation.  The modeles/fglrx directory doesn't get created when you install using DEB files.

I'd recommend starting with a fresh xorg.conf by renaming/deleting your current /etc/X11/xorg.conf and then run **sudo dpkg-reconfigure xserver-xorg** and configure it for the ATI driver.  After that completes then run the **sudo aticonfig --initial** command to add the settings for fglrx.[/QUOTE]

---

### Post by OTll on 2006-02-12
Update: I did a fresh install, followed the howto-guide. After fresh install of Ubuntu (before installing fgrlx), the ati-driver didn't work (Xorg.log: [ATTACH]6104[/ATTACH]). Anyway, I found somewhere that installing fglrx might help, so that's what I did. Starting up with the fglrx-driver in my xorg.conf gives me a blank screen and locks everything (reset with reset-button). It's possibly not a problem with the driver: Xorg.log: [ATTACH]6105[/ATTACH]? 
Last part of kernel.log:
```

Feb 13 00:48:26 localhost kernel: [  123.829922] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 13 00:48:26 localhost kernel: [  123.831723] [fglrx] Maximum main memory to use for locked dma buffers: 1877 MBytes.
Feb 13 00:48:26 localhost kernel: [  123.832112] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Feb 13 00:48:26 localhost kernel: [  123.832118] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
Feb 13 00:48:26 localhost kernel: [  123.832134] [fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
Feb 13 00:48:27 localhost kernel: [  124.903197] [fglrx] free  PCIe = 51118080
Feb 13 00:48:27 localhost kernel: [  124.903205] [fglrx] max   PCIe = 51118080
Feb 13 00:48:27 localhost kernel: [  124.903207] [fglrx] free  LFB = 116322304
Feb 13 00:48:27 localhost kernel: [  124.903209] [fglrx] max   LFB = 116322304
Feb 13 00:48:27 localhost kernel: [  124.903212] [fglrx] free  Inv = 402653184
Feb 13 00:48:27 localhost kernel: [  124.903215] [fglrx] max   Inv = 402653184
Feb 13 00:48:27 localhost kernel: [  124.903217] [fglrx] total Inv = 402653184
Feb 13 00:48:27 localhost kernel: [  124.903218] [fglrx] total TIM = 0
Feb 13 00:48:27 localhost kernel: [  124.903220] [fglrx] total FB  = 0
Feb 13 00:48:27 localhost kernel: [  124.903221] [fglrx] total PCIe = 16384

```

Anyone can point me where to look for possible solutions?
thx, OTll

---

### Post by daniel_victoria on 2006-02-13
Hi all,

I'm completelly newbie here with a Radeon 9000. I want to install the ATI binary drivers but I don't know which instructions to follow. mlonkers' HowTo tells me to remove linux-restricted-modules but the Ubuntu Wiki on the ATI driver does not mention that. This is important for me because I have to use the MadWIFI drivers.

Also, the Wiki mentions to add fglrx at the end of /etc/modules but both mlonkers HowTo (from the forum and his wiki - [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) ) does not mention that.

Which instructions should I follow? Thanks

---

### Post by tcodilean on 2006-02-13
[QUOTE=mlomker]An upgrade to what?  A security upgrade will not be a problem.  If you intend to install a different kernel version then you will have to re-run the **module-assistant** commands again to build a new module.[/QUOTE]
Thanks for the reply! It is just a security update...

---

### Post by Boston on 2006-02-13
I installed the latest ATI drivers for my Radeon Mobility 9700. It works perfectly fine, except when I logout sometimes, my screen will lose it's image and become a pulsating gray with a bunch of scanlines. I'm afraid this will ruin my screen. Has anyone else had this problem?

---

### Post by koma77 on 2006-02-13
I think I'm also seeing what Boston is talking about:
When I logout, my monitor shuts down. 
The same thing happen when I am logged in and switches to a console.
Even if I switch back to X, the monitor will not come back on again.
Not until I reboot!

Any ideas?

---

### Post by shade11 on 2006-02-13
Well I finally got it installed properly. But now there are two issues I have.

-Is there anything I need to add in ininNG?

and

- On some games and screensavers the graphics turn out slow and choppy. I know that my graphics card can take it but it isnt working. What do I do?


Please respond. . . If there is any info I need to post then please tell me.

Here is fglrxinfo:
```
ian@Jevelexwen:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5642 (8.22.5)

ian@Jevelexwen:~$
```

---

### Post by OTll on 2006-02-13
update: if I don't load the 'dri'-module, x starts up find, but not like I expected. Remeber, it's a fresh install of Ubuntu and I followed the very nice howto step by step. This is what I have now:

xorg.conf
```

...
Section "Module"
        Load  "GLcore"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
#       Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
#       Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection
...
Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:5:0:0"
        VideoRam    262144
        #Option      "VideoOverlay" "on"
        #Option      "OpenGLOverlay" "off"
        Option      "UseInternalAGPGART" "no"
        Option      "BusType"   "PCIE"
        Option      "MonitorLayout"     "LVDS, TMDS"
EndSection

```

In Xorg.log.0:
```

(II) fglrx(0): detected X.org 6.8.2.0
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x07ff0000

```
(no dri, which is logic, since I commented the line, right?)

... and testing:
```

# fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

Now, the question here is... how can I enable dri/fgrlx-driver without my X to crash?

thx, OTll

---

### Post by HeXonX on 2006-02-13
I finally got 3D Hardware rendering! Great job! I'm using a Radeon 9200 SE.\\:D/

---

### Post by HeXonX on 2006-02-13
Boston - I have a similar problem. When I reboot my monitor says Out of Range, and the machine doesn't ever reboot. I have to shutdown.

---

### Post by shade11 on 2006-02-14
E-gad this is annoying I need help. I asked the question before. I installed the drivers and it is choppy on some games and stuff. I tried playing shogo MAD (Native linux port) on my lappy but it is too choppy and I have to stick with cruddy software acceleration.  I played Shogo's Windows port and it runs super fast. Not to mention the fact that my praphics cars is 64Mb and I played shogo on a 32 Mb card and it ran perfectly. What is going on?

---

### Post by alfonz on 2006-02-14
I followd the HOW-TO and it worked great, finaly accelerated graphics on my 9600XT. I used the 8.22.5 drivers

However, I did encounter a slight problem. My monitor suspend mode doesn't work anymore and I lost the functions on some of my keys on keyboard (viewmate) ie. win key, print screen don't work anymore. I have remapped the keys and I can deal with no suspend monitor, but i got openGL to work.

If anyone has experienced this problem and found a solution please post it here

Thanks, Cheers!

---

### Post by mlomker on 2006-02-14
[QUOTE=OTll]Fresh install (of Ubuntu) may be possibly the best solution? Or should I try something else first...?[/QUOTE]

A hard lock is usually a hardware problem.  If you can't Ctrl-Alt-F2 then I'd start by looking at hardware...other cards in the box, BIOS, etc.  Linux should *never* hard lock for any reason.

---

### Post by mlomker on 2006-02-14
[QUOTE=daniel_victoria]Which instructions should I follow? Thanks[/QUOTE]

Daniel, I wrote that wiki page.  If you want to run the older 8.16.20 drivers then you can leave linux-restricted.  If you want to run the latest drivers then you need to remove it.

---

### Post by mlomker on 2006-02-14
[QUOTE=Boston]my screen will lose it's image and become a pulsating gray with a bunch of scanlines. I'm afraid this will ruin my screen. Has anyone else had this problem?[/QUOTE]

Yes, it's a common driver bug.  I have to power-off when that happens.  It actually hasn't happen to me with the last two drivers but I commonly got that on the first few 8.18.x versions.

---

### Post by mlomker on 2006-02-14
[QUOTE=shade11]Is there anything I need to add in ininNG?[/quote]

I don't know what that is.

> 
- On some games and screensavers the graphics turn out slow and choppy. I know that my graphics card can take it but it isnt working. What do I do?


Please start another thread in the desktop or the video forum.  I only want discussion of the driver install in this thread--it's already too long for anyone to read.

---

### Post by mlomker on 2006-02-14
[QUOTE=OTll]update: if I don't load the 'dri'-module, x starts up find, but not like I expected. Remeber, it's a fresh install of Ubuntu and I followed the very nice howto step by step. This is what I have now:
[/QUOTE]

**dri** is 3D acceleration.  I'd recommend that you do some research and ask your question on the [Rage3D]("www.rage3d.com/board/forumdisplay.php?f=88") board.  

I'm here to support problems with the how-to itself being wrong and will definitely answer questions if I've heard of the problem before or seen it myself.  I only own one PC, though, and there's no way that I can be knowledgable about every hardware configuration out there.  I don't work for ATI!

---

### Post by mlomker on 2006-02-14
[QUOTE=shade11]E-gad this is annoying I need help. I asked the question before.[/QUOTE]

It's either a problem with the game or the driver itself.  I can't help you with that because I don't play games or write the driver.

You can try starting a thread on one of the game sub-boards on here or you could try jumping on the Rage3D forum where a lot of ATI users hang out (regardless of linux version or OS).

**This thread is just for installing the driver.**

---

### Post by mlomker on 2006-02-14
[QUOTE=alfonz]My monitor suspend mode doesn't work anymore and I lost the functions on some of my keys on keyboard (viewmate) ie. win key, print screen don't work anymore.[/QUOTE]

I can't imagine how a video driver would affect your keyboard, but the monitor thing doesn't surprise me.  The fglrx driver focuses on 3D video and has always been weak on 2D video and power features.  Laptop suspend wasn't even supported until 8.18.x, which was released perhaps four months ago and still has issues.

If you have questions about driver features (bugs) then you'll want to go to the Rage3D board.  I don't want to recreate the wheel on this thread...

---

### Post by riff_79 on 2006-02-15
A big thanks to all who contrib'ed towards this how to. It worked FIRST TIME!!!!

This is so awesone!

---

### Post by kumquatkowboy on 2006-02-15
Hi,

This How-to is a bit high-level for me, I am an absolute beginner. 

I'm using Breezy and an ATI Radeon X550 graphics card. I don't understand how to do this bit:

"You'll need Universe enabled in your sources.list file to download module-assistant. You may replace your /etc/apt/sources.list with this one if you wish and then sudo apt-get update before proceeding."

I don't seem to have an /etc/apt/sources.list file, and I don't know how to create one. 

Sorry if this is a really dumb query - that's the kind of newbie I am.

---

### Post by alfonz on 2006-02-15
[QUOTE=mlomker]I can't imagine how a video driver would affect your keyboard, but the monitor thing doesn't surprise me.  The fglrx driver focuses on 3D video and has always been weak on 2D video and power features.  Laptop suspend wasn't even supported until 8.18.x, which was released perhaps four months ago and still has issues.

If you have questions about driver features (bugs) then you'll want to go to the Rage3D board.  I don't want to recreate the wheel on this thread...[/QUOTE]

Oh my appologies, as I said nothing im rushing with, its minor problem that I can live with, and besides the best sreen safer is your power button. I do agree with you about the keyboard, I was dumbfounded myself. They keys stoped working after I installed the new drivers. Oh well when I have time I will tinker with xorg.conf, it maybe a problem there.

---

### Post by OTll on 2006-02-15
ok, thx a lot... I'll try the other forum

[QUOTE=mlomker]It's either a problem with the game or the driver itself.  I can't help you with that because I don't play games or write the driver.

You can try starting a thread on one of the game sub-boards on here or you could try jumping on the Rage3D forum where a lot of ATI users hang out (regardless of linux version or OS).

**This thread is just for installing the driver.**[/QUOTE]

---

### Post by mlomker on 2006-02-15
[QUOTE=kumquatkowboy]I don't seem to have an /etc/apt/sources.list file, and I don't know how to create one.[/QUOTE]

You have that file by default, so if it isn't there then you must have deleted it.  That file lists the sources that you download operating system updates and packages from.  I included a link to my sources.list in the how-to, so you can always use that instead.  Here's a [specific howto]("http://www.ubuntuforums.org/showthread.php?t=76132") for sources.

Once you update your file you do the following to refresh the package list:

```

sudo apt-get update

```

You can do the same thing within Synaptic...there's more than one way to do most things.

---

### Post by nagudaku on 2006-02-15
[QUOTE=mlomker]This is the thread for discussing [the how-to]("http://ubuntuforums.org/showpost.php?p=423584") for installing the latest ATI driver that is working for Ubuntu, and troubleshooting the results.[/QUOTE]

just wanted to thank you for this howto. i was able to make the ATI driver to work for me on ubuntu/breezy amd64. thanks again !!

---

### Post by NunoCorreia on 2006-02-15
[QUOTE=shade11]-Is there anything I need to add in ininNG?[/QUOTE][This](http://ubuntuforums.org/showpost.php?p=435346&postcount=29) might be of use.

---

### Post by mclough on 2006-02-15
I can't get this right nomatter what i do i still come up with 
```
nice@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
this is how im installing maybe someone can help me i know im not doing some thind right 
```
nice@ubuntu:~$ sudo apt-get install gcc-3.4 module-assistant build-essential
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
module-assistant is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nice@ubuntu:~$ sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
gcc-3.3-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nice@ubuntu:~$ cd /home/nice/ati
nice@ubuntu:~/ati$ sudo sh ./ati-driver-installer-8.22.5-i386.run --buildpkg Ubuntu/breezy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.22.5...........................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/breezy
/tmp/fglrx ~/ati/fglrx-install
Package /home/nice/ati/xorg-driver-fglrx_8.22.5-1_i386.deb has been successfully generated
Package /home/nice/ati/xorg-driver-fglrx-dev_8.22.5-1_i386.deb has been successfully generated
Package /home/nice/ati/fglrx-kernel-source_8.22.5-1_i386.deb has been successfully generated
Package /home/nice/ati/fglrx-control_8.22.5-1_i386.deb has been successfully generated
Package /home/nice/ati/fglrx-sources_8.22.5-1_i386.deb has been successfully generated
~/ati/fglrx-install
Removing temporary directory: fglrx-install
nice@ubuntu:~/ati$ sudo dpkg -i ./xorg-driver-fglrx_8.22.5-1_i386.deb
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 77509 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_8.22.5-1_i386.deb) ...
Adding `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
Setting up xorg-driver-fglrx (8.22.5-1) ...

nice@ubuntu:~/ati$ sudo dpkg -i ./fglrx-control_8.22.5-1_i386.deb
Selecting previously deselected package fglrx-control.
(Reading database ... 77593 files and directories currently installed.)
Unpacking fglrx-control (from .../fglrx-control_8.22.5-1_i386.deb) ...
Setting up fglrx-control (8.22.5-1) ...
nice@ubuntu:~/ati$ sudo dpkg -i ./fglrx-kernel-source_8.22.5-1_i386.deb
(Reading database ... 77601 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.22.5-1 (using .../fglrx-kernel-source_8.22.5-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.22.5-1) ...
nice@ubuntu:~/ati$ sudo rm /usr/src/fglrx-kernel*.deb
nice@ubuntu:~/ati$ sudo module-assistant prepare
 apt-get  install linux-headers-2.6.12-9-386

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-9
The following NEW packages will be installed:
  linux-headers-2.6.12-9 linux-headers-2.6.12-9-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6725kB of archives.
After unpacking 70.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package linux-headers-2.6.12-9.
(Reading database ... 77601 files and directories currently installed.)
Unpacking linux-headers-2.6.12-9 (from .../linux-headers-2.6.12-9_2.6.12-9.23_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-9-386.
Unpacking linux-headers-2.6.12-9-386 (from .../linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb) ...
Setting up linux-headers-2.6.12-9 (2.6.12-9.23) ...

Setting up linux-headers-2.6.12-9-386 (2.6.12-9.23) ...

Done!
nice@ubuntu:~/ati$ sudo module-assistant update

Updated infos about 68 packages
nice@ubuntu:~/ati$ sudo module-assistant a-i fglrx
Reading package lists... Done
Building dependency tree... Done
fglrx-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Updated infos about 1 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2
modules/
modules/fglrx/
modules/fglrx/debian/
modules/fglrx/debian/changelog
modules/fglrx/debian/copyright
modules/fglrx/debian/compat
modules/fglrx/debian/rules
modules/fglrx/debian/control.template
modules/fglrx/debian/dirs.template
modules/fglrx/debian/postinst
modules/fglrx/agp3.c
modules/fglrx/agpgart_be.c
modules/fglrx/firegl_public.c
modules/fglrx/i7505-agp.c
modules/fglrx/nvidia-agp.c
modules/fglrx/agp_backend.h
modules/fglrx/agpgart.h
modules/fglrx/agp.h
modules/fglrx/drm_compat.h
modules/fglrx/drm.h
modules/fglrx/drm_os_linux.h
modules/fglrx/drmP.h
modules/fglrx/drm_proc.h
modules/fglrx/firegl_public.h
modules/fglrx/make.sh
modules/fglrx/libfglrx_ip.a.GCC2
modules/fglrx/libfglrx_ip.a.GCC3
modules/fglrx/libfglrx_ip.a.GCC4
modules/fglrx/Makefile
Done with /usr/src/fglrx-kernel-2.6.12-9-386_8.22.5-1+2.6.12-9.23_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.12-9-386.
(Reading database ... 91359 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.12-9-386 (from .../fglrx-kernel-2.6.12-9-386_8.22.5-1+2.6.12-9.23_i386.deb) ...
Setting up fglrx-kernel-2.6.12-9-386 (8.22.5-1+2.6.12-9.23) ...

nice@ubuntu:~/ati$ sudo aticonfig --initial
Using /etc/X11/xorg.conf
Uninitialised file found, configuring.
nice@ubuntu:~/ati$

```
and for  ldd /usr/bin/glxinfo i get 
```
nice@ubuntu:~$ ldd /usr/bin/glxinfo
        linux-gate.so.1 =>  (0xffffe000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7e41000)
        libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7dcb000)
        libglut.so.3 => /usr/lib/libglut.so.3 (0xb7da1000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d7f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c51000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7b91000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7b84000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7b72000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b6e000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7a88000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7a7d000)
        /lib/ld-linux.so.2 (0xb7eed000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a7a000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7a76000)
nice@ubuntu:~$



```
after the install and reboot the ati control is in the applications menu so 
if you can tell me what im doing wrong that would be great 
i just started using linux 4 days ago so im  realy new to this but i want to learn
thanks
and im runing a dell inspiron 9100 p4 2.8ghz 512mb ati mobility 9700

---

### Post by zi99y on 2006-02-16
Ok I've had a read through a good chunk of this thread and a search around but found no answers. Have done the howto - thanks, very nicely written - everything worked great straight away, but...

If I try to get to a virtual terminal (if thats what they're called) using ctrl-alt-F1 , the laptop will lock up on a blank screen. This is a real pain and only seems to happen with this version of flgrx as I was using the basic driver from the repos before and never had this problem. 

I hope there's a fix for this, has anyone else encountered it? I'm on an Acer 1694wlmi laptop with an x700 graphics chip.

---

### Post by mlomker on 2006-02-17
[QUOTE=mclough]
after the install and reboot the ati control is in the applications menu so 
[/QUOTE]

You'll need to look in /var/log/kern.log for fglrx driver info shortly after a boot-up and at /var/log/Xorg.0.log for other errors.  

The log of your install looks fine and the ldd info isn't relevant these days.

---

### Post by danmagicman7 on 2006-02-17
I've done the guide 3 times, and it has messed up each time. :-(

I have a Dell 2005FPW monitor as well, if that causes complications

Basically, I get an error saying fglrx cannot be found and something about GLcore could not be loaded.

I can boot back up into ati drivers at 640x480 which is...very annoying.

I have 2 of the Gnome ubuntu cores installed, my friend was helping me out and said the one with the .14 in it was more stable than the .15 for ATI.  Sorry, I don't have the full name.

I also am running a AMD64, but the ubuntu is 32-bit.  That shouldn't cause problems, right?

Here's my log.

```

X Window System Version 6.99.99.904 (7.0.0 RC 4)
Release Date: 14 December 2005
X Protocol Version 11, Revision 0, Release 6.99.99.904
Build Operating System:Linux 2.6.10 i686
Current Operating System: Linux drazbot 2.6.15-14-386 #1 PREEMPT Wed Jan 25 15:49:15 UTC 2006 i686
Build Date: 15 December 2005
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 17 13:00:52 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 2005FPW"
(**) |   |-->Device "ATI Technologies, Inc. R420 JP [Radeon X800XT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

bla bla bla....


(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2

bla bla bla...

(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. R420 JP [Radeon X800XT]".
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon X800XT (R420) JP (AGP) found

bla bla bla...this looks interesting, my resolution

(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)

```

The fglrx error isn't in there for some reason.

Help please?

Thanks!

---

### Post by Okami on 2006-02-17
I have tried mlomkers guide and the drivers install but when I try to reboot, xserver cant start. It doesnt start if I have "driver fglrx" in my xorg.conf file.
I am not sure if the drivers is the ones I really should use for my card, ATI Radeon 320m?
Thanks.

---

### Post by ipp3l1 on 2006-02-17
Great guide, it helped me a lot!

---

### Post by mclough on 2006-02-17
this is part of my log file i dont know what to look for ```


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-686-smp #1 SMP Mon Feb 13 12:23:58 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-686-smp (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Mon Feb 13 12:23:58 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 17 23:51:49 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig Screen 0" (0)
(**) |   |-->Monitor "aticonfig Monitor 0"
(**) |   |-->Device "ATI Graphics Adapter 0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

```

this is the error i see ```
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0be7000 at 0xb7a80000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(WW) fglrx(0): Failed to set up write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 800)
(II) fglrx(0): Largest offscreen area available: 1280 x 7387
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
```


when i first installed ubuntu the auto update upgraded me to 2.6.12-10 386
and now that i look back to the way i installed it the linux-headers-2.6.12-9-386 where used clould that be it 
and if so how can i fix that ?
i have a p4 2.8ghz with hyperthreading chip so i upgrade to the 2.6.12-10 686-smp and my laptop is 50% faster now  
and i get this on dmesg | grep fglrx
```
nice@ubuntu:~$ dmesg | grep fglrx
[4294730.593000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294730.595000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294730.595000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294732.169000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4294732.169000] [fglrx:firegl_unlock] *ERROR* Process 7576 using kernel context 0
[4296881.386000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4296881.387000] [fglrx:firegl_unlock] *ERROR* Process 10646 using kernel context 0
nice@ubuntu:~$


```




thanks

ps:is there a book on linux anyone can recommend i love the look and feel of 
linux vs windows

---

### Post by lanteau on 2006-02-18
I'm still getting the Mesa stuff, and I get this in the Xorg log.

```
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Also If I try to modprobe fglrx as root in a terminal I get this

```
FATAL: Error inserting fglrx (/lib/modules/2.6.15-14-686/misc/fglrx.ko): Invalid module format
```

I hope someone can help.

---

### Post by shade11 on 2006-02-19
Would it be possible that if I reconfigure xorg and change the memory settings for my video card it would work better?

---

### Post by dodgeman79 on 2006-02-20
i have been trying to get 8.22.5 installed and have been using all the good info in this thread.  but each time I get it installed and reboot my computer I get an error message for my xorg.conf.  so I restore a back up of xorg.conf and then boot up fine, and I get this from fglrxinfo.
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

so I finally figured out I have a Radeon Mobile 7500 that's built into a laptop and that this driver may not be compatible.  can someone comfirm this?  also what driver can I use because the drivers listed from ATI's site for my card take me off site and I get lost trying to find out how and what to use.

---

### Post by Septor on 2006-02-20
[QUOTE=dodgeman79]i have been trying to get 8.22.5 installed and have been using all the good info in this thread.  but each time I get it installed and reboot my computer I get an error message for my xorg.conf.  so I restore a back up of xorg.conf and then boot up fine, and I get this from fglrxinfo.
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

so I finally figured out I have a Radeon Mobile 7500 that's built into a laptop and that this driver may not be compatible.  can someone comfirm this?  also what driver can I use because the drivers listed from ATI's site for my card take me off site and I get lost trying to find out how and what to use.[/QUOTE]

The fglrx driver does not support anything before a Radeon 8500.  If you have a 7500 (check the output of "lspci") then use the "radeon" driver that is included with X.  You should get 3D acceleration with that driver.  Be sure to uninstall the fglrx packages though!

---

### Post by Septor on 2006-02-20
[QUOTE=mclough]
when i first installed ubuntu the auto update upgraded me to 2.6.12-10 386
and now that i look back to the way i installed it the linux-headers-2.6.12-9-386 where used clould that be it 
and if so how can i fix that ?
i have a p4 2.8ghz with hyperthreading chip so i upgrade to the 2.6.12-10 686-smp and my laptop is 50% faster now  
[/QUOTE]


After a kernel upgrade you will need to re-build the fglrx kernel driver.  You can usually do that by running the following commands:
```

rm /usr/src/fglrx-kernel*.deb
rm /usr/src/linux
m-a prepare
m-a update
m-a a-i fglrx

```

Also, I think you have the "linux-restricted-modules" package installed, so you will need to uninstall that as well.  There is more info at [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by MAbans on 2006-02-20
Followed the instructions to the T.. Worked like a charm. Thanks.. saving the post for future reference.. 10! \\:D/ \\:D/ \\:D/ \\:D/

---

### Post by demonhunter on 2006-02-20
hello dudes...

I followed all instructions a thousand times but when I finish the proccess, when I reboot my machine and the X server is starting, my screen gets black and my system freezes. I'm using linux 5.10 (breezy) on a hp pavilion zv6000 and the videocard is an ATI 200M. :( 

have you all seem some problem like this?? I have already tried to update from breezy to dapper, I've tried to configure the latest driver and the 8.16.xx drivers. I've tried to edit my xorg.conf, changing the Horizontal and Vertical refresh rate, but nothing seemed to work. Everytime that I disable DRI, the xserver goes up perfectly and everytime that I enable DRI, my system freezes during xserver start up. :cry: 

I read something about this problem, telling that this is a problem between xorg and ATI driver, and told that maybe next Xorg will fix this issue. [-( 

does anyone have some information or can help me? :confused: 

thanks. ;)

---

### Post by tamoroso on 2006-02-20
Most excellent HOWTO; solved my problem pronto.  Thanks!

---

### Post by tamoroso on 2006-02-20
Did you replace the DRI library?  There's a step in the HOWTO for it-look at the AMD64 specific instructions (scroll down a bit); I had to replace libdri.a (instructions are here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584).

You may also have to turn off int10 (scroll further down in the HOWTO...); I did, when I got the error message the HOWTO mentions.

Good luck!

---

### Post by oceanelement on 2006-02-21
the tutorial worked great for me. thanks for your help in setting up the howto. the best of luck to others.

eli

p.s. the setup for this system is dapper flight 4. the only thing i changed was the ubuntu/breezy to ubuntu/dapper.

---

### Post by demonhunter on 2006-02-21
hello tamoroso,

I have copied the libdri.a (downgraded it) that is in the site and have commented the line wichi has "int10" in xorg.conf. I will try to follow all the steps again...

but just one question... are you all making it work with the latest drivers or are you all using other drivers or the drivers that came with ubuntu???

thanks.

---

### Post by DonQuixote on 2006-02-21
Just a note on sound and the latest ATI drivers.

I have an ATI Mobility Radeon 9600 on my laptop (Sager 5680) and the installation of the 8.22.5 drivers breaks my sound.

I get the drum sound on the login screen TWICE (as opposed to the normal once), and then the sound is no more.

I still don't have a solution for this, but it appears (from my limited experience and knowledge) that this version of the video driver messes with the sound somehow. ;)

Added info:

I walked back along the preceeding versions until I finally found that the ATI video drivers version 8.19.10 worked without destroying my sound.

JFYI

---

### Post by mlomker on 2006-02-21
[QUOTE=danmagicman7]The fglrx error isn't in there for some reason.
[/QUOTE]

I didn't see anything in the snippets that you posted but they weren't complete logs.  I'm unfamiliar with what problems might occur with a newer kernl (the how-to has only been tested through for 2.6.12-10.  I also know that there are a variety of problems with the X-series boards, but from what I see in your output it seemed to be finding it okay.

I'd recommend the Rage3D board.  Either that or go back to the stock kernel and post your complete logs in a new message and send me a link.  I don't have an X-series card but I have a fairly good eye for reading log files.

---

### Post by mlomker on 2006-02-21
[QUOTE=Okami]Radeon 320m?[/QUOTE]

No, that chipset is too old.  You'll need to stick with the ATI driver.

---

### Post by mlomker on 2006-02-21
[QUOTE=mclough][4294730.595000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[/quote]

That's the wrong kernel driver.  You probably did one of the following:

1) Failed to reboot after the install and had the old driver loading from /etc/modules
2) Didn't remove restricted-modules
3) Didn't run the module-assistant steps

For a linux book I'd strongly recommend [How Linux Works]("http://www.amazon.com/gp/product/1593270356").  It's a great book for a Windows power-user that is looking to make the move.

---

### Post by mlomker on 2006-02-21
[QUOTE=lanteau]
```
FATAL: Error inserting fglrx (/lib/modules/2.6.15-14-686/misc/fglrx.ko): Invalid module format
```
[/QUOTE]

I don't know if 2.6.15 is supported by the driver.  The Rage3D board would be your best bet.

---

### Post by mlomker on 2006-02-21
[QUOTE=dodgeman79]so I finally figured out I have a Radeon Mobile 7500 that's built into a laptop and that this driver may not be compatible.[/QUOTE]

ATI doesn't offer hardware acceleration on that card.  You'll have to use the ATI driver and MESA (software 3D).

---

### Post by mlomker on 2006-02-21
[QUOTE=demonhunter]I read something about this problem, telling that this is a problem between xorg and ATI driver, and told that maybe next Xorg will fix this issue. [-( [/QUOTE]

Not sure what to suggest other than looking to see if the log files tell you anything.  Hardware lock-ups (Ctrl-Alt-F2 doesn't work) are not software problems.  I'd start by making sure you system BIOS is the latest and perhaps pull any unecessary cards/USB devices/etc. as you would for any hardware problem.

---

### Post by wsmoser2004 on 2006-02-21
I seem to have the same problem as demonhunter....

Everything seems to install just fine when I follow the how-to, except that when I reboot I get a blank screen.  It seems like the computer (a laptop by the way) is oblivious to the fact that my screen is black...I hear the KDE log-in sound so I assume that the computer thinks it is booted into the KDE desktop.  I also cannot do a Ctrl-Alt-F1 (nothing happens), so I have to then reboot into the recovery console and restore my xorg.conf back to the one that uses the default "ati" kernel driver.  I should also mention that the "fglrx" driver that comes with Breezy works just fine, except that the laptop is a widescreen and apparently that version of fglrx does not support widescreen formats very well.

I can attach my entire Xorg.0.log, but it is really big.  The part that stuck out most to me was:
```

(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023

```
The following part is repeated many many many times (250 or so); each time the line **/dev/dri/card2** increments (to **/dev/dri/card3, /dev/dri/card4**) until is gets to around **/dev/dri/card254** or so:
```

drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023

```

I can also post my kern.log, but here is the part that concerns fglrx:
```

Feb 21 14:34:22 localhost kernel: [4294733.833000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 21 14:34:22 localhost kernel: [4294733.836000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
Feb 21 14:34:22 localhost kernel: [4294733.836000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0C2] -> GSI 10 (level, low) -> IRQ 10
Feb 21 14:34:22 localhost kernel: [4294733.836000] [fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
Feb 21 14:34:22 localhost kernel: [4294734.089000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Feb 21 14:34:22 localhost kernel: [4294734.089000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Feb 21 14:34:22 localhost kernel: [4294734.089000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Feb 21 14:34:22 localhost kernel: [4294734.089000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Feb 21 14:34:22 localhost kernel: [4294734.090000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb 21 14:34:22 localhost kernel: [4294734.090000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Feb 21 14:34:22 localhost kernel: [4294734.090000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Feb 21 14:34:22 localhost kernel: [4294734.090000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] free  AGP = 256126976
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] max   AGP = 256126976
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] free  LFB = 8413184
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] max   LFB = 8413184
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] free  Inv = 0
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] max   Inv = 0
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] total Inv = 0
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] total TIM = 0
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] total FB  = 0
Feb 21 14:34:22 localhost kernel: [4294734.277000] [fglrx] total AGP = 65536
Feb 21 14:35:01 localhost kernel: [4294772.874000] mtrr: no MTRR for 98000000,800000 found
Feb 21 14:35:01 localhost kernel: [4294772.874000] mtrr: no MTRR for 98800000,100000 found
Feb 21 14:35:01 localhost kernel: [4294772.874000] mtrr: no MTRR for 98900000,40000 found
Feb 21 14:35:01 localhost kernel: [4294772.874000] mtrr: no MTRR for 98940000,10000 found
Feb 21 14:35:01 localhost kernel: [4294772.874000] mtrr: no MTRR for 98950000,4000 found
Feb 21 14:35:01 localhost kernel: [4294773.275000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Feb 21 14:35:01 localhost kernel: [4294773.275000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Feb 21 14:35:01 localhost kernel: [4294773.275000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
Feb 21 14:35:01 localhost kernel: [4294773.276000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb 21 14:35:01 localhost kernel: [4294773.276000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Feb 21 14:35:01 localhost kernel: [4294773.276000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Feb 21 14:35:01 localhost kernel: [4294773.276000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] free  AGP = 256126976
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] max   AGP = 256126976
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] free  LFB = 8413184
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] max   LFB = 8413184
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] free  Inv = 0
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] max   Inv = 0
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] total Inv = 0
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] total TIM = 0
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] total FB  = 0
Feb 21 14:35:01 localhost kernel: [4294773.405000] [fglrx] total AGP = 65536

```

Does this mean anything to anybody?

---

### Post by nhwk64 on 2006-02-21
Can't seem to make the package.. 

```
X_VERSION=x690_64a sh ./ati-driver-installer-8.22.5-x86_64.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.22.5......................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
/tmp/fglrx ~/Desktop/driver/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.22.5-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
dh_testdir
dh_testdir
 fakeroot debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#//g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -p-driver-fglrx \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/dri \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                usr/share/fglrx/diversions
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -p-driver-fglrx \
                usr/lib32 \
                usr/lib32/xorg/modules \
                usr/lib32/xorg/modules/dri \
                usr/lib32/xorg/modules/drivers \
                usr/lib32/xorg/modules/linux \
                etc/X11/Xsession.d
dh_installdirs -p-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
                usr/bin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pfglrx-sources \
                usr/src
dh_install
# Driver package
dh_install -p-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -p-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
# amd64 needs some library redirection
dh_install -p-driver-fglrx "usr/X11R6/lib64/*.so*"     "usr/lib"
dh_install -p-driver-fglrx "usr/X11R6/lib64/modules/*" "usr/lib/xorg/modules"
dh_install -p-driver-fglrx "usr/X11R6/lib/*.so*"       "usr/lib32"
dh_install -p-driver-fglrx "usr/X11R6/lib/modules/*"   "usr/lib32/xorg/modules"
dh_install -p-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
# Driver dev package
dh_install -p-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/lib"
dh_install -p-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -p-driver-fglrx-dev "usr/include/*"       "usr/include"
# Kernel source package
dh_install -pfglrx-kernel-source \
                lib/modules/fglrx/build_mod/*.c            \
                lib/modules/fglrx/build_mod/*.h            \
                lib/modules/fglrx/build_mod/*.sh           \
                lib/modules/fglrx/build_mod/lib*           \
                lib/modules/fglrx/build_mod/2.6.x/Makefile \
                usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debian"
dh_install -pfglrx-kernel-source  \
                debian/copyright        \
                debian/compat           \
                module/rules            \
                module/control.template \
                module/dirs.template    \
                module/postinst         \
                usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
         && chown -R root:src modules \
         && tar -c modules | bzip2 > fglrx.tar.bz2 \
         && rm -rf modules)
# control panel package
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel"     "usr/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/icons"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/pixmaps"
dh_install -A -pfglrx-control "debian/fireglcontrol.desktop"      "usr/share/gnome/apps"
dh_install -A -pfglrx-control "debian/fireglcontrol.kdelnk"       "usr/share/applnk"
# control panel source package
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -p-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc++.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find path for libXrender.so.1
dpkg-shlibdeps: warning: could not find path for libXxf86vm.so.1
dpkg-shlibdeps: warning: could not find path for libXft.so.2
dpkg-shlibdeps: warning: could not find path for libXcursor.so.1
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXmu (soname 6, path /usr/lib32/libXmu.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libICE (soname 6, path /usr/lib32/libICE.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libSM (soname 6, path /usr/lib32/libSM.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXext (soname 6, path /usr/lib32/libXext.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libfontconfig (soname 1, path /usr/lib32/libfontconfig.so.1, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libexpat (soname 0, path /usr/lib32/libexpat.so.0, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXinerama (soname 1, path /usr/lib32/libXinerama.so.1, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXrender.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXrender (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXrandr (soname 2, path /usr/lib32/libXrandr.so.2, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libfreetype (soname 6, path /usr/lib32/libfreetype.so.6, dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXxf86vm.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXxf86vm (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXft.so.2)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXft (soname 2, path , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXcursor.so.1)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXcursor (soname 1, path , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc++.so.5, dependency field Depends)
dh_gencontrol -- -VXVERSION= -VXVERSIONMAX=.99 -VXTYPE= -VXSERVER=
dpkg-gencontrol: warning: can't parse dependency -driver-fglrx
dpkg-gencontrol: warning: can't parse dependency -driver-fglrx
dpkg-gencontrol: warning: can't parse dependency -driver-fglrx
dpkg-gencontrol: warning: can't parse dependency -driver-fglrx-dev
dh_md5sums
dh_builddeb
dpkg-deb: parse error, in file `debian/-driver-fglrx/DEBIAN/control' near line 1:
 invalid package name (must start with an alphanumeric)
dh_builddeb: command returned error code 512
make: *** [binary] Error 1
~/Desktop/driver/fglrx-install
Removing temporary directory: fglrx-install

```

---

### Post by mlomker on 2006-02-22
[QUOTE=wsmoser2004]Does this mean anything to anybody?[/QUOTE]

This indicates a video memory problem:

```

mtrr: no MTRR for 98000000,800000 found

```

I have a link on the how-to for a particular MTRR error.  You could start by taking a look at that thread and then Google for the above.

---

### Post by mlomker on 2006-02-22
[QUOTE=nhwk64]Can't seem to make the package.. 

```

dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc++.so.5, dependency field Depends)
...

```

It appears that you are missing a number of default packages.  Did you start by verifying that all of those packages are installed?  Install the apt-file package and then run **sudo apt-file update**.  Here is how it works:

```

mlomker@mlomkernote:/$ apt-file search libXrender.so.1
libxrender1: usr/lib/libXrender.so.1
libxrender1: usr/lib/libXrender.so.1.3.0
libxrender1-dbg: usr/lib/debug/usr/lib/libXrender.so.1.3.0 

```

It will give you the names of the packages that a file is in.  You can then search on the files that cannot be found and make sure that the corresponding packages are installed.

My only guess is that you tried to clean up your system by removing extra packages and went overboard.  You shouldn't get these errors on a clean install of Breezy.

---

### Post by DavidRibeiro on 2006-02-23
Hi, I've an Asus Pundit-r350 with onboard ATI chip radeon9100. I've done all the steps to install the ATI driver 8.22.5. But, a weird think happen. The *xorg-driver-fglrx* package generated by the installer does'nt have *fglrxconfig*. Anybody knows what's the problem? I want to configure the xorg.conf but it is impossible to do it without *fglrxconfig*.

thank you

---

### Post by combat squirrel on 2006-02-23
Hey all did the driver update for my Radeon 9100 AGP card from these instructions:

[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

all went well, all files compiled etc and i even now have the ati control panel under applications

However it doesnt seem to want to be using the ATI driver and carrys on with the mesa driver, went to the xorg.conf and found this:


Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9100 (R200 QM)"
Driver "ati"
Option "UseFBDev" "true"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Graphics Adapter 0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

*************************************** (yes 2 lines for ati stuff)

So obviously changed it to :


Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9100 (R200 QM)"
Driver "fglrx"
Option "UseFBDev" "true"
BusID "PCI:1:0:0"
EndSection

Section "Device"
Identifier "ATI Graphics Adapter 0"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

************************************************** ***

And rebooted, but again its still using the MESA driver, how do i force it use ati's driver?

cheers folks

---

### Post by pestilence on 2006-02-23
Could you paste the output of your Xorg.0.log file? (located in /var/log)
Why didn't you run the fglrxconfig tool?

---

### Post by combat squirrel on 2006-02-23
Also iv just updated the kernal 2.6.12-10-686
 as i was running the 386 version

rmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xe0b74000
(II) fglrx(0): [drm] mapped SAREA 0xe0b74000 to 0xb7a48000
(II) fglrx(0): [drm] framebuffer handle = 0xf0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0b74000 at 0xb7a48000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xf0000000 FBMappedSize: 0x04000000
(==) fglrx(0): Write-combining range (0xf0000000,0x4000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 768)

---

### Post by combat squirrel on 2006-02-23
ok think iv spotted it myself, 3d driver doesnt match kernal driver. i have JUST updated the 686 kernal driver to 2.6.12-10-686, how do I update this to the required driver from ATI ? I dont have a clue :S

---

### Post by combat squirrel on 2006-02-23
ok iv been looking back through this thread and found instructions like:

rm /usr/src/fglrx-kernel*.deb to rebuild the kernal driver for 686 etc, i get the jist of what I have to do:
1)update kernal again to the kernal supported by ati driver
2) rebuild fglrx stuff match this kernal
3) force it to work and load with ubuntu 

then should have working 3d acceleration, but im not sure of the commands to type, when i ran rm /usr/src/fglrx-kernel*.deb, it said permission denied

---

### Post by combat squirrel on 2006-02-23
OK just reinstalled all the ATI stuff, but same prob, not loadin fglrx, same prob as above, PLEASE SOMEONE HELP ! :(

---

### Post by mlomker on 2006-02-23
[QUOTE=DavidRibeiro]Anybody knows what's the problem? I want to configure the xorg.conf but it is impossible to do it without *fglrxconfig*.
[/QUOTE]

It was replaced with aticonfig.

---

### Post by mlomker on 2006-02-23
[QUOTE=combat squirrel]Hey all did the driver update for my Radeon 9100 AGP card from these instructions:[/QUOTE]

Is it the 9100 IGP or the regular card?  The IGP is not supported.

---

### Post by mlomker on 2006-02-23
[QUOTE=combat squirrel]Also iv just updated the kernal 2.6.12-10-686
 as i was running the 386 version[/QUOTE]

You need to remove the restricted-modules package.  You have to run the **m-a** steps again if you change the kernel.

---

### Post by WackToMack on 2006-02-23
Hello everyone.  I'd just like to know if my ATI Radeon X800XT graphics card is supported since the x1x00 aren't.  Thanks in advance. :D

---

### Post by combat squirrel on 2006-02-23
hi mlonker, im back on the 386 distro now, as linux crashed and wasnt recoverable, no idea what happened, anyways back to square one

its a radeon 9100 AGP regualar card, tried installing it the 'quick way' again no, go, back to problems previously described, any ideas Mr Mlonker ? :)

---

### Post by thieves.honor on 2006-02-24
hey there.  Here's my problem.  I have a Dell Inspiron 6000 laptop with an ATI x300 card in it.  Currently running Ubuntu 5.10.  I followed the walkthrough on installing the latest driver without a problem.  fglrxinfo shows correct

thieveshonor@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5642 (8.22.5)

The problem is with my 3d acceleration.  fgl_glxgears output is consistantly under 500

thieveshonor@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1757 frames in 5.0 seconds = 351.400 FPS
2178 frames in 5.0 seconds = 435.600 FPS
2179 frames in 5.0 seconds = 435.800 FPS
2171 frames in 5.0 seconds = 434.200 FPS
2172 frames in 5.0 seconds = 434.400 FPS
2180 frames in 5.0 seconds = 436.000 FPS
2178 frames in 5.0 seconds = 435.600 FPS
2181 frames in 5.0 seconds = 436.200 FPS
2173 frames in 5.0 seconds = 434.600 FPS
2173 frames in 5.0 seconds = 434.600 FPS
2186 frames in 5.0 seconds = 437.200 FPS
2182 frames in 5.0 seconds = 436.400 FPS
2176 frames in 5.0 seconds = 435.200 FPS
2171 frames in 5.0 seconds = 434.200 FPS
2186 frames in 5.0 seconds = 437.200 FPS
2177 frames in 5.0 seconds = 435.400 FPS
2185 frames in 5.0 seconds = 437.000 FPS
2178 frames in 5.0 seconds = 435.600 FPS
2158 frames in 5.0 seconds = 431.600 FPS

any suggestions on how to fix this??

---

### Post by Des33 on 2006-02-25
does this at all work for the ATi radeon xpress 200m?

its not much different than the x300..

no matter what i try i can only get it to work with vesa..

**edit... got it going.... yay! but its still using the mesa driver** heres a section of my xorg log...

```

(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON XPRESS 200M (RS480 5955)" (Chipset = 0x5955)
(--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x30a4)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xc0100000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON XPRESS 200M Series
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: MS48
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/X11R6/lib/modules/linux/libdrm.a
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a

```

notice it says fglrx failed.. anyone know the reason?

thanks

---

### Post by adam.tropics on 2006-02-26
Having a go with Dapper, and pretty impressed except...

When I get to > sudo m-a a-i fglrx I get errors  as follows
[HTML]debian/rules:77: *** missing separator (did you mean TAB instead of 8
 &#9474; spaces?).  Stop. [/HTML]

It half works in the sense that I am then able to get Mesa, but clearly I would like ATI fglrx to show up, any ideas??

---

### Post by johnnyr on 2006-02-26
> **adam.tropics]Having a go with Dapper, and pretty impressed except...

When I get to  I get errors  as follows
[HTML]debian/rules:77: *** missing separator (did you mean TAB instead of 8
 &#9474 said:**
> 

It half works in the sense that I am then able to get Mesa, but clearly I would like ATI fglrx to show up, any ideas??

I'm having the same issue.

On a Dell 8250 with an ATI 9700.

I tried the same on a IBM Thinkpad T42 and this command ran properly.

---

### Post by adam.tropics on 2006-02-26
Fixed that by editing the debian/rules file within the fglrx source (tar.gz) file, but now get a makefile error


[HTML]make[2]: *** No rule to make target `Makefile'.  Stop.                     
 &#9474; make[2]: Leaving directory                                                 
 &#9474; `/usr/src/modules/fglrx-kernel/fglrx/build_mod/2.6.x'                      
 &#9474; make[1]: *** [build-stamp] Error 2                                         
 &#9474; make[1]: Leaving directory `/usr/src/modules/fglrx-kernel'                 
 &#9474; make: *** [kdist_image] Error 2
[/HTML]

still, it's progress!!!!!

---

### Post by fallencan on 2006-02-26
i'm new to linux and ubuntu

i installed the the latest ati drivers by following the instructions from how-to on first page of this tread. everything went ok until i reboot my system. x refused to start. i checked the error message and it says my card is not in list. i'm using a mobility radeon 9700se (chip id 4e52) i searched the forum and find a similiar problem and it suggest adding chipid 0x4e50 to xorg.conf. i added and x works ok. but the drivers section and fglrxinfo says im using mesa drivers. any suggestions?

---

### Post by mlomker on 2006-02-27
[QUOTE=WackToMack]Hello everyone.  I'd just like to know if my ATI Radeon X800XT graphics card is supported since the x1x00 aren't.  Thanks in advance. :D[/QUOTE]

I've heard from a number of people that they do work.

---

### Post by mlomker on 2006-02-27
[QUOTE=combat squirrel]its a radeon 9100 AGP regualar card, tried installing it the 'quick way' again no, go, back to problems previously described, any ideas Mr Mlonker ? :)[/QUOTE]

What do you mean by the 'quick way'?  I'm really only interested in supporting this how-to.  If you did a clean installation then that'd be a good point to troubleshoot from.  I'd recommend starting a new thread and attaching your various log files to it.  PM me with a link and I'll take a look at it.

---

### Post by mlomker on 2006-02-27
[QUOTE=thieves.honor]any suggestions on how to fix this??[/QUOTE]

I'm not sure what the normal performance is for that card and it probably varies depending upon the design of the laptop (it isn't a high-end card).  My Mobility 9700 Pro averages 460 on that test.

You could try the Rage3D board.  I only want to support the installation on this thread and not performance or game issues.

---

### Post by mlomker on 2006-02-27
[QUOTE=Des33]notice it says fglrx failed.. anyone know the reason?
[/QUOTE]

Look in kern.log shortly after you boot up.

---

### Post by mlomker on 2006-02-27
[QUOTE=adam.tropics]It half works in the sense that I am then able to get Mesa, but clearly I would like ATI fglrx to show up, any ideas??[/QUOTE]

I am not going to support Dapper in this thread until about two weeks prior to release.  Dapper uses a newer kernel and I don't think ATI supports it yet (nevermind the fact that packages are always in flux and things might be broken on the Ubuntu side at any given point).

You should jump on the Rage3D board and look for 'Septor'.  He is the guy that packages the ATI drivers for Ubuntu and could fix the problem if it is on the ATI side (might be a Ubuntu issue).

---

### Post by mlomker on 2006-02-27
[QUOTE=fallencan]ok. but the drivers section and fglrxinfo says im using mesa drivers. any suggestions?[/QUOTE]

Examine the log files.  Create a new thread and attach them if you don't see anything.

---

### Post by fallencan on 2006-02-27
[QUOTE=mlomker]Examine the log files.  Create a new thread and attach them if you don't see anything.[/QUOTE]

thanks for the advice. but since im new to linux can u direct me to how to attach them?

---

### Post by Bloged on 2006-02-27
I've been trying to get the ATI drivers working for a few days now... I've followed [this]("http://ubuntuforums.org/showpost.php?p=423584") How-To for installation... everything goes flawlessly but after restart **fglrxinfo** gives"
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

When checking **/var/log/kern.log** for errors I found this:
```
Feb 27 20:19:28 localhost kernel: [4294714.728000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 27 20:19:28 localhost kernel: [4294714.733000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
Feb 27 20:19:28 localhost kernel: [4294714.733000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 27 20:19:28 localhost kernel: [4294714.733000] [fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
Feb 27 20:19:29 localhost kernel: [4294715.857000] mtrr: type mismatch for e8000000,8000000 old: write-back new: write-combining
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Feb 27 20:19:29 localhost kernel: [4294715.857000] mtrr: type mismatch for f8000000,4000000 old: write-back new: write-combining
Feb 27 20:19:29 localhost kernel: [4294715.859000] [fglrx:firegl_unlock] *ERROR* Process 7654 using kernel context 0
Feb 27 20:19:29 localhost kernel: [4294715.913000] mtrr: type mismatch for e8000000,8000000 old: write-back new: write-combining
```

For those intrested in my **xorg.conf**:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig Screen 0" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/CID"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load  "GLcore"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "LS902U"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Monitor    "LS902U"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig Screen 0"
        Device     "ATI Graphics Adapter 0"
        Monitor    "aticonfig Monitor 0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection
```

When commenting the following X-server isn't started at all any more
```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection
```

The videocard I'm using is the found: ATI Technologies, Inc. Radeon 9200 SE (RV280)!

Thanks in advance for any help! If you need anything else (configuration/logs) I'm happy to provide it!

Grtz,

Bloged

---

### Post by torx on 2006-02-27
i have the same problem as the guy above and have tried unsuccessfully for almost 2 weeks now. on the verge of giving up now

---

### Post by dwessell on 2006-02-27
Great How To!! Thanks a ton!!

I do have one question.. I have installed the drivers, but I can't find/figure out how to activate the TV-OUT function.. Is it something in the config file, and then a keystroke to activate it??

Thanks
David

---

### Post by Bloged on 2006-02-28
[QUOTE=Bloged]...[cut]...

When checking **/var/log/kern.log** for errors I found this:
```
Feb 27 20:19:28 localhost kernel: [4294714.728000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 27 20:19:28 localhost kernel: [4294714.733000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
Feb 27 20:19:28 localhost kernel: [4294714.733000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 27 20:19:28 localhost kernel: [4294714.733000] [fglrx] module loaded - fglrx 8.22.5 [Feb  7 2006] on minor 0
Feb 27 20:19:29 localhost kernel: [4294715.857000] mtrr: type mismatch for e8000000,8000000 old: write-back new: write-combining
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
Feb 27 20:19:29 localhost kernel: [4294715.857000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Feb 27 20:19:29 localhost kernel: [4294715.857000] mtrr: type mismatch for f8000000,4000000 old: write-back new: write-combining
Feb 27 20:19:29 localhost kernel: [4294715.859000] [fglrx:firegl_unlock] *ERROR* Process 7654 using kernel context 0
Feb 27 20:19:29 localhost kernel: [4294715.913000] mtrr: type mismatch for e8000000,8000000 old: write-back new: write-combining
```

...[cut]...[/QUOTE]

[QUOTE=torx]i have the same problem as the guy above and have tried unsuccessfully for almost 2 weeks now. on the verge of giving up now[/QUOTE]

Ok I got one step further along the line; by following [this]("http://ubuntuforums.org/showthread.php?t=115104") howto, which applied to me. So now no mtrr errors anymore.

Now my **/var/log/kern.log** shows:
```

Feb 28 11:41:59 localhost kernel: [4294689.772000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Feb 28 11:41:59 localhost kernel: [4294689.775000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
Feb 28 11:41:59 localhost kernel: [4294689.775000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 28 11:41:59 localhost kernel: [4294689.775000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
................
[fglrx:firegl_unlock] *ERROR* Process 7713 using kernel context 0
```

Now I got a new error :-k and fglrx 8.16.20 is loaded while I'm installing the ATI 8.22.5 drivers!

I changed the following in my /etc/X11/xorg.conf
```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

```
to
```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

```

Hopefully this helps someone else one step further. And is somebody able to help me making the final steps towards having the ATI drivers loaded.\\:D/ 

Grtz, Bloged

---

### Post by mlomker on 2006-02-28
[QUOTE=fallencan]thanks for the advice. but since im new to linux can u direct me to how to attach them?[/QUOTE]

This might be a good question for the Absolute Beginner forum or perhaps the Site forum.  Attaching a text file to a post here on the forum isn't a linux issue--it'd be the same process if you accessed this board from Windows.

You'd rename the log file to .txt from .log and then attach it using the 'Manage Attachments' button.

---

### Post by mlomker on 2006-02-28
[QUOTE=Bloged]Hopefully this helps someone else one step further. And is somebody able to help me making the final steps towards having the ATI drivers loaded.[/QUOTE]

I'd assume that you didn't remove restricted-modules and it overwrote the newer module.  Remove it and re-run the **sudo m-a a-i fglrx** command.

---

### Post by mlomker on 2006-02-28
[QUOTE=dwessell]Is it something in the config file, and then a keystroke to activate it??[/QUOTE]

I've personally never gotten it to work on my laptop, but I know that others have.  Try **sudo aticonfig** at a prompt.  The switches are --tvs and --tvf.

---

### Post by SmasSive on 2006-02-28
I can't build the package...

```
root@mordor /home/smassive/Downloads/ATI $ sh ati-driver-installer-8.22.5-i386.run --buildpkg Ubuntu/dapper
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.22.5.....................................................................................................                                                              ......................................................................................................................................................                                                              ................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/dapper
/tmp/fglrx /home/smassive/Downloads/ATI/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.22.5-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
make: se ingresa al directorio `/tmp/fglrx'
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
dh_testdir
dh_testdir
make: se sale del directorio `/tmp/fglrx'
 fakeroot debian/rules binary
make: se ingresa al directorio `/tmp/fglrx'
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/dri \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                usr/share/fglrx/diversions
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
                usr/bin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pfglrx-sources \
                usr/src
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/*" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib/*.a"   "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
# Kernel source package
dh_install -pfglrx-kernel-source \
                lib/modules/fglrx/build_mod/*.c            \
                lib/modules/fglrx/build_mod/*.h            \
                lib/modules/fglrx/build_mod/*.sh           \
                lib/modules/fglrx/build_mod/lib*           \
                lib/modules/fglrx/build_mod/2.6.x/Makefile \
                usr/src/modules/fglrx
dh_install -pfglrx-kernel-source "debian/changelog" "usr/src/modules/fglrx/debian"
dh_install -pfglrx-kernel-source  \
                debian/copyright        \
                debian/compat           \
                module/rules            \
                module/control.template \
                module/dirs.template    \
                module/postinst         \
                usr/src/modules/fglrx/debian
(cd debian/fglrx-kernel-source/usr/src \
         && chown -R root:src modules \
         && tar -c modules | bzip2 > fglrx.tar.bz2 \
         && rm -rf modules)
# control panel package
dh_install -A -pfglrx-control "usr/X11R6/bin/fireglcontrolpanel"     "usr/bin"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/icons"
dh_install -A -pfglrx-control "usr/share/icons/ati.xpm"           "usr/share/pixmaps"
dh_install -A -pfglrx-control "debian/fireglcontrol.desktop"      "usr/share/gnome/apps"
dh_install -A -pfglrx-control "debian/fireglcontrol.kdelnk"       "usr/share/applnk"
# control panel source package
dh_install -pfglrx-sources "usr/src/*" "usr/src"
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_dm.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_gamma.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libfglrx_pp.so.1.0
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/libGL.so.1.2
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/dri/fglrx_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/dri/atiogl_a_dri.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/drivers/fglrx_drv.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note --strip-unneeded debian/xorg-driver-fglrx/usr/lib/xorg/modules/linux/libfglrxdrm.so
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fgl_glxgears
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/fglrxinfo
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/xorg-driver-fglrx/usr/bin/aticonfig
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libaticonfig.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_dm.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_gamma.a
+ /usr/bin/strip --strip-debug debian/xorg-driver-fglrx-dev/usr/lib/libfglrx_pp.a
+ /usr/bin/strip --remove-section=.comment --remove-section=.note debian/fglrx-control/usr/bin/fireglcontrolpanel
dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/i486-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/i486-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/i486-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/i486-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_gamma.so.1 not found.
dpkg: /usr/i486-linux-gnu/lib/libfglrx_pp.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: se sale del directorio `/tmp/fglrx'
/home/smassive/Downloads/ATI/fglrx-install
Removing temporary directory: fglrx-install
```

I don't know why search in /usr/i486-linux-gnu directory, it doesn't exists.
The result of locate:
```
root@mordor /home/smassive/Downloads/ATI $ locate libm.so.6
/lib/libm.so.6
/lib/tls/libm.so.6
/lib/tls/i686/cmov/libm.so.6
```

Any ideas? Thanks!

---

### Post by Bloged on 2006-02-28
[QUOTE=mlomker]I'd assume that you didn't remove restricted-modules and it overwrote the newer module.  Remove it and re-run the **sudo m-a a-i fglrx** command.[/QUOTE]

That worked like a charm! Only had to edit the /etc/X11/xorg.conf to work with the gflrx drivers instead of the ati!

Thanks,

Bloged

---

### Post by fallencan on 2006-02-28
[QUOTE=mlomker]This might be a good question for the Absolute Beginner forum or perhaps the Site forum.  Attaching a text file to a post here on the forum isn't a linux issue--it'd be the same process if you accessed this board from Windows.

You'd rename the log file to .txt from .log and then attach it using the 'Manage Attachments' button.[/QUOTE]

my problem is not the attaching. i dont know which files to attach. or how to generate text files from error messages.

---

### Post by mlomker on 2006-02-28
[QUOTE=SmasSive]Any ideas? Thanks![/QUOTE]

I heard from somebody else that also said it was broke.  Try the Rage3D board for help.  I'm only supporting Breezy until early April.

---

### Post by mlomker on 2006-02-28
[QUOTE=fallencan]i dont know which files to attach. or how to generate text files from error messages.[/QUOTE]

As mentioned toward the end of the how-to, the log files are /var/log/Xorg.0.log and /var/log/kern.log.  You'll need to get the logs during the failed boot because the Xorg file gets overwritten every time that X starts.

---

### Post by event on 2006-03-01
Does anyone yet know of a way to get fglrx working with a Radeon Mobility M6 LY?

---

### Post by KooT on 2006-03-02
Hello.
I have problem with KDE 3.5.1.
After upgrade and install xorg-driver-fglrx (i have ati radeon 9100 video card - 0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R200 QM [Radeon 9100]) my kde crash on start up - on dialog - "Setting up previous session". I try to startx from new user and then its hang up on 'Seting desktop'.

I think its something wrong with fglrx driver becouse when i change it into 'ati' in xorg.conf its working ok - only i cant set up high refresh rate on my monitor.

Any idea what is wrong? And where can i find some kde/xorg logs to find out what is wrong?

---

### Post by KooT on 2006-03-02
I found it in /var/log/daemon.log
```
 
Feb 28 18:01:47 localhost kdm_greet[8139]: Internal error: memory corruption detected
Feb 28 18:01:55 localhost kdm_greet[8786]: Can't open default user face
Feb 28 18:02:18 localhost kdm_greet[8786]: Internal error: memory corruption detected
Feb 28 18:02:20 localhost kdm_greet[8803]: Can't open default user face
Feb 28 18:02:47 localhost kdm_greet[8803]: Internal error: memory corruption detected
Feb 28 18:02:49 localhost kdm_greet[8820]: Can't open default user face
Feb 28 18:03:12 localhost kdm_greet[8820]: Internal error: memory corruption detected
Feb 28 18:03:15 localhost kdm_greet[8837]: Can't open default user face
Feb 28 18:03:19 localhost kdm_greet[8837]: Internal error: memory corruption detected

```

/var/log/kern.log 
```

Feb 28 18:03:02 localhost kernel: [4331263.456000] IPT INPUT packet died: IN=eth0 OUT= MAC=00:d0:09:e4:15:5f:00:30:4f:3b:49:50:08:00 SRC=221.8.179.98 DST=19
Feb 28 18:03:12 localhost kernel: [4331273.336000] [fglrx] Internal AGP support requested, but kernel AGP support active.
Feb 28 18:03:12 localhost kernel: [4331273.336000] [fglrx] Have to use kernel AGP support to avoid conflicts.
Feb 28 18:03:12 localhost kernel: [4331273.336000] [fglrx] AGP detected, AgpState   = 0x1f000207 (hardware caps of chipset)
Feb 28 18:03:12 localhost kernel: [4331273.337000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Feb 28 18:03:12 localhost kernel: [4331273.337000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Feb 28 18:03:12 localhost kernel: [4331273.337000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Feb 28 18:03:12 localhost kernel: [4331273.337000] [fglrx] AGP enabled,  AgpCommand = 0x1f000304 (selected caps)
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] free  AGP = 54800384
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] max   AGP = 54800384
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] free  LFB = 49278976
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] max   LFB = 49278976
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] free  Inv = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] max   Inv = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total Inv = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total TIM = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total FB  = 0
Feb 28 18:03:12 localhost kernel: [4331273.395000] [fglrx] total AGP = 16384


```

and finaly /ver/log/Xorg.0.log

```


(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xd8d8b000
(II) fglrx(0): [drm] mapped SAREA 0xd8d8b000 to 0xb7b4e000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-k7
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xcfef0000
(II) fglrx(0): [agp] Mode=0x1f000207 bridge: 0x1039/0x0735
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000304
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000304)
(II) fglrx(0): [agp] graphics chipset has AGP v2.0
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xd8f01000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x00501000
(II) fglrx(0): Splitting WC range: base: 0xc0000000, size: 0x501000
(II) fglrx(0): Splitting WC range: base: 0xc0400000, size: 0x101000
(==) fglrx(0): Write-combining range (0xc0500000,0x1000)
(==) fglrx(0): Write-combining range (0xc0400000,0x101000)
(==) fglrx(0): Write-combining range (0xc0000000,0x501000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1024,1281)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1024,768) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 768)
(II) fglrx(0): Largest offscreen area available: 1024 x 505
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                24 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT


```

---

### Post by torx on 2006-03-03
I was wondering if someone could help me fix my MTRR. Here's the output error.

> 
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1
reg01: base=0x20000000 ( 512MB), size=983296MB: write-back, count=1


How i tried to fix it, but failed:

> #echo "disable=2" >| /proc/mtrr
echo "disable=5" >| /proc/mtrr
echo "disable=1" >| /proc/mtrr
echo "disable=3" >| /proc/mtrr
echo "disable=4" >| /proc/mtrr
echo "disable=0" >| /proc/mtrr
echo "base=0x00000000 size=0x30000000 type=write-back" >| /proc/mtrr


This init.d script results in massive slowdown in boot up and i get an error about the *base* value. 

I have 786mb of RAM and 128mb of video ram. Can anyone help me edit the fix_mtrr script?

---

### Post by Cuppa-Chino on 2006-03-03
[QUOTE=l0c0dantes]
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
[/QUOTE]

mine is the same - if I try to fglrxconfig I get no-where it says: 
[I]@ubuntu:~$ fglrxconfig
bash: fglrxconfig: command not found[/I]
fglrxinfo does work however

any help would be great

---

### Post by alanrr_sr on 2006-03-03
Hi,
I have a ATI RADEON 9550 XT, my motherboard is a asus k8n, with nforce 3 chipset.
I really can't put 3d to work, no drive, no kernel, nothing work!!!!!

But I've just discovered that if I boot on Windows, restart it, and boot in linux after the reboot, my 3d card works!!! I don't know who I should complain, - ubuntu kernel, ati, or nforce chipset?? Anyone are having or know any place the describes the problem???

Thx

Ubuntu Breezy
System: 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686 GNU/Linux, Any ati drive, internal agpgart on or off 
=====================================
Xorg problem: 
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0d04000 at 0xb7ab7000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000

**Conclusion: **
Need to boot on windows, (soft)restart, boot on linux. I can reboot in linux after that infinite times, and it keeps working.
If I try to boot on linux first, and restart, It doesn`t work. 

I know that linux does not require shutdowns...but eletricty in Brazil is dangerous :D

---

### Post by mikaPELL on 2006-03-04
Hi guys, I've followed the guide, but it gives me an error I can't understand:
```
mikapell@compqk:~/Desktop/wine$ sh ati-driver-installer-8.22.5-i386.run
Creating directory fglrx-install
Verifying archive integrity...Error in MD5 checksums: 594978d070de1185bd5984f25778d5f4 is different from af7a73518ca61960663ec0dfdd4398c6

```
I can't figure out what to do!
Edit: Never mind, it seems that after downloading the .run file again (twice) it worked.

---

### Post by RaptorRaider on 2006-03-04
Does using the latest fglrx drivers (using the HOWTO) fix the problem where the screen goes black when you logout?

---

### Post by Mobus on 2006-03-04
thank you so much

I tried so many things... this one finally work. glxgears didn't choke! WOOOHOO! 

Thanks again, this was wonderfully concise, complete, and readable.

---

### Post by CloudBolt on 2006-03-05
well, I followed the guide, and everything seems to be working okay(except of course DRI), but fglrxinfo states:
[B]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
[/B]
and glxinfo states:
[B]name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None[/B]

so I don't have 3d hardware acceleration. does anyone know what causes this?

**EDIT: all right, my Xorg.0.log states that the module version (8.16.20) doesn't match the driver used(8.22.5). what should I do about this?**

[B]EDIT 2: my Xorg.0.log states:
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x002b7000 at 0x2aaaaab45000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *[/B]

---

### Post by mlomker on 2006-03-05
[QUOTE=KooT]
Feb 28 18:01:55 localhost kdm_greet[8786]: Can't open default user face
Feb 28 18:02:18 localhost kdm_greet[8786]: Internal error: memory corruption detected
[/QUOTE]

Spent some time Googling for this but couldn't find anything conclusive.  The message relates to KDM's icon view during login but that isn't Ubuntu's default--did you manually edit the configuration files to turn that on?  I also saw some references to misconfigured ~/.bashrc files.

One thing that I'd try is to Ctrl-Alt-F2 to a prompt and then **sudo kill kdm** and **startx** to see if KDE will load without kdm.  You could also install GDM as a test and see if it launches KDE properly.

---

### Post by mlomker on 2006-03-05
[QUOTE=torx]I have 786mb of RAM and 128mb of video ram. Can anyone help me edit the fix_mtrr script?[/QUOTE]

If you haven't already, then you'll want to make a post in the thread that I link to or search the Rage3D board and ask on there.  My machine doesn't have this problem, so I can't help out.

---

### Post by mlomker on 2006-03-05
[QUOTE=Cuppa-Chino]
bash: fglrxconfig: command not found[/I]
[/QUOTE]

That program is for the old drivers.  Use **aticonfig** or edit xorg.conf file.

The MESA error is generic--you need to look in the log files listed toward the bottom of the how-to for errors.

---

### Post by mlomker on 2006-03-05
[QUOTE=RaptorRaider]Does using the latest fglrx drivers (using the HOWTO) fix the problem where the screen goes black when you logout?[/QUOTE]

Maybe.  Hangs on shutdown and logout are problems with certain cards/mobos.  The issue was solved on my laptop but I've heard from others that still have trouble.

---

### Post by mlomker on 2006-03-05
[QUOTE=CloudBolt]
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
[/QUOTE]

You did one of the following: didn't reboot after install, didn't remove restricted-modules, or the **m-a a-i fgrlx** step failed.

---

### Post by linuxishard on 2006-03-05
hi... im using dapper at the moment... and i have the same msg about 
Direct rendering not enabled...:cry: 
its a real bummer.. everything that uses the graphics card runs so slowly.. does anyone know how to enable it...????

---

### Post by CloudBolt on 2006-03-05
[QUOTE=mlomker]You did one of the following: didn't reboot after install, didn't remove restricted-modules, or the **m-a a-i fgrlx** step failed.[/QUOTE]


all right, thanks, fglrxinfo now states 
[B]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X550 Generic
OpenGL version string: 2.0.5642 (8.22.5)[/B]

but still, the glxgears program gives me a very low framerate. do you happen to know why this is(it's around 1900 fps, MESA levels)

EDIT: all right, it gets even stranger, glxgears gives me a VERY low score, whilst fgl_glxgears' score is incredibly high. anyone who knows what's causing this?

EDIT 2: hmm strange, everything is working fine when playing OpenGL 3D games, with PPracer I got about 122 fps, which is pretty good. the only thing not working seems to be glxgears.  well everyone, thanks for your time, my problems are solved

---

### Post by qrazi on 2006-03-05
I cannot get the drover to work on my other Ubuntu machine. 

The hardware: ATi 9800SE 128MB with 9800XT bios, MSI K7N2 Delta2 (nForce2 motherboard) and a AMD Athlon XPm 3200+.

Ubuntu: Breezy Badger, clean install, installed kernel 2.6.12 K7

After I follow the steps of the howto and reboot, i get the message that the Xserver fails to start.

When i look in de log file, it gives a warning:
no matching device section for instance BusID PCI:3:0:1
No devices detected.

No mather what values i select in the xorg.conf, the xserver doesnt load. Can anyone point me in the right direction?

---

### Post by Stew2 on 2006-03-05
Hello, I too am having problems installing the ati drivers on my system. I have went through most of this thread, and being a noob, was confused lots :) . I tried most of the solutions listed, but there are so many it gets confusing. I used synaptic to install the ati drivers, but I cant seem to get it to use the fglrx driver, it keeps coming back with the mesa driver. I tried to manually edit xorg and put fglrx in place of ati as was mentioned in one of the threads, but it didnt help. Frame rates are still abysmall. :( . 2D works great but as soon as I go to 3D and Open GL, it just chugs. 2.4 P4 with 512 ram and ATI 9800 Pro, smokes in   Windows, chugs in Ubuntu. Any idea on how to get rid of the mesa drivers and get it to use the ati ones? Thanks in advance. (I've been screwing around with this for over 4 hours :) ) Heres my fglrx output.

stewart@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
Any ideas? :confused:

Edit: I think this is posted in the wrong thread. Oops! I will start new thread.

---

### Post by Draco Houston on 2006-03-06
I still have that problem too, dispite checking all the steps I still have the damn mesa3d drivers!

Any other ideas, please, I've had this dual booted with windows for a few months now, but I can't really use it while it has no hardware acceleration

---

### Post by mlomker on 2006-03-07
[QUOTE=qrazi]No mather what values i select in the xorg.conf, the xserver doesnt load. Can anyone point me in the right direction?[/QUOTE]

Is that the slot that your card is in?  **lspci** should tell you.  You will see an error like that normally if you have a dual-head card, but shouldn't with a single card.

Did you also look in the /var/log/Xorg.0.log and kern.log?  Did you use **aticonfig** to modify your config or do it by hand?  You could start a new thread and attach a copy of your xorg.conf.  If you send me a link to the thread in a PM then I'll take a look at it.

---

### Post by mlomker on 2006-03-07
[QUOTE=Draco Houston]I still have that problem too, dispite checking all the steps I still have the damn mesa3d drivers!
[/QUOTE]

Create a new thread and attach your /var/log/Xorg.0.log and kern.log from a failed boot.  The errors are in those files.  Send me a link to your post in a PM if you'd like me to take a look.

---

### Post by RaptorRaider on 2006-03-07
[QUOTE=mlomker]Maybe.  Hangs on shutdown and logout are problems with certain cards/mobos.  The issue was solved on my laptop but I've heard from others that still have trouble.[/QUOTE]
I have absolutely no problems when I don't install any drivers - does that rule out my motherboard (MSI K8N Neo Platinum)?


Anyway, I think it's [this]("http://ati.cchtml.com/show_bug.cgi?id=239") bug.
It's almost 4 months old now (and doesn't seem to exist in earlier versions); way to go ATI.
Wish I hadn't spend all that money on this X800 XT PE (AGP).

---

### Post by qrazi on 2006-03-07
mlomker: I started a new thread on your suggestion. You can find it [here]("http://www.ubuntuforums.org/showthread.php?t=141090")

---

### Post by VCSkier on 2006-03-08
according to [this]("http://doc.gwos.org/index.php/IBMThinkpadT42Breezy") guide, installing fglrx drivers on a IBM T42 Thinkpad breaks the hibernate/suspend features.  well, i've got an IBM Thinkpad T41, with the ATI Radeon Mobility 9000 card, and i'd like to get my drivers working...  i was wondering if i installing [Suspend2]("http://www.ubuntuforums.org/showthread.php?t=75443") would fix it.  if i understand it correctly, that would entail me recompiling my kernel, and thats alittle intimidating for me.  can anyone confirm for me that this would work?

---

### Post by ankouts on 2006-03-08
Hello to all :)
I am very new to Ubuntu and and to Linux in general.
I just bought a Fujitsu Siemens laptop, the model is Amilo A1667G2, and i tried to install Ubuntu 5.10. At first restart i see this : Failed to start X server. It is likely that it is not set up correctly. 
Is it a problem with my vga card (ati X700) ? Please can you help me, as i don't know much thing about linux.
Thank you for your help

---

### Post by RaptorRaider on 2006-03-08
Great.

I'm using the "standard" fglrx driver (the one in the Ubuntu repositories), and though I haven't made any major changes lately, problems seem to have become larger.

When I now boot Ubuntu, I have about 66% chance the screen will go black when GDM is about to be started.

I really hope that by the time Dapper is released ATI will have released decent drivers because otherwise Dapper won't get that "stable, polished" finish from many ATI users.

---

### Post by TrendyDark on 2006-03-08
**Just to let the creator of this guide know, there has been a new release of drivers** and I've installed them using your guide (modified version # in the package names of coarse) and it still works like a charm. You'll need to change the 8.22.5 to 8.23.7 in every step of your guide.

---

### Post by mlomker on 2006-03-08
[QUOTE=TrendyDark]Just to let the creator of this guide know, there has been a new release of drivers[/QUOTE]

Thanks, I'll check it out.

---

### Post by mlomker on 2006-03-08
[QUOTE=VCSkier]according to [this]("http://doc.gwos.org/index.php/IBMThinkpadT42Breezy") guide, installing fglrx drivers on a IBM T42 Thinkpad breaks the hibernate/suspend features.  [/QUOTE]

That guide talks about 7500 cards and not a 9000.  The latest ATI drivers supposedly support hibernation.  I have a laptop but I don't even try to use that feature...it doesn't work perfectly under Windows so I wouldn't expect linux to be much better.  

Are you sure that your video card isn't an M6?  The M6 is actually a 7500 and not supported by the fglrx driver.

---

### Post by mlomker on 2006-03-08
[QUOTE=ankouts] i tried to install Ubuntu 5.10. At first restart i see this : Failed to start X server. It is likely that it is not set up correctly. [/QUOTE]

Tried to install Ubuntu or this driver?  If you can't get Ubuntu to boot then you should post on the absolute beginner or installation forums.  You can probably type **sudo dpkg-reconfigure xserver-xorg** and select the VESA or ATI driver to get to your desktop.

---

### Post by mlomker on 2006-03-08
[QUOTE=RaptorRaider]I really hope that by the time Dapper is released ATI will have released decent drivers because otherwise Dapper won't get that "stable, polished" finish from many ATI users.[/QUOTE]

It's been a work in progress for a long time and nobody on this thread works for ATI.  ;)  We should probably consider ourselves lucky that the video card companies are supporting linux as well as they are...plenty of other hardware has no support whatsoever under linux.

---

### Post by bardu on 2006-03-08
I followed every step at the guide but did not have luck so far on my AMD64 box with ATI RADEON XPRESS 200 series.
Here is the /var/log/Xorg.0.log:
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 root@crested.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux ubuntu2 2.6.12-10-amd64-generic #1 Mon Feb 13 12:14:05 UTC 2006 x86_64
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-amd64-generic (buildd@king) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:14:05 UTC 2006 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar  8 13:16:07 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig Screen 0" (0)
(**) |   |-->Monitor "aticonfig Monitor 0"
(**) |   |-->Device "ATI Graphics Adapter 0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,2a26 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a26 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a26 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a26 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a26 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a26 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a26 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,2a26 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,2a27 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5954 card 103c,2a26 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 103c,2a26 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:05:0: chip 1106,3044 card 0003,000f rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc unknown chipset (0x5954) rev 0, Mem @ 0xd8000000/27, 0xfdef0000/16, I/O @ 0xee00/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfddfe000 - 0xfddfe7ff (0x800) MX[B]
	[1] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[13] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[14] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[16] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[17] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfddfe000 - 0xfddfe7ff (0x800) MX[B]
	[1] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[2] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[3] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[4] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[5] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[6] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[7] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[8] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[12] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[13] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[14] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[16] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[17] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfddfe000 - 0xfddfe7ff (0x800) MX[B]
	[6] -1	0	0xfddff000 - 0xfddff0ff (0x100) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[13] -1	0	0xfdef0000 - 0xfdefffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df7f (0x80) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[19] -1	0	0x0000f900 - 0x0000f90f (0x10) IX[B]
	[20] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[21] -1	0	0x0000fb00 - 0x0000fb0f (0x10) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc03 (0x4) IX[B]
	[23] -1	0	0x0000fd00 - 0x0000fd07 (0x8) IX[B]
	[24] -1	0	0x0000fe00 - 0x0000fe03 (0x4) IX[B]
	[25] -1	0	0x0000ff00 - 0x0000ff07 (0x8) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

Fatal server error:
Module load failure


Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


```

Hope somebody can give my advice what to do.
Thanks,
Stephan

---

### Post by ivoencarnacao on 2006-03-09
Is the new driver version working ok?
After following mlomker's HowTo to the end i get this from glxinfo

> 
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None



Thanks,
Ivo.

---

### Post by ankouts on 2006-03-09
I installed the newest ati driver (ati-driver-installer-8.23.7-x86_64.run) but i got errors after installation. At the /usr/share/fglrx/fglrx-install.log there are these messages :
Kernel Module: Trying to install a precompiled kernel module.
Kernel Module: Precompiled kernek module version mismatched.
Kernel Module: No kernel modul build enviroment - please consult readme.

I followed the How-To instructions. I have ATi X700 graphic card. I am very new to Linux.
Thank you for your help.
Edit: I just tried the vesa driver and it works, but i want the ATI driver.

---

### Post by wousser on 2006-03-09
try this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Ubuntu_Dapper](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Ubuntu_Dapper)

---

### Post by ankouts on 2006-03-09
Thank you for your response.
[QUOTE=wousser]try this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Ubuntu_Dapper](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Ubuntu_Dapper)[/QUOTE]
At the beginning of this guide says this:
Important Change: Installation of this driver no longer requires removing the linux-restricted-modules package in order to work.

This works also at the 5.10 version ? If not, what do i have to do at the before  remove existing fglrx driver?

Edit: i found the right one

---

### Post by RaptorRaider on 2006-03-09
[QUOTE=mlomker]It's been a work in progress for a long time and nobody on this thread works for ATI.  ;)  We should probably consider ourselves lucky that the video card companies are supporting linux as well as they are...plenty of other hardware has no support whatsoever under linux.[/QUOTE]
Yet somehow I don't feel so lucky to find out that I've spend over &#8364;400 for my videocard to get near zero functionality in Linux. 

And yes, I know it's not Ubuntu's fault, and that ATI's drivers are slowly getting better, but I just feel like a misunderstood consumer when I see all those laptops with ATI hardware.

I just see those large Linux companies (like Red Hat and Novell) who are depending on hardware companies like ATI to help them squash the Microsoft monopoly but they seem to get almost nothing instead.

I'm just a disappointed customer.

---

### Post by ankouts on 2006-03-10
I followed the instructions of the Ubuntu Installation Guide, but i get this error after all and when i write the command fglrxinfo:
error: unable to open display :0

---

### Post by andbelo on 2006-03-11
Hi,

I was following the howto and after the command:

> sudo apt-get remove linux-restricted-modules-$(uname -r)

I got this output:

> Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  linux-686 linux-restricted-modules-2.6.12-10-686
  linux-restricted-modules-686
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 14.0MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

I aborted because it seemed I would be damaging my linux installation and mybe after rebbot I wouldn't be able to load linux. Is that right? Is it safe to do that? Bytheway, these are my linux packages installed taken from Synaptic in a Dell Inspiron 6000:

> linux-686
linux-headers-2.6.12-10
linux-headers-2.6.12-10-686
linux-image-2.6.12-10-686
linux-image-686
linux-kernel-headers
linux-restricted-modules-2.6.12-10-686
linux-restricted-modules-686
linux-restricted-modules-common

Thanks

---

### Post by sonar_un on 2006-03-12
At least some of you are getting errors. I have just been getting a black screen. Even changing the display mode to vesa no longer works. It seems like its a refresh issue, but even changing the default refresh rates to ones that I know for a fact work just give me a black screen.

I have used linux on and off for a few years and decided to try out the new Ubuntu installation. The 32 bit 5.10 seems to work ok using a vesa mode driver, however the 64 bit flight5 did not work at all, even after a few hours of reading forums and messing with configuration files.

---

### Post by buntulf on 2006-03-12
Hello. I am wondering if any one have tried to get an Ati Radeon x1600pro agp to work properly in Ubuntu 5.10. I have tried, but it only works with the vesa driver. Not giving up easy. :confused:

---

### Post by andbelo on 2006-03-12
I gave my shot and uninstalled

linux-686
linux-restricted-modules-2.6.12-10-686
linux-restricted-modules-686

following all the steps of the HOWTO. Now the drive (ATI Radeon X300) is working fine in a Dell Inspiron 6000.

> andbelo@localhost:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1171 frames in 5.0 seconds = 234.200 FPS
1375 frames in 5.0 seconds = 275.000 FPS
1360 frames in 5.0 seconds = 272.000 FPS
1360 frames in 5.0 seconds = 272.000 FPS
1357 frames in 5.0 seconds = 271.400 FPS

---

### Post by SmartWarthog on 2006-03-12
Hi,

I followed each and every step of the How-to correctly on my (almost) fresh Ubuntu Breezy installation. I couldn't get X to startup with the fglrx drivers (after the Ubuntu logo with the progressbar I get a black screen), so I restored my backup xorg.conf and I am using the ati drivers. After this, I noticed things that used to be fast now are pretty slow (3D screensavers for example). My card is a Powercolor Radeon 9250 and I have the kernel 2.6.12-10-k7 installed. Please help me, what do I have to do to fix this? If there is any other information I should provide, please tell me.

Thanks for the attention

---

### Post by f3tus on 2006-03-12
```
sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
```

After doing the last step... What's wrong?

---

### Post by Xaviar21 on 2006-03-12
[QUOTE=f3tus]```
sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
```[/QUOTE]

Yeah! This is my problem too.. Or part of it anyway..

---

### Post by ivoencarnacao on 2006-03-13
Will this guide work on an Ati Mobility 9700?:confused:

---

### Post by marios88 on 2006-03-13
Did anyone have any luck with 3D with the X800 SE?

I have been trying for around a month searching the web but with no luck...

---

### Post by escape on 2006-03-14
Anyone else notice that fglrx destroys the logout feature? There's a thread about it here: [http://ubuntuforums.org/showthread.php?t=128762](http://ubuntuforums.org/showthread.php?t=128762)

This is really annoying.

---

### Post by mlomker on 2006-03-15
[QUOTE=bardu]I followed every step at the guide but did not have luck so far on my AMD64 box with ATI RADEON XPRESS 200 series.
Here is the /var/log/Xorg.0.log:
```

Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

```
[/quote]

The how-to mentions removing the int10a line from the xorg.conf file to solve this error.  You must be runing the 64-bit version of Ubuntu...fyi, it'd be more clear if you stated '64-bit' rather than 'amd64' because the processor can run 32 or 64 bit versions of Ubuntu.

---

### Post by mlomker on 2006-03-15
[QUOTE=ivoencarnacao]Is the new driver version working ok?
After following mlomker's HowTo to the end i get this from glxinfo[/QUOTE]

It works fine.  You need to look in the log files for the error messages.  glxinfo only provides information of interest to programmers...

---

### Post by mlomker on 2006-03-15
[QUOTE=ankouts]I installed the newest ati driver (ati-driver-installer-8.23.7-x86_64.run) but i got errors after installation. At the [/QUOTE]

Do you have 64-bit Ubuntu (that is the 64-bit file)?  If you are new to linux then I'd recommend installing the 32-bit version instead...it's a lot less trouble.

---

### Post by mlomker on 2006-03-15
[QUOTE=wousser]try this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Ubuntu_Dapper](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.23.7_drivers_in_Ubuntu_Dapper)[/QUOTE]

Dapper allows you disable individual modules for restricted modules.  That'll make life a lot easier.  I'll link to this.

---

### Post by mlomker on 2006-03-15
[QUOTE=ankouts]I followed the instructions of the Ubuntu Installation Guide, but i get this error after all and when i write the command fglrxinfo:
error: unable to open display :0[/QUOTE]

You'll need to look in /var/log/kern.log and Xorg.0.log for error messages.

---

### Post by mlomker on 2006-03-15
[QUOTE=buntulf]Hello. I am wondering if any one have tried to get an Ati Radeon x1600pro agp to work properly in Ubuntu 5.10. I have tried, but it only works with the vesa driver. Not giving up easy. :confused:[/QUOTE]

You'll want to go the ATI forum.  The last I heard was that it still wasn't working, but I haven't had time to read the forum for a week or so.

---

### Post by mlomker on 2006-03-15
[QUOTE=f3tus]```
sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
```

After doing the last step... What's wrong?[/QUOTE]

I found a couple references in Google but most were in a foreign language.  Have you tried **sudo ldconfig**?

---

### Post by mlomker on 2006-03-15
[QUOTE=ivoencarnacao]Will this guide work on an Ati Mobility 9700?:confused:[/QUOTE]

Yes, that's what I have.

---

### Post by ruimoura on 2006-03-15
I really don know what i'm doing wrong, but i follow the guide and all i can get is:

muja@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


I have a laptop with ATI Radeon 9000 Mobile 64 Mb. I'm with Ubuntu 5.10.

Please help me cause i want to leave Micros%&t XP but this way i can't play the only thing it's saving my windows partition from being deleted, America's Army game.

Thank's in advance.

Ps: when i do fglrxconfig i put all the default options, i'm scared of messing something up ...

---

### Post by f3tus on 2006-03-15
> I found a couple references in Google but most were in a foreign language.
Yes I went through all of them but haven't found the answer. 

Tried to soft-link it but it doesn't help.

> Have you tried sudo ldconfig?
I might add I'm a beginner in linux, so I don't know the syntax you're expecting me to  enter :rolleyes:

---

### Post by mssm on 2006-03-15
Hi,

I have successfully installed the latest fglrrx version 8.23.7 for Radeon 9700 video card in my laptop. Thanks a bunch. Here is the output of fglrxinfo :
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5695 (8.23.7)
```

I would like reduce the clock speed of my video card like one can do in atitools for Windows. Is there anything like atitools for linux which will allow me to do so?

Thanks in advance

---

### Post by RaptorRaider on 2006-03-15
mlomker, in your guide you are linking to another guide to install ATI drivers in Dapper.
Currently, you are linking to method 2, which involves compiling manually while the included driver in Dapper seems to be exactly the same.
Why choose for method 2?

---

### Post by kwicky21 on 2006-03-16
[QUOTE=ruimoura]I really don know what i'm doing wrong, but i follow the guide and all i can get is:

muja@laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
[/QUOTE]

I have the same problem! How do you fix this? :( My laptop comes with ATI Mobility Radeon 9100 IGP. If it's not compatible with this card, are there solutions to work around this?

Any help would gladly be appreciated.

Thanks in advance!

---

### Post by acankat on 2006-03-16
Well I have a really cool problem with my ati card. I follow the instructions and install the drivers, check it by fglrxinfo and everything seems ok, 3D apss work really great.

But when I turn off the pc and turn it on again (not soft reboot), direct rendering becomes unavailable and that mesa scum strikes back!

The only solution I could find is applying this step of the ([]("http://www.ubuntuforums.org/showthread.php?t=143283&highlight=ati+drivers")) guide:

> gunzip libdri.a.gz
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a libdri.a.old
sudo cp libdri.a /usr/X11R6/lib/modules/extensions/

copying libdri.a to its place again and soft rebooting the computer temporarily solves the problem, until the next turn off.

that goes on like this...

I beg for some help, Please.

[EMAIL="aydin.cankat@gmail.com"]aydin.cankat@gmail.com[/EMAIL]

---

### Post by kwicky21 on 2006-03-16
How do you fix the mesa problem?

---

### Post by acankat on 2006-03-16
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+drivers]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+drivers")

this guide works perfectly for me execpt the problem I mentioned above.

---

### Post by mssm on 2006-03-16
Hi,

I have successfully installed the latest fglrrx version 8.23.7 for Radeon 9700 video card in my laptop. Thanks a bunch. Here is the output of fglrxinfo :
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5695 (8.23.7)
```

I would like reduce the clock speed of my video card like one can do in atitools for Windows. Is there anything like atitools for linux which will allow me to do so? Actually, I am having some trouble with my laptop's display -- it becomes "dirty" due to some artifacts.  Maybe the RAM of video card is malfunctioning due to overheating. I have a screenshot attached.

Thanks in advance

---

### Post by mlomker on 2006-03-17
[QUOTE=ruimoura]Ps: when i do fglrxconfig i put all the default options, i'm scared of messing something up ...[/QUOTE]

Is that an M6 (an IBM laptop)?  They aren't supported by the driver.  There isn't an fglrxconfig in this version...the instructions use aticonfig.

---

### Post by mlomker on 2006-03-17
[QUOTE=f3tus]I might add I'm a beginner in linux, so I don't know the syntax you're expecting me to  enter :rolleyes:[/QUOTE]

**sudo ldconfig**

---

### Post by mlomker on 2006-03-17
[QUOTE=RaptorRaider]The included driver in Dapper seems to be exactly the same.  Why choose for method 2?[/QUOTE]

I don't run Dapper and people keep asking me about it.  Even if the driver in Dapper is currently the latest right now that won't be true at release.  They'll freeze the version sometime soon and ATI will keep updating.

---

### Post by mlomker on 2006-03-17
[QUOTE=kwicky21]I have the same problem! How do you fix this? :( My laptop comes with ATI Mobility Radeon 9100 IGP. [/QUOTE]

The IGP cards are not supported.  You have to use the ATI driver.

---

### Post by mlomker on 2006-03-17
[QUOTE=acankat]copying libdri.a to its place again and soft rebooting the computer temporarily solves the problem, until the next turn off.
[/QUOTE]

I haven't seen that before.  Is this Breezy?

---

### Post by mlomker on 2006-03-17
[QUOTE=kwicky21]How do you fix the mesa problem?[/QUOTE]

That is a symptom, not the problem.  Look in the log files for error messages to figure out what went wrong.  /var/log/Xorg.0.log and kern.log.

---

### Post by mlomker on 2006-03-17
[QUOTE=mssm]Is there anything like atitools for linux which will allow me to do so?[/QUOTE]

Try a search on the [ATI support forum]("http://www.rage3d.com/board/forumdisplay.php?f=88")/make a post there.

---

### Post by DigiNeT on 2006-03-19
Is this Ok?

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 DDR Generic
[COLOR="Red"]OpenGL version string: 1.3.1050 (X4.3.0-8.23.7)[/COLOR]

```

It`s not saying...

```
[COLOR="Red"]OpenGL version string: 2.0.5695 (8.23.7)[/COLOR]
```

how can i fix that?

---

### Post by c3l5o on 2006-03-19
Have a problem also....

```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

WTF is this? I have a X800 (R430) PCI-Ex...

---

### Post by iceloki on 2006-03-20
I followed the install instructions. After I switched to 'fglrx' driver, I restarted my ubuntu box, the fglrx driver works great and the opengl is working. But when I turned on the computer next time, the system halt while starting X with blank screen (monitor is power off and seems to be in sleep mode) and the system does not respond any more. I don't know how to debug or checking the problem...

My system is sempron 2600+ (not 64-bit), 1G RAM, Dataland 9550 Golden edition, K8N (nforce 3) mainboard. System is dapper with latest uprades.

---

### Post by Amodef on 2006-03-21
@ DigiNeT : I have the same problem than you, and all the other guys that have a Radeon 9000M seem to have it too.

I've tried different tutorial to install the fglrx driver but I always get the same result. If you try "fgl_glxgears", you 'll see that your cube as no gears in it...

I have tried to played at Never Winter Nights, but the game is very slow. It was better with the free Radeon driver ! The OpenGL screensaver are very slow too...

I don't know how to do to get it work, but if anybody can help, he is welcome ^^ .

(excuse for my bad english)

---

### Post by DigiNeT on 2006-03-22
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 DDR Generic
[COLOR="Red"]OpenGL version string: 1.3.1050 (X4.3.0-8.23.7)[/COLOR]
```

And this is the picture you are talking about.

[IMG]http://www.imgfreehost.com/uploads/52ce141f0c.jpg[/IMG]

help please ](*,)

---

### Post by SkimWear on 2006-03-28
[QUOTE=iceloki]I followed the install instructions. After I switched to 'fglrx' driver, I restarted my ubuntu box, the fglrx driver works great and the opengl is working. But when I turned on the computer next time, the system halt while starting X with blank screen (monitor is power off and seems to be in sleep mode) and the system does not respond any more. I don't know how to debug or checking the problem...

My system is sempron 2600+ (not 64-bit), 1G RAM, Dataland 9550 Golden edition, K8N (nforce 3) mainboard. System is dapper with latest uprades.[/QUOTE]

that's crazy. i'm having the same exact problems.

the HOW-TO worked. However, about 2 minutes of running time and my monitor goes into a stand by mode says "Power Save Mode running, to Power On use the PC" and I cant get it out of that stage :(

another odd thing about it is that the programs I'm using lock-up 3 seconds before the monitor goes blank.

oh and iceloki, we have a very similar setup.

any ideas to what this may be related to?

edit: I'm running a Radeon 9800 Pro 128mb.

edit#2: I've narrowed down my problem back to the video card...it's a little dusty and it seems like the fan is not spinning. Check if that may be your cause as well. So far I havent regulated a fix for mines, but I've got my case open and am monitoring the temperature of the video card via "Cuban Style" :) I made my own thing. Anyways, WD-40 and some swabs should clean off the card/fan and i'll pop it back in, check the power cables and fire it up again and re-post if I got it fixed or not.

---

### Post by SkimWear on 2006-03-29
My Solution: Fan looks like its dead, there are a few options out there such as aftermarket replacement fans or you can make your own fan. The point is getting the video card cooled. I currently have a huge fan thats suspended over a PCI slot blowing towards the GPU and it seems to help. Hope this solves any of you guys problems as well.

Extra cooling is key :)

---

### Post by VikngEyez182 on 2006-03-30
[QUOTE=mlomker]That is a symptom, not the problem.  Look in the log files for error messages to figure out what went wrong.  /var/log/Xorg.0.log and kern.log.[/QUOTE]

I'm getting the meso problem and I'm running an ATI Radeon 9550 card. Everything in the control panel looks alright except it says Unknown for both the  Card Name and the Chip Type. I tried to post my Xorg.0.log and my kern.log files as .txt files on here, but it said that it was too big. Could someone please help me?

---

### Post by Adler on 2006-03-30
Hi All,

I've a COMPAQ Presario AMD 64-Bit Turion chipset and a ATI Radeon Express 200M video card with 128Mb of dedicated memory. 

About a week ago I downloaded the latest version of UBUNTU Dapper. I'm new to UBUNTU, but have been using SuSE for about 2 years. I've been following the guide at the beginning of this thread and after I 

chmod +x ati-driver-installer-8.23.7-x86_64.run, then
LANG=C LANG_ALL=C ./ati-driver-installer-8.23.7-x86_64.run --buildpkg Ubuntu/dspper

the install begins. However, I am getting this error message --

dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/x86_64-linux-gnu/lib64/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libpthread.so.0 not found. 
dpkg: /usr/x86_64-linux-gnu/lib64/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libX11.so.6 not found. 
dpkg: /usr/x86_64-linux-gnu/lib64/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libstdc++.so.5 not found. 
dpkg: /usr/x86_64-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libdl.so.2 not found. 
dpkg: /usr/x86_64-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_gamma.so.1 not found. 
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_pp.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx' 
~/Desktop/fglrx-install
Removing temporary directory: fglrx-install

I've searched and have not found the source of my dependency issues. I'm completely up-dated and if there is an answer out there I would be most appreciative to hear it.

Thanks in advance for any responses.

Adler

---

### Post by franklee on 2006-03-30
Hey folks, I cant get x to open a session because of the unknown device error and Im wondering how I go about setting my default display to vesa?

---

### Post by ThaRabbit on 2006-03-30
[QUOTE=franklee]Hey folks, I cant get x to open a session because of the unknown device error and Im wondering how I go about setting my default display to vesa?[/QUOTE]

Does system boot end you up in text mode ?

If so, you may try to check /etc/X11 for a file called xorg.conf~. That file would contain your default settings. You can try to rename that file to xorg.conf (be sure to rename your current xorg.conf to somehting like xorg.conf.bak !) to restore your prmary settings and hence probably bring you back to vesa :)

---

### Post by flankker on 2006-04-01
hi, im new with ubuntu. my gfx is an ati mobility radeon 9000 IGP.

i was following the tutorial here [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

i downloaded the ati driver installer.

then i did:
 
sudo apt-get install gcc-3.4 module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

but when i try to do:

chmod +x ati-driver-installer-8.23.7-i386.run

it says "no such file or directory". can any1 help? thanx.

---

### Post by Kure on 2006-04-01
[QUOTE=flankker]hi, im new with ubuntu. my gfx is an ati mobility radeon 9000 IGP.

i was following the tutorial here [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

i downloaded the ati driver installer.

then i did:
 
sudo apt-get install gcc-3.4 module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

but when i try to do:

chmod +x ati-driver-installer-8.23.7-i386.run

it says "no such file or directory". can any1 help? thanx.[/QUOTE]


In which directory do you execute chown?

---

### Post by flankker on 2006-04-01
[QUOTE=Kure]In which directory do you execute chown?[/QUOTE]

im not sure what u mean, sorry.

i just typed chmod +x ati-driver-installer-8.23.7-i386.run in the terminal

the file is located in a sub folder in my home folder

EDIT: never mind, i got it working.

i did all the steps with no errors, at the end i did fglrxinfo and get:

agustin@Laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

does it mean it worked?

---

### Post by Adler on 2006-04-01
Hi All,

I've made progress from my last post and have completed the install. After re-booting to check to confirm that it is working I enter -- in Console -- $ fglrxinfo, but get the following --

Error: couldn't find RGB GLX visual!

I think that I am almost there. Any suggestions?

---

### Post by flankker on 2006-04-02
EDIT: got the 8.16.20 version working correctly.

however, hardware acceleration is not supported for my card (mobility 9000 igp) so theres no chance for me to install compiz or xgl or play any decent games.

im going to install ubuntu on my main pc with a radeon X300 see if thats any better.

---

### Post by Adler on 2006-04-02
Hi All,

Well, I got it to work after carefully following the instructions mentioned at the start of this thread. I used the method --

Method 2: Generating/Installing Ubuntu packages for the newer 8.23.7 drivers in Ubuntu Dapper.

I had tried this method in the past, but this time around I enabled UMA&Sideport in the BIOS. Then I re-did the install on my COMPAQ Turion 2.2 GHz 64-Bit Notebook. 

Presently my frame rate playing GL-117 is 30 FPS, so I now need to tweak the config a bit.

---

### Post by arkangel on 2006-04-10
hI  I have a  singular problem  i look for someone who has the same problem , maybe one of you  had the same problem  or have read about 

My notebook is a Asus V6Va Centrino 1.86 1gb ram ,and X 700 mobility radeon ,  I have install the last drivers (wiki ati) , the previous ones and I have the same weird effect 

the installation goes smoothly , all is ok ,  but when i  want to logout , restart or shutdown  , or restart the Xserver ,  the screen goes black  , then goes white like some kind of flourescence  (see  picture),   then i cannot open a console  or nothing , this only happeds when i install any ati driver "fglrx"

now I am with mesa  drivers  

Please somes help

---

### Post by DonQuixote on 2006-04-10
I don't know if this will help you, but I found that the latest version of the ATI drivers broke things.

[http://ubuntuforums.org/showthread.php?t=133707](http://ubuntuforums.org/showthread.php?t=133707)

---

### Post by mlomker on 2006-04-12
[QUOTE=arkangel]this only happeds when i install any ati driver "fglrx"
[/QUOTE]

This is a rather common problem with the drivers and is probably BIOS-related.

You should make sure that you're running the latest BIOS for your laptop, look on the ATI forums, and use the Bugzilla link at the top of the page and do a few searches.  If you don't find anything then you may want to file a Bugzilla report on it.

---

### Post by Adler on 2006-04-18
Hi All,

I've installed the latest ATI Driver -- ati-driver-installer-8.24.8-x86_64.run -- using the instructions at the beginning of this thread. I have a AMD Turion 64-Bit COMPAQ Notebook and can play Tux Racer and GL-117 in 2D vodeo, but have not yet figured out how to get 3D Acceleration working.

The video card is a ATI Radeon XPress 200m. 

Here is some information concerning both glxgears and fgl_glxgears --

jxxxxxx@ubuntu:~$ glxgears -printfps
7577 frames in 5.0 seconds = 1513.725 FPS
8653 frames in 5.0 seconds = 1730.472 FPS
8578 frames in 5.0 seconds = 1715.512 FPS
8654 frames in 5.0 seconds = 1730.607 FPS
8581 frames in 5.0 seconds = 1715.574 FPS
8627 frames in 5.0 seconds = 1725.321 FPS
jxxxxxx@ubuntu:~$

jxxxxxx@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
Floating point exception

I've searched and searched for the error message and how to correct it, but I have not been succesful. If I add -fbo I do get a result --

jxxxxxx@ubuntu:~$ fgl_glxgears -fbo
Using GL_EXT_framebuffer_object
1817 frames in 5.0 seconds = 363.400 FPS
2572 frames in 5.0 seconds = 514.400 FPS
2048 frames in 5.0 seconds = 409.600 FPS
1874 frames in 5.0 seconds = 374.800 FPS
1868 frames in 5.0 seconds = 373.600 FPS
1874 frames in 5.0 seconds = 374.800 FPS
1867 frames in 5.0 seconds = 373.400 FPS
jxxxxxx@ubuntu:~$

The issue is how to I start 3D Acceleration without having to add -fpo or where should I look to edit my xorg.conf file?

Any help would be appreciated.

---

### Post by bugme on 2006-04-21
Does anyone have the guide for 8.23.7 that was here before.  It worked perfectly for me.  Now I cannot get the control panel installed, and my sound doesnt work in games.

---

### Post by gmcle454 on 2006-05-22
for some weird reason, I had to run the install script several times before it installed correctly. Try getting the latest version or the last one and re-run the script. 

Good luck

---

### Post by marios88 on 2006-05-23
I have installed the newest ati drivers and i can now run 3D with an ati x800 SE

but when i run glxgears of fgl_glxgears i get 100% processor use,is that ok?

here are the results from 

marios@toumpano:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
5907 frames in 5.0 seconds = 1181.400 FPS
6180 frames in 5.0 seconds = 1236.000 FPS
6174 frames in 5.0 seconds = 1234.800 FPS

marios@toumpano:~$ glxgears -printfps
33724 frames in 5.0 seconds = 6744.661 FPS
33804 frames in 5.0 seconds = 6760.628 FPS
33756 frames in 5.0 seconds = 6751.148 FPS

are the numbers ok?

---

### Post by gmcle454 on 2006-05-23
I wouldn't think that glx should peak out your processor for long periods of time. That is probably a problem. Whish I new more about it, so I could help you trouble-shoot and fix it.

---

### Post by Rippy on 2006-05-23
I have a Radeon 9250, 128mb

I installed the fglrx driver as instructed in the how-to, however when I switch the driver from "ati" to "fglrx", I get NO video. It just boots to a blank screen. I could've figured out how to edit xorg.conf and switch it back, but I figured it'd be faster to just re-install ubuntu (as I had only just installed it). I tried again and had no more success. Can anyone help me out?

---

### Post by BayGuy27 on 2006-05-24
I updated my ATI drivers using these steps ->

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

After rebooting, my screen's brightness is extremely high, a very pale shade. Changing the contrast and brightness on the monitor does not help, and the ATI Control program that is installed has no area to adjust such settings. I really need help with this one, even to revert back to the original drivers. Thanks in advance,

Dave

---

### Post by supsup on 2006-06-03
[QUOTE=BayGuy27]I updated my ATI drivers using these steps ->

[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

After rebooting, my screen's brightness is extremely high, a very pale shade. Changing the contrast and brightness on the monitor does not help, and the ATI Control program that is installed has no area to adjust such settings. I really need help with this one, even to revert back to the original drivers. Thanks in advance,

Dave[/QUOTE]

The same here. Any solutions?

---

### Post by clandestino81 on 2006-06-03
[QUOTE=supsup]The same here. Any solutions?[/QUOTE]
The same problem.

---

### Post by Stinko on 2006-06-04
Finalmente funzionano! :mrgreen: 

Ecco come ho fatto:

1) Installare Dapper, abilitare tutti i repo standard e aggiornare il sistema

2) Scaricare questi driver nel Desktop:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

3) Installare il necessario per la compilazione:
```
sudo apt-get update
sudo apt-get install module-assistant build-essential debhelper gcc-3.4
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```

4) Generare i pacchetti:
```
cd ~/Desktop
chmod +x ati-driver-installer-8.24.8-x86.run
./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper
```

5) Editare questo file:
```
sudo nano /etc/default/linux-restricted-modules-common

Modificare questa riga:
DISABLED_MODULES=""
in
DISABLED_MODULES="fglrx"
```

6) Installare i pacchetti che abbiamo generato al §4:
```
sudo dpkg -i xorg-driver-fglrx_8.24.8-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.24.8-1_i386.deb
sudo dpkg -i fglrx-control_8.24.8-1_i386.deb
```

7) Rimuovere fglrx-kernel*.deb (non ci dovrebbe essere niente)
```
sudo rm /usr/src/fglrx-kernel*.deb
```

8 ) Compilare:
```
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod
```

9) Correggere  /etc/X11/xorg.conf
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

10) Riavviare il sistema:
```
sudo reboot
```

11) Primo test:
```
fglrxinfo
```

12) Secondo test:
```
fgl_glxgears
```

13) Fare un bel sorriso! ;D

Ecco i risultati dei miei test:
```
stinko@stinko-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1060 (X4.3.0-8.24.8)

stinko@stinko-desktop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
641 frames in 5.0 seconds = 128.200 FPS
798 frames in 5.0 seconds = 159.600 FPS
818 frames in 5.0 seconds = 163.600 FPS
791 frames in 5.0 seconds = 158.200 FPS
823 frames in 5.0 seconds = 164.600 FPS
790 frames in 5.0 seconds = 158.000 FPS
807 frames in 5.0 seconds = 161.400 FPS
787 frames in 5.0 seconds = 157.400 FPS
823 frames in 5.0 seconds = 164.600 FPS
795 frames in 5.0 seconds = 159.000 FPS
797 frames in 5.0 seconds = 159.400 FPS
817 frames in 5.0 seconds = 163.400 FPS
790 frames in 5.0 seconds = 158.000 FPS
stinko@stinko-desktop:~$

```

Questo è il mio attuale * /etc/X11/xorg.conf* (vedi *Section "Device"*)
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "it"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "L1950S"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "L1950S"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

Vedi:
[http://forum.ubuntu-it.org/index.php?topic=25266.0](http://forum.ubuntu-it.org/index.php?topic=25266.0)

---

### Post by kokas on 2006-06-04
Can you translate it to english please ?? I did follow the wiki tutorial several times and it never worked. Here's the error I'm getting:

```
nelson@nelson-desktop:~$ fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEX T
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectf vATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjecti vATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvA RB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvA RB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantAT I
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryA TI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivE XT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentPar ameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
nelson@nelson-desktop:~$

```

This is my xorg.conf file

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "pt"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "NEC V520"
	HorizSync    31.0 - 70.0
	VertRefresh  55.0 - 120.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor    "NEC V520"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

### Post by [HUN]Levente on 2006-06-04
I have Radeon 9600Pro, I have an older ATI driver installed, the installing seemed to be OK, but even planetpenguin racer is unplayable, about 5fps... :)
Now I tried to install the newest driver, but aticonfig gives an error:

```
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
```

The file libfglrx_pp.so.1 exists in /etc/X11R6/lib and I also copied it to /usr/bin, but it gives the same error. What could be the problem?

---

### Post by sumadartson on 2006-06-05
> Can you translate it to english please ?? I did follow the wiki tutorial several times and it never worked. Here's the error I'm getting:


Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=185033](http://www.ubuntuforums.org/showthread.php?t=185033)

---

### Post by blocky on 2006-06-06
Can someone tell me how to enable vertical sync on my 9500?  I can't find anything about it in xorg.conf but there must be a way to get rid of the tearing when I play videos/games at a decent fps

---

### Post by Kidijs on 2006-06-06
[QUOTE='[HUN]Levente']I have Radeon 9600Pro, I have an older ATI driver installed, the installing seemed to be OK, but even planetpenguin racer is unplayable, about 5fps... :)
Now I tried to install the newest driver, but aticonfig gives an error:

```
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory
```

The file libfglrx_pp.so.1 exists in /etc/X11R6/lib and I also copied it to /usr/bin, but it gives the same error. What could be the problem?[/QUOTE]

The same problem here except I don't have a folder /etc/X11R6, I have /etc/X11 but no 'lib' in it. Maybe you can try copying it to /usr/lib ?

EDIT: I found the missing file under /usr/X11R6/lib, copied it to /usr/lib, adn hurray- aticonfig worked.
I will restart now to see if drivers are installed properly.
(And if xorg.conf isn't corrupted ;-))

---

### Post by JeronimoGe on 2006-06-06
```
sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
ilia@ubuntu:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
(Reading database ... 150301 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.24.8-1 (using xorg-driver-fglrx_8.25.18-1_i386.deb) ...
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
 different file `/usr/share/fglrx/diversions/libGL.so.1.2', not allowed
dpkg: error processing xorg-driver-fglrx_8.25.18-1_i386.deb (--install):
subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
xorg-driver-fglrx_8.25.18-1_i386.deb
ilia@ubuntu:~/Desktop$
```

unable to install ati driver after Kernel UPdate IMHO.
trying method 2 from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

this manual please somebody help me!:confused: :confused: :confused: :confused: :confused:

---

### Post by bjtuna on 2006-06-07
[QUOTE=Rippy]I have a Radeon 9250, 128mb

I installed the fglrx driver as instructed in the how-to, however when I switch the driver from "ati" to "fglrx", I get NO video. It just boots to a blank screen. I could've figured out how to edit xorg.conf and switch it back, but I figured it'd be faster to just re-install ubuntu (as I had only just installed it). I tried again and had no more success. Can anyone help me out?[/QUOTE]

Same thing going on here, dude. Other people are reporting the same problem.

---

### Post by campnic on 2006-06-17
[QUOTE=bjtuna]Same thing going on here, dude. Other people are reporting the same problem.[/QUOTE]


Try commenting out "Load "extmod" " in your xorg.conf file (/etc/X11/xorg.conf)  This solved my black screen problems (thanks fadah)

---

### Post by Heitzso on 2006-08-31
SYSTEM: ms-1039 laptop, x1600 mobility
OS: dapper drake 32 
(failed to get 64 working due to fglrx and wlan 64 problems)
FGLRX and X: seveas 
(the xorg update bug bit me and I bumped to seveas to fix)
PROBLEM: when reboot, system tries to load fglrx from a volatile dir where it does not exist
FIX: in bootmisc I create a sym link from where expected to where it is actually found.

QUESTION: I cannot figure out why modprobe can't find fglrx where it actually lives, and instead goes to that weird volatile dir.
What's up with that?  What is the correct fix instead of the jury rigged ln -s in bootmisc.sh?

Thanks

My apt sources for seveas:
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas drivers
deb-src [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas drivers

The bad modprobe error output:
FATAL: Could not open '/lib/modules/2.6.15-26-k7/volatile/fglrx.ko': No such file or directory

The jury rig in bootmisc.sh:
ln -s /lib/modules/2.6.15-26-k7/misc/fglrx.ko \
/lib/modules/2.6.15-26-k7/volatile/fglrx.ko

---

### Post by r00tzz on 2007-01-01
> **Adler said:**
> Hi All,

I've a COMPAQ Presario AMD 64-Bit Turion chipset and a ATI Radeon Express 200M video card with 128Mb of dedicated memory. 

About a week ago I downloaded the latest version of UBUNTU Dapper. I'm new to UBUNTU, but have been using SuSE for about 2 years. I've been following the guide at the beginning of this thread and after I 

chmod +x ati-driver-installer-8.23.7-x86_64.run, then
LANG=C LANG_ALL=C ./ati-driver-installer-8.23.7-x86_64.run --buildpkg Ubuntu/dspper

the install begins. However, I am getting this error message --

dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/x86_64-linux-gnu/lib64/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libpthread.so.0 not found. 
dpkg: /usr/x86_64-linux-gnu/lib64/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libX11.so.6 not found. 
dpkg: /usr/x86_64-linux-gnu/lib64/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libstdc++.so.5 not found. 
dpkg: /usr/x86_64-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libdl.so.2 not found. 
dpkg: /usr/x86_64-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_gamma.so.1 not found. 
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_pp.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx' 
~/Desktop/fglrx-install
Removing temporary directory: fglrx-install

I've searched and have not found the source of my dependency issues. I'm completely up-dated and if there is an answer out there I would be most appreciative to hear it.

Thanks in advance for any responses.

Adler

How did you solve this error?!?!?!?

Thanks

---

### Post by Adler on 2007-01-01
r00tzz,

I was like many of the people that have posted, or viewed this thread e.g. desperate to get my ATI Radeon Xpress 200M Notebook card going. I've been trying to get this done for about 6 - 8 months.

I started with Dapper, and now run Edgy, but via Linux Mint. I was having problems with the 64-bit codecs that I wanted with 64-bit Ubuntu Edgy, and went to 32-bit [Linux Mint]("http://lt.k1011.nutime.de/"). Linux Mint is Edgy, but with all the codecs already installed. Automatix2 seems to have been giving me too many problems. 

The newest ATI Driver works, while nothing else has. I followed Method #2 from [here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").

I have also not had to change my BIOS settings from SidePort to UMA+SidePort. Cool!

I then went on to installing Beryl by following this [guide]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html").

Basically, the ATI driver development has fallen behind, but is catching up. I'm getting OK Game Play, in 3D, but my newest toys are those cool Beryl Desktop effects. But, here I think that I need to get an external mouse with a wheel to get the best of Beryl performance. Those Desktop guys make it look sooo easy.

Hey, we are pushing Linux Notebooks here!

I hope this has helped, and Happy New Year!

Adler

---

### Post by shizow on 2007-01-02
i tried to install 8.32.5 on my Thinkpad t43 with X300
(before i had a 8.2xx version of fglrx)
i followed the guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

after rebooting i get an black window with the mouse pointer

/var/log/kernel.log
```

Jan  2 14:26:39 localhost kernel: [17179637.108000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jan  2 14:26:39 localhost kernel: [17179637.112000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
Jan  2 14:26:39 localhost kernel: [17179637.116000] [fglrx] module loaded - fglrx 8.32.5 [Dec 12 2006] on minor 0
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] total      GART = 130023424
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] free       GART = 114032640
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] max single GART = 114032640
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] total      LFB  = 66977792
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] free       LFB  = 40816640
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] max single LFB  = 40816640
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] total      Inv  = 0
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] free       Inv  = 0
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] max single Inv  = 0
Jan  2 14:26:45 localhost kernel: [17179642.864000] [fglrx] total      TIM  = 0
Jan  2 14:27:02 localhost kernel: [17179660.588000] [fglrx] PCIe has already been initialized. Reinitializing ...
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] total      GART = 130023424
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] free       GART = 114032640
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] max single GART = 114032640
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] total      LFB  = 66977792
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] free       LFB  = 40816640
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] max single LFB  = 40816640
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] total      Inv  = 0
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] free       Inv  = 0
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] max single Inv  = 0
Jan  2 14:27:02 localhost kernel: [17179660.600000] [fglrx] total      TIM  = 0

```

it is somehowe reinitializing 3 or more times, which i can see also on the screen

any suggestions?

UPDATE:
i am now installed 8.29.6 which works without problems
why do i have problems with 8.32.5?

---

### Post by CyberCod on 2007-01-14
I just did a fresh install of edgy, and installed the proprietary drivers using instructions from the Binary/HOWTO

I've successfully gotten the TV-out to work, but I'm having major problems with the monitor.

The monitor has a washed-out, high-gamma appearance that makes everything hard to see.

Others have remarked on this problem earlier and I've not seen any responses to it.

If anyone can help, please help me.

Thanx.

---

### Post by melenor on 2007-01-16
i am brand new to linux and i was disappointed when my X1800 XTX did not have 3D acceleration, and i began looking for the driver and i need an easy to do and use for newbies driver guide

---

### Post by s3lf on 2007-02-12
the fglrx driver works for me, but --set-powerstate doesnt seem to have an power-safing affect with my ATI Mobility RADEON X1400 :(

---

### Post by lodp on 2007-03-06
...exactly! I've got the Mobility RADEON X1300, and after I installed the new ATI driver - 8.34.08 - the fan won't stop blowing. No matter what powerstate the card is in. This sure sucks -- is there any way around this (other than reverting to prior versions?)

---

### Post by Zakk Walid on 2007-05-19
hey i m new her :) 

i have a problem installing my ATI. 

i followed this: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
and followed the "Method 2: Install the 8.36.5 Driver Manually" because i was toled that the Linux effects work only with this way of installation. 

while following this tutorial... 
in one of the steps, i am toled to go to this page, [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
and do it before continuing. 
in one of their steps i need to do this: 
[IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=menu-sw.png[/IMG]
and i dont have this opthion! :O 

what should i do!!! 
:( help me plzzzzzzzzzz

---

### Post by Melcar on 2007-05-20
Latest version (8.36.5) does not work for me.  I always have followed this basic [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually") with 100% success rate every time, until now.  Basically, I can follow up the entire process error free until I get to the point of configuring the driver; running the *aticonfig* commands corrupts my xorg.conf file for some reason; configuring the file manually may be possible, but I'm not that proficient in xserver configurations.  For now I just follow the first method (getting the driver from the repositories) and it works great (no errors and everything is stable) but I hate not having the most recent driver and not being able to install it myself.

---

### Post by drummingpariah on 2007-09-07
Right now, typing is pretty painful.  I have a choice between a resolution of 640x480 @ ~ 10fps using the open-source ATI driver or 800x600 @ 2fps using the VESA driver.  I can also make an attempt to load up the fglrx (both the xubuntu edgy restricted driver, or latest ATI release) but that locks the machine completely (even ctrl+alt+del gives no results), and xorg produces no logs when I try.

For a little info, because I'd yell at me if I read this:

lspci:
```

01:00.0 VGA compatible controller: ATI Technologies Inc R200 BB [Radeon All in Wonder 8500DV]
01:00.1 PCI bridge: ATI Technologies Inc R200 BC [Radeon All in Wonder 8500]
02:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)

```

My bios is currently using the 64mb AGP instead of the 256, because 256 locks the machine as well.  It could very well be related to the motherboard, being an old Dell XPS.  Dell reports it as being a Dimension XPS T700r.

So finally, I'd just like to state that I'd like to get a reasonable framerate at 1680x1050, and I believe this can only be accomplished using the latest fglrx drivers.  It's possible that the open-source ATI drivers will be able to do that, but xfce seems to be limiting me to the barebones default resolutions.

current applicable (vesa) xorg.conf sections (leaving out input, as they are default):
```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```


The same sections for the ATI driver:
```

Section "Device"
        Identifier      "ATI Technologies, Inc. R200 BB [Radeon All in Wonder 8500DV]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "FPD1975W"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. R200 BB [Radeon All in Wonder 8500DV]"
        Monitor         "FPD1975W"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1280" "1280x1024" "1280x960" "1280x800" "1152x921" "1024x768"$
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

And finally, the ENTIRE fglrx xorg.conf (because 'aticonfig --initial' changes the whole thing):
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1280x800" "1152x921" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

Any help that anybody can offer would be much appreciated!  If you need more/different info, please let me know.

*NOTE* just to make sure everybody knows, I'm running XUBUNTU 6.10, and have installed fglrx version 8.40.4-x86*/NOTE*

---

### Post by mikejordan on 2007-09-14
> 
 Originally Posted by Adler  View Post
Hi All,

I've a COMPAQ Presario AMD 64-Bit Turion chipset and a ATI Radeon Express 200M video card with 128Mb of dedicated memory.

About a week ago I downloaded the latest version of UBUNTU Dapper. I'm new to UBUNTU, but have been using SuSE for about 2 years. I've been following the guide at the beginning of this thread and after I

chmod +x ati-driver-installer-8.23.7-x86_64.run, then
LANG=C LANG_ALL=C ./ati-driver-installer-8.23.7-x86_64.run --buildpkg Ubuntu/dspper

the install begins. However, I am getting this error message --

dh_compress
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/x86_64-linux-gnu/lib64/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_gamma.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_pp.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx'
~/Desktop/fglrx-install
Removing temporary directory: fglrx-install

I've searched and have not found the source of my dependency issues. I'm completely up-dated and if there is an answer out there I would be most appreciative to hear it.

Thanks in advance for any responses.

Adler


I'm having this EXACT PROBLEM... I followed the instructions on the wiki (method 2) to no avail. Does anyone have a clue how to fix this?

thanks

---

### Post by Verdin on 2008-05-03
I'm having the following problem.  I installed the Ubuntu 7.1 server on a UltraSPARC machine.  I then downloaded ubuntu through apt-get but I don't get any gui...just command line.  So I can't follow the instructions below: 

> Enable "restricted" Repository

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

System > Administration > Software Sources. Check "Proprietary Drivers for Devices (Restricted)" box. 

I've tried a couple options from the terminal but nothing works.

I've checked out AMDs website and there are only drivers for x86 and x86-64.

How are people using ATI cards on a Sun Computer?

---

### Post by jarekl on 2008-06-21
My configuration, HD2600xt, AMD 3000+, 1G RAM, Two monitors, 1 samsung and one Pansonic TH-50PZ70E, both and DVI, the Panasonic through the HDMI dongle. The Panasonic is the problem. 

Installation using  ati-driver-installer-8-6-x86.x86_64.run was without any problems. Dual-head setup eventually worked too. The Panasonic is probably not returning correct EDID info and I can't get rid of the black border surrounding the image on the Panasonic (which is significantly smaller though having nominal resolution of 1920x1080). The manual says that custom modes take preference over probed but nothing I did made any difference (I did read the manual and used only "Modes" name "1920x1080" so it should).

I addition to that, every time I stoped gdm, it froze the machine (though Alt-SysRQ worked). The amdcccle application worked once when I had the screens mixed up. When I got it right, catalyst control center locked up every time.

I have had this card (the HD2600XT) for quite some time now. With this release, I could actually smoothly drag windows and scroll firefox pages but that's all. I revisit the driver releases once every two or three months to see if it works but the Nvidia cards go back every time. 

The good thing about this card is the image quality. Perhaps that's why I keep on trying, or is it perhaps because today you can't barely give this card away.

---

### Post by melenor on 2008-06-22
Okay just installed 8.6 and now i can;t watch any video, any way to fix this or to just reinstall the ATI driver from the ubuntu repo because that worke fine with video. thanks

---

