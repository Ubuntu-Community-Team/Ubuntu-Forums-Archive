---
title: "problems with Radeon XPRESS 200M"
date: 2010-06-06
forum: Multimedia Software
---

### Post by boonenoob on 2010-06-06
im having problems getting drivers for my graphics card. I haven't been able to find a Linux version of the driver. heres the Specs:

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 7
    Memory at c8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [size=256]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Kernel modules: radeonfb, radeon

could someone help me out?

---

### Post by boonenoob on 2010-06-06
tried to install fglrx and got this: 
installArchives() failed: (Reading database ...  
dpkg: warning: files list file for package `clamav-base' missing, assuming package has no files currently installed.<-idk what the ef this is
 (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 185649 files and directories currently installed.) 
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_i386.deb) ... 
 
[Warning] Uninstall : inst_path_default or inst_path_override 
 does not exist in /etc/ati.  This suggests that the ATI driver 
 is not installed, the ATI driver is only partially installed, 
 or the current ATI driver installed is an older version than the 
 one this script was designed for.  Both files listed above are 
 required for determining where installed files are located. 
 To force uninstallation of the driver by guessing where the 
 uninstallation files are located, set the FORCE_ATI_UNINSTALL 
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended). 
 
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 1 
Selecting previously deselected package fglrx-amdcccle. 
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.723.1-0ubuntu3_i386.deb) ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb 
dpkg: dependency problems prevent configuration of fglrx-amdcccle: 
 fglrx-amdcccle depends on fglrx; however: 
  Package fglrx is not installed. 
dpkg: error processing fglrx-amdcccle (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 fglrx-amdcccle

---

### Post by boonenoob on 2010-06-06
i found the install log: 
Unloading radeon module...
Unloading drm module...
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.32-22-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:443:
/lib/modules/fglrx/build_mod/2.6.x/drm_proc.h: In function &#8216;FGLDRM__vma_info&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/drm_proc.h:497: warning: format &#8216;%08lx&#8217; expects type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;phys_addr_t&#8217;
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;KCL_SetPageCache_Array&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1316: warning: passing argument 1 of &#8216;KCL_ConvertPageToKernelAddress&#8217; makes pointer from integer without a cast
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:325: note: expected &#8216;void *&#8217; but argument is of type &#8216;long unsigned int&#8217;
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function &#8216;KCL_MapPageToPfn&#8217;:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:1615: warning: unused variable &#8216;bus_addr&#8217;
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_debug.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_ioctl.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_io.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_pci.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_str.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_wait.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Reboot required.

---

### Post by boonenoob on 2010-06-07
holy jesus, i almost broke my computer. apparantly, fglxst or w/e does NOT work with unsupported drivers. i uninstalled fglxst, but now i get this when trying to test the 3d with glxgears: 
Segmentation fault

someone help please >.>

---

### Post by boonenoob on 2010-06-07
hmmm. it seems to have fixed itself somehow... this is too bizzare. i rebooted again to make sure. oh, wait a sec. now i remember, DO NOT F'IN INSTALL ATI CATALYST CONTROLL CENTER ON A COMPUTER WITH A RADEON 200M!! *ahem* anyways, it got fixed after I completely removed ati catalyst controll center and flgxst / w/e.

---

### Post by boonenoob on 2010-06-07
a mod should make a sticky warning people with discontinued cards about installing ati catalyst controll center

---

### Post by akeem_da_dream on 2010-06-10
umm, so what exactly did u do here? I have the 200m card too, with ubuntu 10.04, and for some reason cannot get my 2nd monitor detected. apparently aticonfig cannot detect a graphics card either.

---

