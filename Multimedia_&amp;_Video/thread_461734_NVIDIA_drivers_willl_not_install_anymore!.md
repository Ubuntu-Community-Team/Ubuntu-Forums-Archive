---
title: "NVIDIA drivers willl not install anymore!"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by edubbler on 2007-06-02
after my last dist-upgrade, X would no longer start. Last time this happened, it was a simple matter of reinstalling the nvidia drivers. 

I am using the nvidia driver package from nvidia (NVIDIA-Linux-x86-1.0-9755-pkg1.run) and not doing things the apt-get/module-assistant way. This time the drivers would not even install. I tried installing the older version (9746) also to no avail. 

I am able to get going using the native nv driver, but I want to get back to using the nvidia driver ASAP (for 3d,etc..).

The past few times I've installed the nvidia drivers, I've done so successfully by runnning:
NVIDIA-Linux-x86-1.0-9755-pkg1.run --x-module-path=`X -showDefaultModulePath 2>&1 | cut -d, -f1` --x-library-path=`X -showDefaultLibPath 2>&1`

I have some  questions regarding the following excerpts from /var/log/nvidia-installer.llog

First:
> WARNING: Unable to restore symbolic link /usr/lib/libGL.so.1 -> libGL.so.1.2
         (File exists).

when the install fails, both the file and the symbolic link disappear. They exist prior to the driver install attempt as part of the libgl1-mesa-glx package. Without this, several programs will not run and I end up having to reinstall that package.

Also, There are several message similar to this one:
> ERROR: Unable to create
       '/usr/lib/dosemu/drive_z/tmp/selfgz5620/NVIDIA-Linux-x86-1.0-9746-pkg1/u
       sr/lib/libGL.la' for copying (No such file or directory)

/usr/lib/dosemu/drive_z/tmp is a symlink to /tmp. I verified that /tmp is writeable. 

Any ideas?

---

