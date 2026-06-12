---
title: "New nVidia video card = blank screen?"
date: 2009-08-29
forum: Multimedia Software
---

### Post by gungfujoe on 2009-08-29
After being unhappy with the performance of my low-end ATI video card in my HTPC (no way to turn off overscan, considerable shearing artifacts with HD video), I found an inexpensive GeForce 9400 with HDMI to replace it with.

I booted up, hoping that it would see that I was no longer using an ATI video card and revert to the generic drivers that should work with any card.  Instead, I got a momentarily scrambled screen, followed by a blank screen.

So I went into recover mode, and tried the automatic graphics problem fix.  No luck, same result.

So I went back into recover mode, downloaded the latest [nVidia drivers](ftp://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run), and tried to run them.  It suggested I switch from mode 1 to mode 3, which of course tried to load the GUI and once again left me with no display.

So I rebooted again and ignored the warning, telling it to install in mode 1.  It told me that no driver package for my distribution could be found, and that it would try to compile one.  That effort failed, with an error consisting of a full screen of text.  It indicated that the problem was usually caused by a GCC version mismatch or something.

What do I do next?  I can't get into the GUI without fixing the graphics drivers, and I can't seem to install the drivers from recover mode.  I'm sure there's a simple solution to this, but I don't know my way around Linux well enough to find it myself.  I'd rather not reinstll the OS from scratch and have to reconfigure it, just because I installed a new video card.

---

### Post by RedSingularity on 2009-08-29
From the text screen do.  

sudo apt-get autoremove xorg-driver-fglrx

Reboot.

---

### Post by gungfujoe on 2009-08-29
> **Shadow121 said:**
> sudo apt-get autoremove xorg-driver-fglrx

Thanks for the really quick response.  This got me back into the GUI, but I'm still not having any luck getting the nVidia drivers installed.

I used the proprietary drivers dialog to activate the 180 drivers (a bit old, but if they work, I'm happy), and restarted the system.

When it came back, it loaded in 800x600 mode, with an error saying that I was in low graphics mode, and that the drivers failed with the following error:

(EE)NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE)NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Not quite sure what that means.  I've got my 9400 video card connected to my HDTV with a VGA cable, and also connected to my A/V receiver with an HDMI cable (the VGA cable is there only to troubleshoot HDMI issues, and I'm using it instead of the DVI port simply because I have a spare VGA cable, but no spare DVI cable).  The video card doesn't seem to want to send a signal over the HDMI cable (figuring that out is the next step, once I get drivers working), but it's sending a signal over the VGA cable directly to the TV.

---

### Post by RedSingularity on 2009-08-29
SO you have the nvidia drivers installed then correct?  If so post the output of your /etc/x11/xorg.conf file.

---

### Post by gungfujoe on 2009-08-29
I don't think the drivers are installed.  Every time I try, I get the error, and the only way to get into the OS is to tell it to use low graphics mode for just this session.  I've tried telling it to create a new configuration for this setup, and get the same result.  If I go into the proprietary drivers tool, it tells me that the driver is active, but not currently in use.

In any case, my /etc/X11/xorg.conf file contains (commented lines removed for brevity):

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by renkinjutsu on 2009-08-29
what kernel do you have installed? Is it a custom kernel?
use the binary from nvidia's website.. and make sure you have your kernel headers installed

---

### Post by gungfujoe on 2009-08-29
> **renkinjutsu said:**
> what kernel do you have installed? Is it a custom kernel?No, I'm a bit much of a Linux newbie to be doing that.  I'm using a stock Mythbuntu 9.04 (32-bit) system with the various system updates installed.  I was using the whatever.14 version of the kernel when I first tried installing the nVidia drivers, but went ahead and installed all of the System Updates, which included the whatever.15 version of the kernel. Same results with both kernels. (I've shut the system down until I have another concrete option to try, which is why I don't have the full version handy, but it's whatever is currently distributed in the Ubuntu system updates)

As I said in my initial message, the binary from nVidia's website (FTP site, actually, since I could only get to the command line at that point) failed to install.  If Ubuntu normally installs the kernel headers, then they're installed.  If it doesn't, they're not.

---

### Post by RedSingularity on 2009-08-29
Well you have the correct driver activated according to your xorg.  Have you tried hooking up a regular computer monitor and restarting?  I am curious.  It may just be a problem configuring your TV to use as a monitor.  Of course if you hook up the computer monitor and still have problems then it is another issue.


Oh and did you install the driver directly from the Nvidia site?  The .run file?

---

### Post by gungfujoe on 2009-08-30
> **Shadow121 said:**
> Well you have the correct driver activated according to your xorg.  Have you tried hooking up a regular computer monitor and restarting?  I am curious.  It may just be a problem configuring your TV to use as a monitor.This afternoon, I'll have to dig the monitor from one of our computers out (there's enough debris on my wife's and my desk that neither monitor's base is clearly visible) and try this. Assuming this works, though, what is the next step? How do I configure the TV to be used as a monitor? Since this is an HTPC and I don't have a spare computer monitor, this obviously isn't a fix, but just a troubleshooting step.

In Windows, since the HDTV is connected with a VGA cable, I would just tell it I'm not using a plug and play monitor and manually specify an output resolution, but I don't see any way to do that here.

> **Shadow121 said:**
> Oh and did you install the driver directly from the Nvidia site?  The .run file?The driver that failed to install completely was the .run file from nVidia.com (the pkg1 file, not the pkg0 file). It said it had to compile a driver, and then failed to compile. The driver that did install but failed to work is the one from the proprietary hardware drivers dialog within Ubuntu, so it's the one that's been tested and approved by the Ubuntu team, but is a few revisions old (180 vs. 185).

---

### Post by rrplay on 2009-08-30
gungfujoe wrote

> The driver that failed to install completely was the .run file from nVidia.com (the pkg1 file, not the pkg0 file). It said it had to compile a driver, and then failed to compile. The driver that did install but failed to work is the one from the proprietary hardware drivers dialog within Ubuntu, so it's the one that's been tested and approved by the Ubuntu team, but is a few revisions old (180 vs. 185). 

a good idea would be to back up the xorg.conf you have 
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.current

and reconfigure xserver [for the change of vid cards]
$ sudo dpkg-reconfigure -phigh xserver-xorg

and reboot

I do not know why 'enabling nvidia restricted drivers' did not work for you. You may want to try enabling the restricted drivers after the xserver reconfig. you can even use Synaptic for build-essentials and headers if you have any type of GUI available to you.

renkinjutsu wrote: > what kernel do you have installed? Is it a custom kernel?
use the binary from nvidia's website.. and make sure you have your kernel headers installed 

$ uname -r 

then 
$ sudo apt-get install build-essential linux-headers-`uname -r`

$ sudo apt-get install nvidia-settings

If you still have to install the nVidia driver manually take a look here ;;
[http://forums.nvidia.com/index.php?showtopic=99513]("http://forums.nvidia.com/index.php?showtopic=99513")

Note : Remember that If you installed the video driver manually, you need to re-install them every time the kernel gets upgraded.
So it's recommended that using the drivers that comes with Ubuntu.

---

### Post by gungfujoe on 2009-09-02
> **Shadow121 said:**
> Well you have the correct driver activated according to your xorg.  Have you tried hooking up a regular computer monitor and restarting?
Obviously, I didn't get to this last weekend, but I have just done it this afternoon.  I thought for sure this would sidestep the issue (if not resolve it), but I was wrong.  I connected my Dell 2001FP via DVI, and even disconnected both the VGA and HDMI cables.  I get the same error.  I even tried telling it to reconfigure for the current display and rebooted.  Same result.

At this stage, "try to repair graphics problems" from the recovery mode successfully disables the proprietary drivers and puts me back into low-graphics mode.

I'll go on to rrplay's suggestions in a moment (as soon as the Linux system reboots)

---

### Post by gungfujoe on 2009-09-02
> **rrplay said:**
> $ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.current
$ sudo dpkg-reconfigure -phigh xserver-xorg
and reboot

I do not know why 'enabling nvidia restricted drivers' did not work for you. You may want to try enabling the restricted drivers after the xserver reconfig.
Done and.... same result.  My display doesn't have a usable configuration.

 you can even use Synaptic for build-essentials and headers if you have any type of GUI available to you.

> **rrplay said:**
> 
$ sudo apt-get install build-essential linux-headers-`uname -r`
$ sudo apt-get install nvidia-settings
I did this and rebooted, and it was still using the open source driver. I enabled the proprietary driver and rebooted, and got the same result. No usable configuration

> **rrplay said:**
> If you still have to install the nVidia driver manually take a look here ;;
[http://forums.nvidia.com/index.php?showtopic=99513]("http://forums.nvidia.com/index.php?showtopic=99513")Thanks.  As much as I'd like to stick with the drivers available from Ubuntu, they're just not working.  I'll try this procedure and report back shortly.

---

### Post by gungfujoe on 2009-09-02
Following the instructions at nvidia.com (rrplay's link above), I still get the same error as in the first post, when I mentioned trying to install the latest drivers. (transcribing, so any typos are my fault)

ERROR: Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not suported by this NVIDIA Linux graphics driver release.

Please see the log entries 'Kernel module load error' and 'Kernel messages' at the end of the file '/var/log/nvidia-installer.log' for more information.

The contents of that log file will be attached below once I save this message, open it back up on the Ubuntu system, and paste it in.

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Sep  2 17:38:55 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 185.18.36.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-15-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-15-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.28-15-gener
   ic/build SYSOUT=/lib/modules/2.6.28-15-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.28-15-generic/build SUBDIRS
   =/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/include -
   include include/linux/autoc
   onf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fn
   o-strict-aliasing -fno-common -Werror-implicit-function-declaration -fno-del
   ete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -Wa,-mtune=generic
   32 -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -m
   no-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x86/include/asm/mach-default -fn
   o-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdecl
   aration-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz5087/NVIDIA-L
   inux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -
   Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werr
   or -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ 
   -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG 
   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvidia)"  -c -o /
   tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_nv.o /tmp/sel
   fgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KER
   NEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/includ
   e -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-float 
   -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mt
   une=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno
   -asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x8
   6/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -Wdeclaration-aft
   er-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz5087/NVIDIA-Linux-x86-18
   5.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wc
   har-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -fno-def
   er-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -D
   NVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D
   "KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=
   KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/u
   sr/src/nv/.tmp_nv-vm.o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/s
   rc/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wun
   def -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Wer
   ror-implicit-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -
   msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -ma
   rch=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-
   compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dn
   ow -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-
   pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-point
   er-sign -fwrapv -I/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compar
   e -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING
   =\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KB
   UILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c
   -o /tmp/selfgz5087/NVIDIA-Linux-x8
   6-185.18.36-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz5087/NVIDIA-Linux-x86-1
   85.18.36-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include 
   -D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86
   /include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -
   Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-i
   mplicit-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft
   -float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i
   586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compa
   re -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -I
   arch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-point
   er -fno-optimize-sibling-calls -Wdeclar
   ation-after-statement -Wno-pointer-sign -fwrapv -I/tmp/selfgz5087/NVIDIA-Lin
   ux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wf
   ormat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror
   -fno-defer-pop -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5087/NVIDIA-Linux-x86-1
   85.18.36-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz5087/NVIDIA-Linux-x8
   6-185.18.36-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -
   D__KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/
   include -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-im
   plicit-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-
   float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i5
   86 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compar
   e -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Ia
   rch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointe
   r -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sig
   n -fwrapv -I/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall
   -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -
   Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185
   .18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(os_regist
   ry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz5087/NVIDIA-Li
   nux-x86-185.18.36-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz5087/NVIDIA-
   Linux-x86-185.18.36-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-float
   -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mt
   une=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno
   -asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -
   Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-poin
   ter -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-s
   ign -fwrapv -I/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wa
   ll -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenthese
   s -Wpointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -
   Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"
   185.18.36\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUIL
   D_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o
   /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.tmp_nv-i2c.o /tm
   p/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KE
   RNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/inclu
   de -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-float
   -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -mt
   une=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare -fno
   -asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarch/x8
   6/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign -fwr
   apv -I/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -Wimp
   licit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoin
   ter-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-cast
   -qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.18.3
   6\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)"  -c -o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src
   /nv/.tmp_nvacpi.o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv
   /nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function &#8216;object_is_on_stack&#8217;:
   include/linux/sched.h:2026: warning: pointer of type &#8216;void *&#8217; used in ar
   ithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function &#8216;sg_virt&#8217;:
   include/linux/scatterlist.h:199: warning: pointer of type &#8216;void *&#8217; used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq_32.h:5,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/hardirq.h:2,
                    from include/linux/hardirq.h:7,
                    from include/linux/interrupt.h:12,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:87,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/irq.h: In function &#8216;irq_to_desc&#8217;:
   include/linux/irq.h:189: warning: comparison between signed and unsigned
   In file included from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nv-linux.h:113,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: In function &#8216;zero_user_segments&#8217;:
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     ld -m elf_i386   -r -o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr
   /src/nv/nvidia.o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/
   nv-kernel.o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv.o 
   /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-agp.o /tmp/selfgz5087/N
   VIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-interface.o /tmp/selfgz5087/NVI
   DIA-Linux-x86-185.18.36-pkg1/usr/src/nv/os-registry.o /tmp/selfgz5087/NVIDIA
   -Linux-x86-185.18.36-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz5087/NVIDIA-Linux-x
   86-185.18.36-pkg1/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg
   1/usr/src/nv/nvidia.ko;) > /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/u
   sr/src/nv/modules.order
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.28-15-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.28-15-generic/Modu
   le.symvers -I /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/M
   odule.symvers -S -K /usr/src/linux-headers-2.6.28-15-generic/Module.markers 
   -M /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/Module.markers
   -w  -s
   WARNING: could not find /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D
   __KERNEL__  -Iinclude  -I/usr/src/linux-headers-2.6.28-15-generic/arch/x86/i
   nclude -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-imp
   licit-function-declaration -fno-delete-null-pointer-checks -O2 -m32 -msoft-f
   loat -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i58
   6 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe -Wno-sign-compare
   -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iarc
   h/x86/include/asm/mach-default -fno-stack-protector -fno-omit-frame-pointer 
   -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointer-sign 
   -fwrapv -I/tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith -Wno-multichar -Werror -fno-defer-pop -MD -Wsign-compare -Wno-
   cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"185.
   18.36\" -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=K
   BUILD_STR(nvi
   dia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz
   5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz5087
   /NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/cpufeature.h:166,
                    from /usr/src/linux-headers-2.6.28-15-generic/arch/x86/incl
   ude/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;set_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h: In f
   unction &#8216;clear_bit&#8217;:
   /usr/src/linux-headers-2.6.28-15-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type &#8216;void *&#8217; used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/sr
   c/nv/nvidia.mod.c:1:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:57: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
     ld -r -m elf_i386  --build-id -o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.3
   6-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/
   usr/src/nv/nvidia.o /tmp/selfgz5087/NVIDIA-Linux-x86-185.18.36-pkg1/usr/src/
   nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [    9.202966] type=1505 audit(1251926946.676:2): operation="profile_load"
   name="/sbin/dhclient-script" name2="default" pid=1843
   [    9.203053] type=1505 audit(1251926946.676:3): operation="profile_load"
   name="/sbin/dhclient3" name2="default" pid=1843
   [    9.203083] type=1505 audit(1251926946.676:4): operation="profile_load"
   name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default"
   pid=1843
   [    9.203111] type=1505 audit(1251926946.676:5): operation="profile_load"
   name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1843
   [    9.302918] type=1505 audit(1251926946.776:6): operation="profile_load"
   name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1848
   [    9.303086] type=1505 audit(1251926946.776:7): operation="profile_load"
   name="/usr/sbin/cupsd" name2="default" pid=1848
   [    9.323012] type=1505 audit(1251926946.797:8): operation="profile_load"
   name="/usr/sbin/mysqld" name2="default" pid=1852
   [    9.342834] type=1505 audit(1251926946.817:9): operation="profile_load"
   name="/usr/sbin/tcpdump" name2="default" pid=1856
   [    9.667031] RPC: Registered udp transport module.
   [    9.667034] RPC: Registered tcp transport module.
   [    9.743929] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
   [   41.751639] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state
   recovery directory
   [   41.751668] NFSD: starting 90-second grace period
   [   45.067703] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
   [   45.067706] Bluetooth: BNEP filters: protocol multicast
   [   45.082881] Bridge firewalling registered
   [   46.807346] ppdev: user-space parallel port driver
   [   47.483368] mtrr: base(0xfb000000) is not aligned on a size(0xe00000)
   boundary
   [   50.524938] forcedeth 0000:00:0f.0: irq 2299 for MSI/MSI-X
   [  636.863044] NVRM: This PCI I/O region assigned to your NVIDIA device is
   invalid:
   [  636.863045] NVRM: BAR1 is 0M @ 0x0 (PCI:0002:00.0)
   [  636.863048] NVRM: The system BIOS may have misconfigured your GPU.
   [  636.863052] nvidia: probe of 0000:02:00.0 failed with error -1
   [  636.863072] NVRM: The NVIDIA probe routine failed for 1 device(s).
   [  636.863074] NVRM: None of the NVIDIA graphics adapters were initialized!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

If anything in this log can help figure out what I need to do to make the Ubuntu-supplied drivers work, that'd probably be even better than helping me get the manually-installed drivers to work.

One thing that comes to mind...  The motherboard has a GF7050 on it.  I haven't used it, and it did not interfere with the ATI card.  I've looked through the manual, the BIOS settings, and the physical motherboard (for jumpers), but have not found any way to explicitly disable the onboard video.  I assumed it must auto-disable when not in use (an assumption that was reinforced when it worked fine with an ATI graphics card plugged in).  Might this somehow mess up the proprietary drivers, even though it doesn't affect the generic drivers?

---

### Post by iansane on 2009-09-02
Something obviously changed when they got rid of nvidia-glx-new. I have the same problem for both nvidia and ati with anything newer than Hardy LTS. I'm wondering if I'll ever be able to take advantage of Jaunty or intrepid but they just don't work for me now. I also have friends who have the same problem and the only way to get 3d working was to stay with Hardy and glx-new. I was able to use the vesa driver but couldn't do to much without my desktop freezing. Even a web page with to much flash or opening and closing windows to fast would cause video to freeze up using vesa driver so I had to go back to Hardy.

Anyone know if there are plans in the works to fix the frglx so it works like glx-new?

---

### Post by gungfujoe on 2009-09-02
> **iansane said:**
> Something obviously changed when they got rid of nvidia-glx-new. I have the same problem for both nvidia and ati with anything newer than Hardy LTS.I had no such problems with my ATI 3450 video card, but the fact that ATI's Linux drivers don't let you turn overscan compensation off was a real turnoff, as was the fact that it couldn't handle 1080p output without significant tearing artifacts.

I've spent over six months trying to get this HTPC up and running, and honestly, I'm almost content to just bide my time until Windows 7 comes out, buy a copy for my primary system, and use one of my old XP licenses on this machine and start over with MediaPortal. Between audio issues (spent hours researching how to send AC3 over S/PDIF), video issues (see above), and network issues (network connection refuses to load before mythbackend, even if I adjust the boot order), Linux has been one problem after another. :(

---

### Post by RedRat on 2009-09-02
Just out of curiosity have you tried to use EnvyNG to install the drivers. Remember when you run anything in regard to drivers you must do it with the sudo command, otherwise it doesn't "stick"

---

### Post by gungfujoe on 2009-09-02
> **RedRat said:**
> Just out of curiosity have you tried to use EnvyNG to install the drivers. Remember when you run anything in regard to drivers you must do it with the sudo command, otherwise it doesn't "stick"
No, I don't have EnvyNG.

For the Ubuntu-supplied drivers, I'm using the Hardware Manager, or whatever it's called (the proprietary driver list).  For the nVidia-supplied drivers, I followed the [linked instructions](http://forums.nvidia.com/index.php?showtopic=99513) exactly, including prefacing the commands with sudo.

---

### Post by RedRat on 2009-09-02
> **gungfujoe said:**
> No, I don't have EnvyNG.

For the Ubuntu-supplied drivers, I'm using the Hardware Manager, or whatever it's called (the proprietary driver list).  For the nVidia-supplied drivers, I followed the [linked instructions]("http://forums.nvidia.com/index.php?showtopic=99513") exactly, including prefacing the commands with sudo.

Not saying that envyNG will save you, but it might be worth a try. Welcome to Ubuntu's greatest annoyance: Graphics. I used to have this problem too, but I am running Hardy and envyNG worked for me in terms of installing the correct driver, I still use the older one 175 because it works. I am not inclined to &quot;fix&quot; what ain't broken.

You can get envyNG by typing in:
sudo apt-get envyng

then run it with:
sudo envyng 
or 
gksudo envyng

Once you have made your selection you might also want to download nvidia-settings:
sudo apt-get nvidia-settings
then run it with
sudo nvidia-settings
or
gksudo nvidia-settings

Whenever you run nvidia-settings do with sudo or gksudo.

---

### Post by gungfujoe on 2009-09-03
EnvyNG has the same result.  It installs the driver for me, but I get the same set of errors I mentioned in the first post.

Any other suggestions?  I can wipe the HD and start over (which I guess I'll do this weekend, if it comes to that), but I really don't want to.  It took a lot of work to get all of the other components working, and I'd hate to have to redo all that work, especially since there's no guarantee it'll solve this problem.

---

### Post by rrplay on 2009-09-03
gungfujo previously wrote

> I did this and rebooted, and it was still using the open source driver. I enabled the proprietary driver and rebooted, and got the same result. No usable configuration

you simply cannot have both the nVidia proprietary driver and the Ubuntu restricted drivers and packages at the same time..they just DO NOT play along nicely on the same install.
you'll be better off if you simply uninstall the nvidia drivers
sudo sh nvidia XXX  -uninstall  completely 
get rid of Envy and uninstall any previous 'botched' nvidia packages reboot search Syaptic for any and all nvidia packages make sure to disable the resticted drivers reboot
reconfigure xserver
sudo dpkg-reconfigure xserver-xorg
 and systematically reboot to a default xorg.conf  on your current install so that that when you reboot a pop up will appear asking if you want to enable the Ubuntu proprietary drivers.[restricted] and reboot.[the longest part of this is the reboots!]

should you reinstall 9.04   before you apt-get update anything enable Ubuntu  nvidia restricted drivers and reboot.

good luck

---

### Post by gungfujoe on 2009-09-04
> **rrplay said:**
> you simply cannot have both the nVidia proprietary driver and the Ubuntu restricted drivers and packages at the same time..they just DO NOT play along nicely on the same install.
I haven't gotten _any_ of them successfully installed and activated, and each time I tried a different method of installing the drivers, I followed the various instructions for removing the old drivers.  As far as I've been able to tell, the uninstallations were successful.

---

### Post by rrplay on 2009-09-05
Seems like you are getting really close to figuring this all out
Boot into recovery mode and get to the command line and enter this.

```
dpkg-reconfigure xserver-xorg
```

you now have a new xorg.conf file in /etc/X11 this is the file you want when you reboot to enable the nvidia restricted drivers a bit more troubleshooting should work this out..
Have you tried booting from a live CD to see if that nvidia card is detected? Should you reinstall you really want to use ubuntu,s restricted drivers so you will not have this again.

---

### Post by gungfujoe on 2009-09-05
> **rrplay said:**
> Seems like you are getting really close to figuring this all out
Boot into recovery mode and get to the command line and enter this.

```
dpkg-reconfigure xserver-xorg
```
I'm learning a lot about Linux, but I don't feel I'm getting any closer to figuring out the problem, since I've attempted to install the drivers three different ways, and they've all failed in the same way.  I've run the command above between every single attempt, though I've always included "-phigh" in it, which shouldn't make or break it, since it appears to just be a thread priority setting.

I can try this, but I'm pretty sure it's just repeating a step I've tried a number of times before.

> **rrplay said:**
> Have you tried booting from a live CD to see if that nvidia card is detected? Should you reinstall you really want to use ubuntu,s restricted drivers so you will not have this again.

I haven't tried the Live CD. I didn't think that the restricted drivers were included on the LiveCD (and since it's running off nonwritable media, it won't accept any config changes beyond what's included on the disc, will it?).  Ideally, the restricted drivers are what I want. I did first try the nvidia.com drivers (I couldn't select the restricted drivers without the GUI working), but since they didn't even compile successfully, they didn't install, so the first set of drivers I actually installed were the Ubuntu restricted ones.

---

### Post by gungfujoe on 2009-09-05
Ugh.  I reinstalled Mythbuntu 9.04 from scratch, and I get the same error upon first reboot.  This is a completely clean, stock install, with no updates or anything, and with the proprietary drivers selected during initial setup.

I also tried the Live CD, but as I indicated in my last reply, it doesn't support the proprietary video drivers.  You can tell it to install them, but activating them requires a reboot, which obviously resets the Live CD back to its initial state.

---

### Post by markmaus on 2009-09-07
I am having the same problem:  Install Mythbuntu 9.04 from disk and select Nvidia driver during the install process.  This results in a blank screen (X will not load).  I then re-boot, select "Recovery Mode" from the grub menu and run xfix, and then resume boot.  X will then load properly, and I can watch TV but because of the crappy open graphics driver for the video card the motion is choppy and animated looking.  I've also tried using the hardware detection tool in Ubuntu to load the Nvidia driver but that doesn't work either (blank screen). I've tried typing "dpkg-reconfigure xserver-xorg" into a root shell during Recovery Mode and all I get is a bunch of questions about the keyboard setup.  Nothing is mentioned about video drivers.  I guess that I'll try to dig up the kernel headers, install a compiler and get the Nvidia driver from Nvidia and compile that.  I'm also running the 64 bit Mythbuntu.  I don't really understand why this video driver won't work.  It worked fine in Mythbuntu 8.10.  I'll try anything that you can recommend.  Thanks,

---

### Post by markmaus on 2009-09-07
I got the Nvidia driver from Nvidia's website and compiled a kernel module and now the whole system is screwed up.  X won't load at all.  I think it is time to give up on Mythbuntu 9.10.  I guess that I'll install Mythbuntu 8.10 this time around.

---

### Post by gungfujoe on 2009-09-07
It appears that this is a hardware conflict of some sort, and NOT a Linux driver issue.  Apparently a lot of people are having trouble getting the GeForce 9400 working on motherboards that also have integrated video (and MSI's tech support basically said "nope, won't work, you have to disable onboard video first" - great idea, if this motherboard **had** such an option.  Still waiting to hear back from ECS tech support as to whether or not there's some hidden method to disable it).

I wiped the drive (again) and tried a Windows XP install (since you don't have to activate for 30 days, I didn't need an available license for this test), and the drivers failed to install, giving me an error about not finding any supported hardware.  Fails in Linux, fails in Windows... sounds like a hardware conflict.  My next step will be to install this video card in another system to verify that the card does indeed work in a motherboard without onboard video before going out and buying yet another motherboard.

At least I now seem to know what the problem is, but it requires buying yet another piece of replacement hardware on a machine that has been giving me nothing but trouble in the 8 months since I started piecing it together. I've built a dozen or so machines, and have never run into as many problems as I have with this. I've gone through three motherboards (and now apparently need a fourth), three sets of RAM, two video cards, had various driver problems, networking problems, and probably a couple other things that I'm either forgetting or haven't yet encountered.

---

### Post by markmaus on 2009-09-07
I tend to disagree.  I don't think that it is a hardware conflict (in my case).  I think it is a driver issue.  I just did a fresh install of Mythbuntu 8.10 and selected the Nvidia proprietary driver during the install process.  The proprietary nvidia driver in 8.10 works fine for me.  I'm watching Barney on PBS in high def as I write this.  I actually have the GeForce 9300 GS PCIe video card and do not have integrated video on my MSI Mobo (so my case is a little different than yours), but HDTV is working great with Mythbuntu 8.10.  I wish I could say the same with Mythbuntu 9.10. You might want to find Mythbuntu 8.10 on the web and try installing that.  Right now I'm running "apt-get install ubuntu-desktop" since this machine serves as desktop as well as DVR.  I'll then try to upgrade to 9.04.  That should be interesting. It sounds like you have a nightmare of a machine build on your hands.  I hope my system trouble shooting is of some help to you.
Mark

---

### Post by gungfujoe on 2009-09-07
Sorry markmaus, I should have been more clear.  I was providing an update to the *problem that this thread is about*, not a response to your last message.

If I could mark this thread closed without marking it "solved," I would.  I know what the problem is now, but as far as I can tell, there's no actual solution, so it's not "solved."

---

### Post by markmaus on 2009-09-07
I still think that it would be worth you time to try installing Mythbuntu 8.10 on this machine.  Since it worked for me, and I have similar hardware and the exact same video problem as you when installing Mythbuntu 9.04.  Just my 2 cents worth.  I'll be quiet now. Good luck.

---

### Post by gungfujoe on 2009-09-07
when even the idiot-friendly Windows drivers won't recognize the hardware, I don't see any purpose in spending a couple hours trying a different Linux version. It might work, but it's too much of a longshot chance to be worth the time it'd take. Now, if, upon getting a new motherboard, the Windows drivers work, but the Ubuntu 9.04 drivers don't, then maybe I'll try 8.10.

---

