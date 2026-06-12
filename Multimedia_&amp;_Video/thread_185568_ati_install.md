---
title: "ati install"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by majkmil on 2006-05-31
I am trying to install the 8.25.18 proprietary drivers. I am getting an error when installing this deb package. Does anyone know what the error means and what I can do to fix this? All the other packages installed OK.

mark@ubuntu:~/ati$ sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
(Reading database ... 135853 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.24.8-1 (using xorg-driver-fglrx_8.25.18-1_i386.deb) ...
Removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/share/fglrx/diversions/libGL.so.1.2', not allowed
dpkg: error processing xorg-driver-fglrx_8.25.18-1_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx_8.25.18-1_i386.deb

Thanks

---

### Post by majkmil on 2006-06-01
Please

---

### Post by majkmil on 2006-06-01
PLease

---

### Post by cillian on 2006-06-11
If it's any consolation I'm getting a similar issue after installing the nvidia drivers with apt-get then trying to uninstall the previous drivers with nvidia-installer --uninstall and then uninstalling nvidia-glx gives the following 

error:
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

I think this issue was resolved by running the update manager, it seemed to stall for a while and then somehow removed the offending package. Error gone.

---

