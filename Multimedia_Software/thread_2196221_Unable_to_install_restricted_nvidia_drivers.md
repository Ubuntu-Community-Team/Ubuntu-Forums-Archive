---
title: "Unable to install restricted nvidia drivers"
date: 2013-12-28
forum: Multimedia Software
---

### Post by fabian-hernalsteen on 2013-12-28
Hello,

I am running into some problems after an upgrade from 12.04 to 13.10.
I upgraded step by step and everything kept working, until i got to version 13.10. After a lot of searching, i discovered that the latest kernel does not boot for some reason (something about isapnp if i remember well). Instead of fixing the problem, i went for the quick solution: I added "GRUB_DEFAULT=saved" and "GRUB_SAVEDEFAULT=true" to /etc/default/grub and simply selected an older kernel 
```

$ uname -r
3.8.0-34-generic

```

At this point, i was able to boot into my ubuntu box (no big problems so far)

In the restricted drivers, i selected the nvidia-319 instead of the actual 304 as 319 said it had been tested. When i rebooted my machine, all i got was a black screen. 

I removed the nvidia packages and rebooted. The GUI was working again but without hardware acceleration, which causes a huge audio delay in XBMC

I reinstalled the 304 package (like it was before), rebooted and got a black screen again.
After some searching, it seems that the package is built during installation, which means that the headers are needed. :
```


Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.11.0-14-generic
Done.


```

This is where the second problem comes in: the headers can not be installed for some reason for the kernel i am running
```

$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-3.8.0-34-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-3.8.0-34-generic' has no installation candidate

```



The 2 solutions I see are obvious (make the new kernel work or be able to install the old headers), but I have no idea how i can do this. 
Does anyone have a hint? In case you would need anything (logfiles, screenshots, ...), please let me know

Thanks!!!

---

### Post by SeijiSensei on 2013-12-28
How are you installing the driver?  Usually if you use "sudo apt-get install nvidia-common" it will bring in all the dependencies you need including dkms, compilers, and header files.  I did this just yesterday on an older netbook with the NVIDIA Ion platform after installing Lubuntu 13.10.

---

### Post by fabian-hernalsteen on 2013-12-28
Hello SeijiSensei,

Thanks for your quick reply. I just redid the installation and copy pasted the output below:


```

mediacenter@mediacenter:~$ dpkg -l "*nvidia*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-=============================================================
un  libgl1-nvidia-alternatives   <none>                                  (no description available)
rc  nvidia-304                   304.88-0ubuntu8     i386                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-304-updates           304.108-0ubuntu1    i386                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-319                   319.32-0ubuntu7     i386                NVIDIA binary Xorg driver, kernel module and VDPAU library
un  nvidia-common                <none>                                  (no description available)
un  nvidia-driver-binary         <none>                                  (no description available)
un  nvidia-persistenced          <none>                                  (no description available)
rc  nvidia-settings-304          304.88-0ubuntu2     i386                Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-304-updates  304.88-0ubuntu2     i386                Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-319          319.32-0ubuntu3     i386                Tool for configuring the NVIDIA graphics driver
un  nvidia-settings-binary       <none>                                  (no description available)
un  nvidia-vdpau-driver          <none>                                  (no description available)


mediacenter@mediacenter:~$ sudo apt-get install nvidia-common 
[sudo] password for mediacenter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglew1.6 libhal-storage1 libhal1 libmicrohttpd5 screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,236 B of archives.
After this operation, 37.9 kB of additional disk space will be used.
Get:1 http://be.archive.ubuntu.com/ubuntu/ saucy/universe nvidia-common i386 1:0.2.83 [1,236 B]
Fetched 1,236 B in 0s (14.9 kB/s)        
Selecting previously unselected package nvidia-common.
(Reading database ... 203803 files and directories currently installed.)
Unpacking nvidia-common (from .../nvidia-common_1%3a0.2.83_i386.deb) ...
Setting up nvidia-common (1:0.2.83) ...


mediacenter@mediacenter:~$ dpkg -l "*nvidia*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                         Version             Architecture        Description
+++-============================-===================-===================-=============================================================
un  libgl1-nvidia-alternatives   <none>                                  (no description available)
rc  nvidia-304                   304.88-0ubuntu8     i386                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-304-updates           304.108-0ubuntu1    i386                NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-319                   319.32-0ubuntu7     i386                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                1:0.2.83            i386                transitional package for ubuntu-drivers-common
un  nvidia-driver-binary         <none>                                  (no description available)
un  nvidia-persistenced          <none>                                  (no description available)
rc  nvidia-settings-304          304.88-0ubuntu2     i386                Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-304-updates  304.88-0ubuntu2     i386                Tool for configuring the NVIDIA graphics driver
rc  nvidia-settings-319          319.32-0ubuntu3     i386                Tool for configuring the NVIDIA graphics driver
un  nvidia-settings-binary       <none>                                  (no description available)
un  nvidia-vdpau-driver          <none>                                  (no description available)





mediacenter@mediacenter:~$ sudo apt-get install nvidia-319
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglew1.6 libhal-storage1 libhal1 libmicrohttpd5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-settings-319
Recommended packages:
  nvidia-persistenced
The following NEW packages will be installed:
  nvidia-319 nvidia-settings-319
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/40.7 MB of archives.
After this operation, 116 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously unselected package nvidia-319.
(Reading database ... 203806 files and directories currently installed.)
Unpacking nvidia-319 (from .../nvidia-319_319.32-0ubuntu7_i386.deb) ...
Selecting previously unselected package nvidia-settings-319.
Unpacking nvidia-settings-319 (from .../nvidia-settings-319_319.32-0ubuntu3_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Processing triggers for man-db ...
Setting up nvidia-319 (319.32-0ubuntu7) ...
update-alternatives: using /usr/lib/nvidia-319/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: warning: skip creation of /usr/lib/XvMCConfig because associated file /usr/lib/nvidia-319/XvMCConfig (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-319/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-319/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-319/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: using /usr/lib/nvidia-319/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.8.0-34-generic
INFO:Enable nvidia-319
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-319-319.32 DKMS files...
Building for 3.8.0-34-generic and 3.11.0-14-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 3.11.0-14-generic
Done.

nvidia_319:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.11.0-14-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-settings-319 (319.32-0ubuntu3) ...
update-alternatives: warning: alternative /usr/lib/nvidia-settings-304/ld.so.conf (part of link group nvidia_settings_conf) doesn't exist; removing from list of alternatives
update-alternatives: warning: /etc/alternatives/nvidia_settings_conf is dangling; it will be updated with best choice
update-alternatives: using /usr/lib/nvidia-settings-319/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-14-generic



```

---

### Post by SeijiSensei on 2013-12-29
I apologize.  The correct package is named "nvidia-current" not "nvidia-common".  There is an nvidia-common as well, of course.

---

### Post by Bucky Ball on 2013-12-29
*Thread moved to **Multimedia & Video**.*

---

### Post by fabian-hernalsteen on 2013-12-30
I tried the same with nvidia-current, no difference :(

---

### Post by Yellow Pasque on 2013-12-30
> **fabian-hernalsteen said:**
> This is where the second problem comes in: the headers can not be installed for some reason for the kernel i am running

The 3.8.x kernel is from Ubuntu 13.04/Raring. You need to boot into the correct kernel for Ubuntu 13.10/Saucy (3.11.x kernel) and get rid of the old kernels..

---

### Post by fabian-hernalsteen on 2013-12-30
With this kernel, nothing works...
Not sure what i can do to debug this as i can not log in to the console to check logs. Any idea what i can do?

---

### Post by fabian-hernalsteen on 2014-01-05
The nvidia part is "solved", i will open a new thread for the kernel problem

---

### Post by Bucky Ball on 2014-01-05
It would be good if you could share with the community what you did to fix it. Thanks. ;)

---

