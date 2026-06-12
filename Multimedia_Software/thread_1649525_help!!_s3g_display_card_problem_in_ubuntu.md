---
title: "help!! s3g display card problem in ubuntu"
date: 2010-12-20
forum: Multimedia Software
---

### Post by mengmeng on 2010-12-20
Hi, I am a absolutely beginner for linux. I have a Fujitsu laptop with S3G 9045 display card. just installed ubuntu 10.10, but the resolution cann't be higher than 800*600, and the xorg.conf is empty. 
I went to the S3 Graphics webpage and downloaded my driver, followed the instruction here (skiped step 1.3) [http://drivers.s3graphics.com/en/download/drivers/chrome4x-Linux/Readme.txt](http://drivers.s3graphics.com/en/download/drivers/chrome4x-Linux/Readme.txt) 

when I installed the driver, it showed, 

 mengmeng@uranus:~/Downloads/S3G-InstallPkg-i386$ sudo ./install.sh
[sudo] password for mengmeng: 
Package vdpau was not found in the pkg-config search path.
Perhaps you should add the directory containing `vdpau.pc'
to the PKG_CONFIG_PATH environment variable
No package 'vdpau' found
Installing/Uninstalling S3G Linux driver built on Xorg 7.3 
Cannot find pre-build S3G kernel driver for kernel 2.6.35-24-generic-pae
Found 01:00.0 VGA compatible controller: S3 Inc. Device 9045 (rev 01) on your system.
Backup /usr/lib/xorg/modules/extensions/libglx.so sucessfully.
cp: cannot stat `/etc/X11/xorg.conf': No such file or directory
Backup /etc/X11/xorg.conf sucessfully.
Install s3g_drv.so sucessfully.
Install libglx.so sucessfully.
Install libGL.so.1.2 sucessfully.
Install s3g_dri.so sucessfully.
Install libva.so.0.28.0 sucessfully
Install s3g_drv_video.so sucessfully.
Error Install libvdpau_s3g.so.1!!! Required Package libvdpau.
Install S3DApp.cfg sucessfully.
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
[I]Begin building kernel modules
*.o
*.ko
.depend
.*.flags
.*.d
.*.cmd
*.mod.c
linux
.tmp_versions
*~
Module.*
rm -f linux
ln -s . linux
make -C /lib/modules/2.6.35-24-generic-pae/build  SUBDIRS=`pwd` S3GSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic-pae'
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_bufs.o
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_context.o
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.o
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c: In function ‘s3g_get_busid’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c:196: warning: statement with no effect
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c: In function ‘s3g_ioctl_get_display_info’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fops.c:233: warning: unused variable ‘found’
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_lock.o
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.o
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:37: warning: missing braces around initializer
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:37: warning: (near initialization for ‘s3g_servers[0]’)
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c: In function ‘fill_in_dev’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:45: warning: unused variable ‘romaddr’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:44: warning: unused variable ‘romsave2’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_kedrv.c:43: warning: unused variable ‘romsave’
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fb.o
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fb.c: In function ‘s3gfb_create’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fb.c:404: warning: unused variable ‘i’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fb.c: At top level:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fb.c:105: warning: ‘s3gfb_setcmap’ defined but not used
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_fb.c:362: warning: ‘s3gfb_rotate’ defined but not used
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_swfb.o
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_swfb.c: In function ‘s3g_swfb_create’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_swfb.c:8: warning: unused variable ‘ret’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_swfb.c: In function ‘s3g_swfb_probe’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/../common/s3g_swfb.c:65: warning: unused variable ‘entity’
  CC [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.o
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c: In function ‘s3g_mem_track_remove’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c:765: warning: left-hand operand of comma expression has no effect
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c:765: warning: statement with no effect
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c: In function ‘s3g_mem_leak_list’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c:791: warning: unused variable ‘fp’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c: In function ‘__s3gke_set_cached_vmalloc’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c:956: warning: unused variable ‘prot’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c: In function ‘__s3gke_set_nocached_vmalloc’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c:972: warning: unused variable ‘prot’
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c: In function ‘get_power’:
/home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3gkeapi.c:1144: warning: statement with no effect
  LD [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3g.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/.libS3G.a.GCC4.cmd for /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/libS3G.a.GCC4
  CC      /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3g.mod.o
  LD [M]  /home/mengmeng/Downloads/S3G-InstallPkg-i386/s3gdrm/s3g/s3g.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic-pae'
[I]End building kernel modules
Install s3g.ko sucessfully.


I guess the warning of lacking of vdpau could be the problem but not sure, and I don't know how to solve this either.

when I reboot the computer, it could only have tty login then. when I did startx, it complained that failed to have s3g driver, and no screen found

I could only delete the xorg.conf to get back to the GUI, but the resolution remains bad

what should I do for that? I really want to install the driver properly and solve this problem.

thanks in advance!:P

---

### Post by vykuntamsrinivas on 2012-06-19
hi,i too have same problem s3g driver was not installed properly,after tty login  i didnt get desktop instead its giving me the error xinit: no such file or directory(can not connect to x server).....i think u are able to see the desktop but i left with that terminal   tried to reinstall xorg but it didn work ... can you please explain how to get my desktop back.....^^

---

