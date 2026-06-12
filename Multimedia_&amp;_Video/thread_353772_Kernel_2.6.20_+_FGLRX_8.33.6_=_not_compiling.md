---
title: "Kernel 2.6.20 + FGLRX 8.33.6 = not compiling"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by Xemanth on 2007-02-05
Does anybody have patch for this problem?

```

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.20/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/kernels/linux-2.6.20'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:198: error: expected declaration specifiers or ‘...’ before ‘mlock’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:198: error: expected declaration specifiers or ‘...’ before ‘addr’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:198: error: expected declaration specifiers or ‘...’ before ‘len’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:200: warning: return type defaults to ‘int’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function ‘_syscall2’:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:200: error: expected declaration specifiers before ‘_syscall2’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:233: error: parameter ‘__ke_debuglevel’ is initialized
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:234: error: parameter ‘__ke_moduleflags’ is initialized
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:237: error: storage class specified for parameter ‘__mod_author237’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:237: error: parameter ‘__mod_author237’ is initialized
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:237: warning: ‘__used__’ attribute ignored
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:237: error: section attribute not allowed for ‘__mod_author237’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:238: error: storage class specified for parameter ‘__mod_description238’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:238: error: parameter ‘__mod_description238’ is initialized
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:238: warning: ‘__used__’ attribute ignored
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:238: error: section attribute not allowed for ‘__mod_description238’
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:242: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
(BLABLABLABLABLABLLABLAB 200 lines same issue)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:198: error: parameter name omitted
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:198: error: parameter name omitted
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4492: error: expected ‘{’ at end of input
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/firegl_public.o] Error 1
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/kernels/linux-2.6.20'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.

```

---

### Post by barney_1 on 2007-02-05
Well, I would make sure that you don't have another version of fglrx already installed:
```
sudo apt-get remove xorg-driver-fglrx
```
Then try compiling again.

Hope that helps.

---

### Post by Xemanth on 2007-02-06
> **barney_1 said:**
> Well, I would make sure that you don't have another version of fglrx already installed:
```
sudo apt-get remove xorg-driver-fglrx
```
Then try compiling again.

Hope that helps.

No I don't have old version installed.
"Package xorg-driver-fglrx is not installed, so not removed"

Problem occurs with my 2.6.20-rc7 and with the newest stable. But i haven't tested any 2.6.20 release candidates.

With kernel 2.6.19.2 I don't get those errors and fglrx compiles perfectly.

Can somebody else reproduce ?

---

### Post by acankat on 2007-02-06
from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide:](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide:)

"the fglrx source code requires Linux 2.6.19 or lower. It is not yet prepared for 2.6.20."

---

### Post by Xemanth on 2007-02-06
> **acankat said:**
> from [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide:](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide:)

"the fglrx source code requires Linux 2.6.19 or lower. It is not yet prepared for 2.6.20."

Oh I see. Back to use old horse 2.6.19.2. :)

edit: So there ain't any unofficial dirty patch which could fix this problem ?

---

### Post by GoingDown on 2007-02-08
Here is unofficial patch:

[http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch](http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch)

Haven't tested it yet.

EDIT: Yes, seems to work. And actually I don't know if patch is unofficial or not.

---

### Post by Xemanth on 2007-02-08
> **GoingDown said:**
> Here is unofficial patch:

[http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch](http://darcs.frugalware.org/repos/frugalware-current/source/x11-extra/fglrx/fglrx-2.6.20.patch)

Haven't tested it yet.

EDIT: Yes, seems to work. And actually I don't know if patch is unofficial or not.

I'll test that later this evening.

---

### Post by acankat on 2007-02-09
> **Xemanth said:**
> I'll test that later this evening.

Does anybody know how to apply this patch?

---

### Post by GoingDown on 2007-02-09
Here is what I did:

I downloaded and installed newest ati drivers (ati-driver-installer-8.33.3-x86_64.run)

After installation, I just downloaded the patch and (as a root):

cd /lib/modules/fglrx/build_mod
patch -p6 < {path to patch}/fglrx-2.6.20.patch
./make.sh
cd ..
./make_install.sh

And then restart X (of course you might to need to modify your xorg.conf if you are doing new install of ati fglrx drivers).

---

### Post by asforme on 2007-02-15
I have followed all instructions and am still getting the following errors:

My /usr/share/ati/fglrx-install.log is attached.  There are about a billion errors, but I though those might be expected, hence the need for a patch.

So then I go and try to patch anyway which shows:
```

root@greenmachine:/lib/modules/fglrx/build_mod# patch -p6 < /home/clint/fglrx-2.6.20.patch
missing header for unified diff at line 3 of patch
patching file firegl_public.c
Hunk #1 succeeded at 194 (offset 13 lines).

```

build.sh seems to go okay
```

root@greenmachine:/lib/modules/fglrx/build_mod# ./make.sh
ATI module generator V 2.0
==========================
initializing...
cat: /lib/modules/2.6.20/build/include/linux/version-*.h: No such file or directory
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
 Assuming default munmap API
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.20/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-2.6.20'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:529: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 'firegl_stub_open':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:652: warning: assignment discards qualifiers from pointer target type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function '__ke_request_irq':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2641: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function '__ke_smp_call_function':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4081: warning: passing argument 1 of 'smp_call_function' from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function 'KAS_ExecuteAtLevel':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:4506: warning: 'flags' may be used uninitialized in this function
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC4.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC4
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-2.6.20'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================

```

But make_install.sh does not.
```
root@greenmachine:/lib/modules/fglrx/build_mod# cd ..
root@greenmachine:/lib/modules/fglrx# ./make_install.sh
- recreating module dependency list
- trying a sample load of the kernel modules
FATAL: Error running install command for fglrx
failed.

```

Here is DMESG
```

[  142.535000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  142.537000] [fglrx] Maximum main memory to use for locked dma buffers: 3389 MBytes.
[  142.537000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed

```

I read that fire_stub_register failed can be caused by  having the radeon drivers installed so I tried again after doing an apt-get remove xserver-xorg-driver-radeon.  Still gave the same errors.  I have tried this from a terminal after totally killing gdm and doing it from gnome.  ](*,)

---

### Post by GoingDown on 2007-02-15
> **asforme said:**
> I read that fire_stub_register failed can be caused by  having the radeon drivers installed so I tried again after doing an apt-get remove xserver-xorg-driver-radeon.  Still gave the same errors.  I have tried this from a terminal after totally killing gdm and doing it from gnome.  ](*,)

It seem your patch and build were successfull.

Can you check that you don't have radeon module loaded when the make_install.sh script is ran? If it is, then fglrx module might fail. 

By the way, do you have PCI-E or AGP card? And you have drm and agp/pci-x support compiled in?

fglrx-install log you have attached seem to be from previous install (when you have first ran the ati installer) when the patch was not installed...  (EDIT) ... as you said in your message :-)

---

### Post by asforme on 2007-02-15
lsmod shows no radeon present.
```

root@greenmachine:/lib/modules/fglrx# ./make_install.sh
- recreating module dependency list
- trying a sample load of the kernel modules
FATAL: Error running install command for fglrx
failed.
root@greenmachine:/lib/modules/fglrx# lsmod
Module                  Size  Used by
rfcomm                 39192  0
l2cap                  23936  5 rfcomm
bluetooth              53796  4 rfcomm,l2cap
capability              5000  0
commoncap               7360  1 capability
cpufreq_userspace       4264  0
cpufreq_ondemand        8268  0
cpufreq_powersave       1856  0
button                  7824  0
video                  15556  0
serio_raw               7108  0
i2c_nforce2             5888  0
pcspkr                  3200  0
evdev                  10240  2
usblp                  14080  0
k8temp                  5696  0
i2c_core               22016  1 i2c_nforce2
dm_mirror              22164  0
ohci1394               35632  0
ieee1394              298040  1 ohci1394
ohci_hcd               20804  0
ide_generic             1344  0 [permanent]
amd74xx                14108  0 [permanent]
generic                 4932  0 [permanent]
sd_mod                 21440  2
thermal                13896  0
processor              25464  1 thermal
fan                     4804  0

```

I'm pretty sure I checked everything in the kernel conf that looked like it was necessary for PCI-E (Radeon X1900XT), though I was pretty frugal trying to get rid of everything I didn't deem necessary.  What exactly am I looking for?  I have my kernel.conf that I used here if you want to see it.  This is really confusing me.

[Edit]  I just did some searches through my kernel.conf.
```
CONFIG_DRM=y
# CONFIG_DRM_TDFX is not set
# CONFIG_DRM_R128 is not set
CONFIG_DRM_RADEON=y
# CONFIG_DRM_I810 is not set
# CONFIG_DRM_I830 is not set
# CONFIG_DRM_I915 is not set
# CONFIG_DRM_MGA is not set
# CONFIG_DRM_SIS is not set
# CONFIG_DRM_VIA is not set
# CONFIG_DRM_SAVAGE is not set

```
Looks like I have DRM
```

CONFIG_PCIEPORTBUS=y
CONFIG_PCIEAER=y

```
The only thing I'm missing compared to the generic config that has the phrase pcie is pcie_hotplug.
[/edit]

---

### Post by GoingDown on 2007-02-16
it seems you have radeon module built-in on your kernel

```

CONFIG_DRM_RADEON=y

```

You must remove it, but keep support for DRM. I have DRM made as module, but built-in drm should work as well. Also note that you need to enable AGP support 
(/dev/agpgart) even if you have PCI-E graphics card.

---

### Post by asforme on 2007-02-16
That did it, thanks.  Sorry for my n00bieness there.  This is the first time I've compiled a kernel and instinct said "hey, I have a Radeon card, I should include radeon".  Everything else seems to be working perfectly and my computer now runs much faster.

---

### Post by bheadlim on 2007-05-21
I couldn't download the unofficial patch, it is broken link.

Is there any official patch or new link?

---

