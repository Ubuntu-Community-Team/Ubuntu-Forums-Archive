---
title: "Can't Get Cuda to Install on Ubuntu..."
date: 2014-05-16
forum: Multimedia Software
---

### Post by chris231 on 2014-05-16
I  can't seem to install Cuda successfuly on Ubuntu on my laptop.  I need  it in order to properly use Dax for "data analysis at the extreme".   I've tried a lot of different things and done a lot of google searches  on this, and nothing seems to really be working.  I've included a  summary below.
  It now looks like an issue building **nvidia-331-uvm**, but I've included all relevant info below.  I've bolded the error.
  [HR][/HR]  **Ubuntu Version #:**
  chris@chris-G750JW:~$ lsb_release -a
  No LSB modules are available.
  Distributor ID: Ubuntu
  Description:    Ubuntu 14.04 LTS
  Release:    14.04
  Codename:   trusty
  --From what I've read, this version of Ubuntu is not "officially  supported" by NVidia because it's too new, but I've found a posting by  someone saying they got it to work.  If it's really needed, I'll  downgrade Ubuntu, but I'd have to think that leads to other problems (ie  security).
  **Graphics Card:**
  GeForce GTX 765M
  [HR][/HR]  I tried following the instructions at [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html) -- method 4
  ...when I was advised that it may be a graphics driver issue. Seeing the Noveau card seemed to be causing issues, I followed the  instructions on this web page to disable it.  When these didn't work, I  allowed the installer to create nvidia-installer-disable-nouveau.conf in  directory /etc/modprobe.d and then rebooted.  This got the graphics  driver to install finally, but it did not resolve the cuda installation  issues.
  [HR][/HR]  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **cuda**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
  The following information may help to resolve the situation:
  The following packages have unmet dependencies:
  cuda : Depends: cuda-6-0 (= 6.0-37) but it is not going to be installed
  E: Unable to correct problems, you have held broken packages.
  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **cuda-6-0**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
  The following information may help to resolve the situation:
  The following packages have unmet dependencies:
  cuda-6-0 : Depends: cuda-drivers (>= 331.00) but it is not going to be installed
  E: Unable to correct problems, you have held broken packages.
  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **cuda-drivers**
  Reading package lists... Done
  Building dependency tree     
  Reading state information... Done
  Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
  The following information may help to resolve the situation:
  The following packages have unmet dependencies:
  cuda-drivers : Depends: nvidia-persistenced (>= 331.62)
  E: Unable to correct problems, you have held broken packages.
  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **nvidia-persistenced**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  The following packages will be REMOVED:
  nvidia-331
  The following NEW packages will be installed:
  nvidia-persistenced
  0 upgraded, 1 newly installed, 1 to remove and 157 not upgraded.
  Need to get 0 B/21.8 kB of archives.
  After this operation, 182 MB disk space will be freed.
  Do you want to continue? [Y/n] Y
  (Reading database ... 189569 files and directories currently installed.)
  Removing nvidia-331 (331.67-0ubuntu1~xedgers14.04.2) ...
  Removing all DKMS Modules
  Done.
  update-alternatives: using /usr/lib/nvidia-331-prime/ld.so.conf to provide 
  /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
  update-alternatives: using /usr/lib/nvidia-331-prime/alt_ld.so.conf to provide 
  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
  update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide 
  /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
  INFO:Disable nvidia-331
  DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
  DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
  DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
  stop: Unknown instance: 
  update-initramfs: deferring update (trigger activated)
  Processing triggers for libc-bin (2.19-0ubuntu6) ...
  Processing triggers for man-db (2.6.7.1-1) ...
  Processing triggers for initramfs-tools (0.103ubuntu4) ...
  update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
  Selecting previously unselected package nvidia-persistenced.
  (Reading database ... 189351 files and directories currently installed.)
  Preparing to unpack .../nvidia-persistenced_331.62-0ubuntu1_amd64.deb ...
  Unpacking nvidia-persistenced (331.62-0ubuntu1) ...
  Processing triggers for ureadahead (0.100.0-16) ...
  Processing triggers for man-db (2.6.7.1-1) ...
  Setting up nvidia-persistenced (331.62-0ubuntu1) ...
  Configuration file '/etc/init/nvidia-persistenced.conf'
  ==> Deleted (by you or by a script) since installation.
  ==> Package distributor has shipped an updated version.
  What would you like to do about it ?  Your options are:
  Y or I  : install the package maintainer's version

N or O  : keep your currently-installed version

  D     : show the differences between the versions

  Z     : start a shell to examine the situation
  The default action is to keep your current version.
  *** nvidia-persistenced.conf (Y/I/N/O/D/Z) [default=N] ? Y
  Installing new version of config file /etc/init/nvidia-persistenced.conf ...
  Processing triggers for ureadahead (0.100.0-16) ...
  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **cuda-drivers**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Some packages could not be installed. This may mean that you have
  requested an impossible situation or if you are using the unstable
  distribution that some required packages have not yet been created
  or been moved out of Incoming.
  The following information may help to resolve the situation:
  The following packages have unmet dependencies:
  cuda-drivers : Depends: nvidia-331 (>= 331.62) but it is not going to be installed
              Depends: nvidia-331-uvm (>= 331.62) but it is not going to be installed

            Depends: nvidia-331-dev (>= 331.62) but it is not going to be installed
  E: Unable to correct problems, you have held broken packages.
  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **nvidia-331**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  Suggested packages:
  nvidia-331-uvm
  The following packages will be REMOVED:
  nvidia-persistenced
  The following NEW packages will be installed:
  nvidia-331
  0 upgraded, 1 newly installed, 1 to remove and 157 not upgraded.
  Need to get 0 B/36.5 MB of archives.
  After this operation, 182 MB of additional disk space will be used.
  Do you want to continue? [Y/n] Y
  (Reading database ... 189355 files and directories currently installed.)
  Removing nvidia-persistenced (331.62-0ubuntu1) ...
  Processing triggers for man-db (2.6.7.1-1) ...
  Selecting previously unselected package nvidia-331.
  (Reading database ... 189351 files and directories currently installed.)
  Preparing to unpack .../nvidia-331_331.67-0ubuntu1~xedgers14.04.2_amd64.deb ...
  Unpacking nvidia-331 (331.67-0ubuntu1~xedgers14.04.2) ...
  Processing triggers for ureadahead (0.100.0-16) ...
  Processing triggers for man-db (2.6.7.1-1) ...
  Setting up nvidia-331 (331.67-0ubuntu1~xedgers14.04.2) ...
  Configuration file '/etc/init/nvidia-persistenced.conf'
  ==> Deleted (by you or by a script) since installation.
  ==> Package distributor has shipped an updated version.
  What would you like to do about it ?  Your options are:
  Y or I  : install the package maintainer's version

N or O  : keep your currently-installed version

  D     : show the differences between the versions

  Z     : start a shell to examine the situation
  The default action is to keep your current version.
  *** nvidia-persistenced.conf (Y/I/N/O/D/Z) [default=N] ? Y
  Installing new version of config file /etc/init/nvidia-persistenced.conf ...
  update-alternatives: using /usr/lib/nvidia-331/ld.so.conf to provide /etc/ld.so.conf.d
  /x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
  update-alternatives: using /usr/lib/nvidia-331/alt_ld.so.conf to provide 
  /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
  update-alternatives: using /usr/share/nvidia-331/glamor.conf to provide /usr/share /X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
  update-initramfs: deferring update (trigger activated)
  INFO:Enable nvidia-331
  DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
  DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
  DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
  Loading new nvidia-331-331.67 DKMS files...
  Building only for 3.13.0-24-generic
  Building for architecture x86_64
  Building initial module for 3.13.0-24-generic
  Done.
  nvidia_331:
  Running module version sanity check.
  
[LIST]
[*]Original module
[LIST]
[*]No original module exists within this kernel 
[/LIST]
  
[*]Installation
[LIST]
[*]Installing to /lib/modules/3.13.0-24-generic/updates/dkms/ 
[/LIST]
   
[/LIST]
  depmod....
  DKMS: install completed.
  Processing triggers for ureadahead (0.100.0-16) ...
  Processing triggers for initramfs-tools (0.103ubuntu4) ...
  update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
  chris@chris-G750JW:/etc/modprobe.d$ sudo apt-get install **nvidia-331-uvm**
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  The following NEW packages will be installed:
  nvidia-331-uvm
  0 upgraded, 1 newly installed, 0 to remove and 157 not upgraded.
  Need to get 0 B/67.2 kB of archives.
  After this operation, 432 kB of additional disk space will be used.
  Selecting previously unselected package nvidia-331-uvm.
  (Reading database ... 189570 files and directories currently installed.)
  Preparing to unpack .../nvidia-331-uvm_331.67-0ubuntu1~xedgers14.04.2_amd64.deb ...
  Unpacking nvidia-331-uvm (331.67-0ubuntu1~xedgers14.04.2) ...
  Setting up nvidia-331-uvm (331.67-0ubuntu1~xedgers14.04.2) ...
  Loading new nvidia-331-uvm-331.67 DKMS files...
  First Installation: checking all kernels...
  Building only for 3.13.0-24-generic
  Building for architecture x86_64
  Building initial module for 3.13.0-24-generic
  **Error! Application of patch buildfix_kernel_3.12.patch  failed. Check /var/lib/dkms/nvidia-331-uvm/331.67/build/ for more  information.**
  chris@chris-G750JW:/var/lib/dkms/nvidia-331-uvm/331.67/build$ sudo apt-get install **nvidia-331-dev**
  Reading package lists... Done
  Building dependency tree  
  Reading state information... Done
  The following NEW packages will be installed:
  nvidia-331-dev
  0 upgraded, 1 newly installed, 0 to remove and 157 not upgraded.
  Need to get 0 B/8,594 B of archives.
  After this operation, 41.0 kB of additional disk space will be used.
  Selecting previously unselected package nvidia-331-dev.
  (Reading database ... 189610 files and directories currently installed.)
  Preparing to unpack .../nvidia-331-dev_331.67-0ubuntu1~xedgers14.04.2_amd64.deb ...
  Unpacking nvidia-331-dev (331.67-0ubuntu1~xedgers14.04.2) ...
  Setting up nvidia-331-dev (331.67-0ubuntu1~xedgers14.04.2) ...
  [HR][/HR]  **I checked out that directly cited in the error above but don't see any logs:**
  chris@chris-G750JW:/var/lib/dkms/nvidia-331-uvm/331.67/build$ ll -rt
  total 472
  -rw-r--r-- 1 root root  1566 May 16 02:23 ctrl2080mc.h
  drwxr-xr-x 3 root root  4096 May 16 02:23 ../
  -rw-r--r-- 1 root root  6339 May 16 02:23 uvmtypes.h
  -rw-r--r-- 1 root root  1568 May 16 02:23 uvm_linux_ioctl.h
  -rw-r--r-- 1 root root  7798 May 16 02:23 uvm_ioctl.h
  -rw-r--r-- 1 root root 12539 May 16 02:23 uvm.h
  -rw-r--r-- 1 root root  1752 May 16 02:23 uvm_gpu_ops_tests.h
  -rw-r--r-- 1 root root  8829 May 16 02:23 uvm_gpu_ops_tests.c
  -rw-r--r-- 1 root root 10759 May 16 02:23 uvm-debug.h
  drwxr-xr-x 2 root root  4096 May 16 02:23 patches/
  -rw-r--r-- 1 root root 21707 May 16 02:23 nvmisc.h
  -rw-r--r-- 1 root root  5808 May 16 02:23 nvkernel.h
  -rw-r--r-- 1 root root  1942 May 16 02:23 nvidia_uvm_utils.h
  -rw-r--r-- 1 root root  3140 May 16 02:23 nvidia_uvm_utils.c
  -rw-r--r-- 1 root root  4628 May 16 02:23 nvidia_uvm_page_cache.c
  -rw-r--r-- 1 root root 12752 May 16 02:23 nvidia_uvm_lite.h
  -rw-r--r-- 1 root root  2470 May 16 02:23 nvidia_uvm_lite_events.c
  -rw-r--r-- 1 root root  3627 May 16 02:23 nvidia_uvm_lite_counters.h
  -rw-r--r-- 1 root root 11205 May 16 02:23 nvidia_uvm_lite_counters.c
  -rw-r--r-- 1 root root 83268 May 16 02:23 nvidia_uvm_lite.c
  -rw-r--r-- 1 root root 14970 May 16 02:23 nvidia_uvm_lite_api.c
  -rw-r--r-- 1 root root 14670 May 16 02:23 nvidia_uvm_linux.h
  -rw-r--r-- 1 root root  2293 May 16 02:23 nvidia_uvm_linux.c
  -rw-r--r-- 1 root root  4576 May 16 02:23 nvidia_uvm_common.h
  -rw-r--r-- 1 root root  7855 May 16 02:23 nvidia_uvm_common.c
  -rw-r--r-- 1 root root  2419 May 16 02:23 nvidia_page_migration_kepler.h
  -rw-r--r-- 1 root root 11254 May 16 02:23 nvidia_page_migration_kepler.c
  -rw-r--r-- 1 root root  9585 May 16 02:23 nvidia_page_migration.h
  -rw-r--r-- 1 root root  2896 May 16 02:23 nvidia_page_migration.c
  -rw-r--r-- 1 root root  6867 May 16 02:23 Makefile
  -rw-r--r-- 1 root root   282 May 16 02:23 dkms.conf.fragment
  -rw-r--r-- 1 root root   551 May 16 02:23 dkms.conf
  -rwxr-xr-x 1 root root 78186 May 16 02:23 conftest.sh*
  -rw-r--r-- 1 root root 10386 May 16 02:23 cla0b5.h
  -rw-r--r-- 1 root root  1440 May 16 02:23 cla06fsubch.h
  -rw-r--r-- 1 root root  4534 May 16 02:23 cla06f.h
  -rw-r--r-- 1 root root   651 May 16 02:23 nvidia_uvm_linux.h.rej
  -rw-r--r-- 1 root root 14670 May 16 02:23 nvidia_uvm_linux.h.orig
  drwxr-xr-x 3 root root  4096 May 16 02:23 ./

---

