---
title: "FGLRX + RT Kernel"
date: 2009-09-14
forum: Multimedia Software
---

### Post by g-raf on 2009-09-14
Is there anyway to get the proprietary ati/amd fglrx graphics driver working in the realtime kernel? I'm dying to figure out how it can be accomplished.

---

### Post by g-raf on 2009-09-15
bump

---

### Post by g-raf on 2009-09-16
I've heard that the fglrx driver is able to be installed with a rt kernel patch so that it works with the rt kernel. Is there a link to any more information or any more information that someone could give me please? Thanks.

---

### Post by markbuntu on 2009-09-16
Well, the rt patch was in the wrong file for about a year so fglrx would not install properly but that was fixed a few drivers ago. Personally I have not tested fglrx with the jaunty rt kernel because it will not boot for me for other reasons but I did get fglrx to work with the rt kernel in my Hardy Ubuntustudio.

You can give it a try. You will need to be runing the rt kernel ( with the generic VESA driver) and do a manual install and do aticonfig --initial -f after installing, then reboot. If the driver fails then you need to reboot into the recovery kernel and use the fix x option to get back to the VESA driver or you can uninstall the driver by running the script usr/share/ati/fglrx-uninstall.sh

If you give this a try let us know how you make out or what problems you encounter.

good luck

---

### Post by g-raf on 2009-09-16
It didn't work. In recovery mode, choosing the "automatically fix graphics problems" didn't work either, so i needed to sudo apt-get remove the driver an dependencies after loading the root kernel. 

HOWEVER, i didn't install the driver from a source file (not sure where to download that or how to install it from source properly), but installed the xorg-driver-fglrx and dependencies through synaptic. Is that where i made a mistake, by chance? One of the dependencies in synaptic included a jaunty kernel patch. However, i'm only using the ubuntu studio rt kernel, not a generic kernel.

---

### Post by g-raf on 2009-09-16
I would like to try something like this (link),

[http://ubuntuforums.org/showthread.php?t=756236](http://ubuntuforums.org/showthread.php?t=756236)

but these were instructions for how to do it on hardy or gutsy, so it doesn't seem like it's the instructions i should be using for jaunty.

---

### Post by g-raf on 2009-09-17
Should i not install the xorg-driver-fglrx through synaptic? If so, then should i just open up the terminal and type "sudo get-apt install xorg-driver-fglrx"? What would the difference be? What is "installing it manually"?

---

### Post by markbuntu on 2009-09-17
I don't think the patch was fixed until the 9.6 driver so no, you should not use the driver available with synaptics. You should get the latest driver from ati.

---

### Post by g-raf on 2009-09-18
markbuntu, sorry. Now i have a bigger favor to ask: from ati, which driver should i download & install? There are so many, here is the website with the list of downloads: 

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

This is my video card:

ATI Technologies Inc Mobility Radeon HD 3400 Series

---

### Post by markbuntu on 2009-09-18
You should choose linux x86 for 32 bit or x86_64 for a 64 bit OS and then Radeon and 3xxx from the lists. There is a link from the download page to release notes and installed instructions, be sure to read them. Also make sure you have removed any previous drivers before installing a new one.

---

### Post by g-raf on 2009-09-18
In the installation instructions, if i choose to "generate distribution specific driver package," but that only allows me to select between RedHat and SuSE stuff. Not sure how to make this install the kernel modules for the 2.6.28-3 rl kernel.

---

### Post by markbuntu on 2009-09-20
Instructions are here use the manual installation method

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by g-raf on 2009-09-25
> **markbuntu said:**
> Instructions are here use the manual installation method

[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I followed these instructions, installed the packages and rebooted my computer. Then i opened up the terminal and typed "fglrxinfo" to check if it is properly installed and i got this:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

Anyone know what this means? Doesn't seem like the driver is working.

---

### Post by gurpal2000 on 2009-10-03
> **g-raf said:**
> I followed these instructions, installed the packages and rebooted my computer. Then i opened up the terminal and typed "fglrxinfo" to check if it is properly installed and i got this:



Anyone know what this means? Doesn't seem like the driver is working.

i got the same - any ideas?

---

### Post by g-raf on 2009-10-10
bump

---

### Post by gurpal2000 on 2009-10-10
> **gurpal2000 said:**
> i got the same - any ideas?

I must say things seem to be much better in karmic beta 9.10. Graphics looks good to me with 3D all working !!

---

### Post by markbuntu on 2009-10-12
Is that with the rt kernel?

---

### Post by gurpal2000 on 2009-10-12
> **markbuntu said:**
> Is that with the rt kernel?

no sorry, just with the 64-bit desktop kernel. I tried the 32-bit pae kernel but the graphics driver was messed up and left X in a weird state. I wish ATI or AMD or Ubuntu would comment on this.

---

### Post by markbuntu on 2009-10-12
What sort of messages did you get???
I used to get these when trying to install on the rt kernel but not since the 9.7 driver on Hardy at least.

```

Error!  Patch fglrx-rt-compat.patch as specified in dkms.conf cannot be
found in /var/lib/dkms/fglrx/8.602/build/patches/.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.24-24-rt (x86_64) first.
Done.

```

This was because the rt patches were in /patches/patches instead of /patches. 

I suppose I should give it a whirl on karmic and maybe start some bug reporting. Did you file a bug report at launchpad against fglrx about your problems? you really should.

---

### Post by gurpal2000 on 2009-10-12
> **markbuntu said:**
> What sort of messages did you get???
I used to get these when trying to install on the rt kernel but not since the 9.7 driver on Hardy at least.

```

Error!  Patch fglrx-rt-compat.patch as specified in dkms.conf cannot be
found in /var/lib/dkms/fglrx/8.602/build/patches/.
Installing initial module

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.24-24-rt (x86_64) first.
Done.

```This was because the rt patches were in /patches/patches instead of /patches. 

I suppose I should give it a whirl on karmic and maybe start some bug reporting. Did you file a bug report at launchpad against fglrx about your problems? you really should.

Well the actual bug reporter applet keeps crashing! I just got a blank screen and none of the special key combos worked or did anything. I had to boot into a safe kernel and start over. It's quicker for me to reinstall karmic in various configs and try trial and error (i have a pretty fast machine)

---

### Post by markbuntu on 2009-10-12
Well, I just gave it a whirl with the latest karmic rt kernel and no black screen at least but also no kernel modules got installed so no 3D and a very slow screen. 

So I tried to make the kernel modules myself and found out I had no kernel headers installed, meh. Installing them got me this
```


Selecting previously deselcted package linux-rt-headers-2.6.31-8,
unpacking linux-rt-headers-2.6.31-8 (from .../linux-rt-headers-2.6.31-8.10_all.deb
Selecting previously deselcted package linux-headers-2.6.31-8-rt,
Unpacking linux-headers-2.6.21-8-rt (from.../linux-headers-2.6.31-8-rt_2.6.31-8.10_amd64.deb

Setting up linux-rt headers-2.6.31-8 (2.6.31-8.10)
Setting up linux-headers-2.6.31-8-rt (2.6.31-8.10)
run-parts: executing /etc/kernel/header_postinst.d/dkms

* Running DKMS auto installation service for kernel 2.6.31.8-rt


*   fglrx (8.660)...
fglrx (8.660): Installing module.
.....(bad exit status: 6)
  Build failed.  Installation skipped.
   ....fail!

run-parts: executing /etc/kernel/headers_postinst.d/nvidia-common

```

OK, so try something else, like running make from /usr/src/fglrx-8.660. Again fail!!
```

AMD kernel module generator version 2.1
.
Active kernel:
uname -a = Linux mark-desktop 2.6.31-8-rt #10-Ubuntu SMP PREEMPT RT Sat Oct 10 05:02:01 UTC 2009 x86_64 GNU/Linux
uname -s = Linux
uname -m = x86_64
uname -r = 2.6.31-8-rt
uname -v = #10-Ubuntu SMP PREEMPT RT Sat Oct 10 05:02:01 UTC 2009
.
Target kernel:
uname -a = Linux mark-desktop 2.6.31-8-rt #10-Ubuntu SMP PREEMPT RT Sat Oct 10 05:02:01 UTC 2009 x86_64 GNU/Linux
uname -s = Linux
uname -m = x86_64
uname -r = 2.6.31-8-rt
uname -v = #10-Ubuntu SMP PREEMPT RT Sat Oct 10 05:02:01 UTC 2009
.
OsVersion says: SMP=1
file /proc/kallsyms says: SMP=1
file /lib/modules/2.6.31-8-rt/build/include/linux/autoconf.h says: SMP=1
file /lib/modules/2.6.31-8-rt/build/include/linux/autoconf.h says: MODVERSIONS=1
.
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.31-8-rt/build SUBDIRS=/usr/src/fglrx-8.660/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-8-rt'
  CC [M]  /usr/src/fglrx-8.660/2.6.x/firegl_public.o
In file included from /usr/src/fglrx-8.660/2.6.x/firegl_public.c:443:
/usr/src/fglrx-8.660/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/usr/src/fglrx-8.660/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/usr/src/fglrx-8.660/2.6.x/firegl_public.c: In function &#8216;firegl_init_module&#8217;:
/usr/src/fglrx-8.660/2.6.x/firegl_public.c:1028: error: expected expression before &#8216;{&#8217; token
/usr/src/fglrx-8.660/2.6.x/firegl_public.c: In function &#8216;KAS_Mutex_Initialize&#8217;:
/usr/src/fglrx-8.660/2.6.x/firegl_public.c:5001: error: implicit declaration of function &#8216;init_MUTEX&#8217;
make[2]: *** [/usr/src/fglrx-8.660/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/usr/src/fglrx-8.660/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-8-rt'
make: *** [kmod_build] Error 2
build failed with return value 2

```

Ok then, I think I have something for a bug report now.

---

### Post by markbuntu on 2009-10-16
UPDATE:

The latest updates from today include a new rt patch for fglrx that now works with the 2.6.31-8rt kernel, Hooray!!!

Just get the latest updates and then while running the rt kernel remove and reactivate fglrx with Hardware Manger, reboot and viola!!

---

