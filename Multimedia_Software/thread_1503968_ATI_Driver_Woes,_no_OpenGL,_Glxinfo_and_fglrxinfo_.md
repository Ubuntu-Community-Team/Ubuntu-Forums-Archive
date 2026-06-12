---
title: "ATI Driver Woes, no OpenGL, Glxinfo and fglrxinfo do not work, Compiz does not work.."
date: 2010-06-07
forum: Multimedia Software
---

### Post by tropicalfish on 2010-06-07
Hello!

So I've searched pretty much all over Google for this and I've spend a few hours trying to solve it to no avail.

Basically I've managed to get my ATI drivers installed (That much I finally figured out with the help of Google), but now I'm not getting any direct rendering or 3d graphics.

Desktop special effects do not work. Compiz-check returns this:
```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV770 [Radeon HD 4870]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```


glxinfo returns this:
```
glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

```

and fglrxinfo returns this:
```
fglrxinfo
Error: couldn't find RGB GLX visual!

```


Any suggestions or solutions? Please help!



[b]SOLUTION: GO TO POST 21 HERE: [http://ubuntuforums.org/showpost.php?p=9431865&postcount=21](http://ubuntuforums.org/showpost.php?p=9431865&postcount=21)

And... I don't know how to change the title prefix. The edit post page doesn't seem to have the dropdown for it.[/b]

---

### Post by proxess on 2010-06-07
```
sudo apt-get install fglrx
sudo aticonfig --initial
```

Reboot.

---

### Post by tropicalfish on 2010-06-07
You won't believe how many times I've tried to do that.
I've purged it, remove everything video, reinstalled etc.

Nothing worked. Still the same.

---

### Post by boonenoob on 2010-06-07
do you have ati catalyst controll center installed?

---

### Post by tropicalfish on 2010-06-07
Yes, I do.

I can configure my dual monitor options and enable/disable Xinerama...
However, under "Information," nothing shows up for OpenGL Provider, OpenGL Renderer, or OpenGL Version.
Also, I cannot edit the following 3D settings (they are grayed out): Anti-Aliasing, Anisotropic Filtering, and Catalyst AI (I hate using CAI on my Windows install but still...).

---

### Post by boonenoob on 2010-06-07
try this:
```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

```
this worked for me

---

### Post by tropicalfish on 2010-06-07
^ Tried before, to no avail.

I made what I hope to be some progress... I've removed libgl1-mesa-dri and libgl1-mesa-glx (which automatically also removed compiz-fusion-plugins-extra, xorg, and metapackage ubuntustudio-desktop).

Now I am able to enable Desktop effects and also my fglrxinfo returns this:

```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series         
OpenGL version string: 1.4 (3.3.9836 Compatibility Profile Context)

```

However, my glxinfo | grep rendering still returns:
```
glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

"LIBGL_DEBUG=verbose glxinfo | grep rendering" returns:
```

LIBGL_DEBUG=verbose glxinfo | grep rendering
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib/fglrx/dri/swrast_dri.so failed (/usr/lib/fglrx/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib32/fglrx/dri/swrast_dri.so
libGL error: dlopen /usr/lib32/fglrx/dri/swrast_dri.so failed (/usr/lib32/fglrx/dri/swrast_dri.so: wrong ELF class: ELFCLASS32)
libGL error: unable to load driver: swrast_dri.so
libGL error: reverting to indirect rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

---

### Post by boonenoob on 2010-06-07
did you
```

sudo dpkg-reconfigure xserver-xorg

```before reboot?

---

### Post by tropicalfish on 2010-06-07
Tried that, didn't work. 
I've tried reinstalling drivers, purging, and also making .deb packages of the ATI proprietary driver to install.
The only things that happened was that I got wonky colors, no CCC, and mirrored display on my monitors. It's at its best at the moment, but still with no direct rendering.

---

### Post by boonenoob on 2010-06-07
does opengl work?
(to test it type glxgears in terminal)

---

### Post by tropicalfish on 2010-06-07
Yes it does, I get rotating gears.


Though it seems quite flickery if I don't disable the desktop effects.

---

### Post by boonenoob on 2010-06-07
hmmm. did you get the driver from the ATI website? Some cards are no longer Supported.
For me, removing ATI catalyst control center fixed some things, but I don't know if that will work for you.

---

### Post by tropicalfish on 2010-06-07
Yes, driver was from the AMD/ATI website. 

I have an HD4870... It should be supported.

---

### Post by boonenoob on 2010-06-07
can you tell me the contents of the Xorg.*.log files by doing:
```

cd //
 cd var
 cd log
 gedit Xorg.0.log
 gedit Xorg.1.log
 gedit Xorg.2.log

```

---

### Post by tropicalfish on 2010-06-07
Here they are, attached.

The number corresponds with the log file + 1 (0 is 1, if that makes sense)

1 is tar'd due to filesize.

---

### Post by boonenoob on 2010-06-08
it looks like it is trying to load fglrx still
the * earlier:
```

sudo apt-get remove --purge fglrx[COLOR=Red]*
[/COLOR]
```[COLOR=Red][COLOR=Black]
is very important.
also try this:
```

sudo apt-get remove xserver-xorg-video-radeon
```
[/COLOR][/COLOR]then
```

sudo apt-get install xf86-video-radeonhd

```

---

### Post by tropicalfish on 2010-06-08
Nope, doesn't work.

My biggest problem is this:

Anytime I try to install something fglrx (yes, I uninstalled it to see if i could reinstall it and make it work), I get this:

(In this case, I'm using the packaged deb files of the original ATI proprietary driver.)

```
[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /home/terry/Desktop/ATI/fglrx_8.732-0ubuntu1_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /home/terry/Desktop/ATI/fglrx_8.732-0ubuntu1_amd64.deb

```

---

### Post by boonenoob on 2010-06-08
hmm. at this point, i don't know what the problem could be. ubuntu forum community, could you help out?

---

### Post by tropicalfish on 2010-06-08
New problem.

When I try to install fglrx: 

```
Setting up fglrx (2:8.732-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.732 DKMS files...

------------------------------
Deleting module version: 8.732
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.732 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.31-12-realtime
Building for architecture x86_64
Building initial module for 2.6.31-12-realtime

Error! Bad return status for module build on kernel: 2.6.31-12-realtime (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.732/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-12-realtime
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up fglrx (2:8.732-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.732 DKMS files...

------------------------------
Deleting module version: 8.732
completely from the DKMS tree.
------------------------------
Done.

```



make.log:

```
DKMS make.log for fglrx-8.732 for kernel 2.6.31-12-realtime (x86_64)
Tue Jun  8 15:30:17 CDT 2010
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.31-12-realtime/build SUBDIRS=/var/lib/dkms/fglrx/8.732/build/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-12-realtime'
  CC [M]  /var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.o
In file included from /var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c:443:
/var/lib/dkms/fglrx/8.732/build/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/var/lib/dkms/fglrx/8.732/build/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c: In function &#8216;firegl_init_module&#8217;:
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c:1028: error: expected expression before &#8216;{&#8217; token
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c: In function &#8216;KCL_SetPageCache_Array&#8217;:
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c:1316: warning: passing argument 1 of &#8216;KCL_ConvertPageToKernelAddress&#8217; makes pointer from integer without a cast
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.h:325: note: expected &#8216;void *&#8217; but argument is of type &#8216;long unsigned int&#8217;
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c: In function &#8216;KAS_Mutex_Initialize&#8217;:
/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.c:5060: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/var/lib/dkms/fglrx/8.732/build/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.732/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-12-realtime'
make: *** [kmod_build] Error 2
build failed with return value 2
```

---

### Post by boonenoob on 2010-06-08
```

sudo apt-get remove --purge fglrx fglrx-amdcccle fglrx-dev

```[COLOR=Red]
[COLOR=Black]This will completely remove those from the system, which will solve the error, but not the overall problem.[/COLOR]
[COLOR=Black]This is driving me crazy. ](*,)[/COLOR]
[/COLOR]

---

### Post by tropicalfish on 2010-06-08
**_[SIZE="7"][FONT="Arial Black"]SOLVED THAT CRAP![/FONT][/SIZE]_**

Updated my kernel as stated here: [http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264)

> 1. (64 bit users only) There is a low-latency preempt kernel available. This is the default kernel for an installation of Ubuntu Studio with the audio package. It can also be installed by selecting linux-preempt  and linux-headers-preempt in Synaptic Package Manager.

Removed all the old headers and kernels. 

Did this:

```

sudo apt-get remove fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases 
sudo apt-get purge fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases 

```

Rebooted.

Did this:

```

sudo apt-get update

sudo apt-get install fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases 
```

Rebooted

Now...

glxinfo | grep rendering
```
glxinfo | grep rendering
direct rendering: Yes
```

---

### Post by hfranco75 on 2010-06-30
Hell man, I'm already desperate. Still no OpenGL functionality. What could I miss? The only important thing I've discovered is that the driver installation process tries to build the kernel module, but it fails cause', while compiling, it cannot find the file utsrelease.h

I've got a HD 5830 card in a system running Lucid.

Help, please...

---

### Post by pinginn on 2011-05-11
Nvid >>  sudo apt-get install mesa-utils 


xinfo -h
Usage: glxinfo [-v] [-t] [-h] [-i] [-b] [-display <dname>]
	-v: Print visuals info in verbose form.
	-t: Print verbose table.
	-display <dname>: Print GLX visuals on specified server.
	-h: This information.
	-i: Force an indirect rendering context.
	-b: Find the 'best' visual and print it's number.
	-l: Print interesting OpenGL limits.

# Note To My Self. Pinginn

---

