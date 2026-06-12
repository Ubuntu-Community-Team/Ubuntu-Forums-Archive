---
title: "namespace compilation error"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by babu_neelam on 2009-03-11
Hi,

I would like to build an image with network namespaces support enabled. I am using ubuntu version 8.10.

So I followed the steps in [http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/](http://beginlinux.wordpress.com/2008/12/03/how-to-compile-an-ubuntu-810-kernel/)
to download the source.

And in make menuconfig, I have enabled network namespace related options as explained in "INstallation" section at [http://lxc.sourceforge.net/network/configuration.php](http://lxc.sourceforge.net/network/configuration.php), following errors are observed:


When "fakeroot make-kpkg - -initrd - -append-to-version=-mw1 kernel_image kernel_headers" command is issued,   CC [M]  ubuntu/aufs/opts.o
  CC [M]  ubuntu/aufs/wkq.o
  CC [M]  ubuntu/aufs/vfsub.o
ubuntu/aufs/vfsub.c: In function &#8216;do_vfsub_mknod&#8217;:
ubuntu/aufs/vfsub.c:166: warning: passing argument 3 of &#8216;vfs_mknod&#8217; makes pointer from integer without a cast
ubuntu/aufs/vfsub.c:166: error: too few arguments to function &#8216;vfs_mknod&#8217;
ubuntu/aufs/vfsub.c: In function &#8216;do_vfsub_link&#8217;:
ubuntu/aufs/vfsub.c:191: warning: passing argument 2 of &#8216;vfs_link&#8217; from incompatible pointer type
ubuntu/aufs/vfsub.c:191: warning: passing argument 3 of &#8216;vfs_link&#8217; from incompatible pointer type
ubuntu/aufs/vfsub.c:191: error: too few arguments to function &#8216;vfs_link&#8217;
ubuntu/aufs/vfsub.c: In function &#8216;do_vfsub_rename&#8217;:
ubuntu/aufs/vfsub.c:222: warning: passing argument 3 of &#8216;vfs_rename&#8217; from incompatible pointer type
ubuntu/aufs/vfsub.c:222: warning: passing argument 4 of &#8216;vfs_rename&#8217; from incompatible pointer type
ubuntu/aufs/vfsub.c:222: error: too few arguments to function &#8216;vfs_rename&#8217;
ubuntu/aufs/vfsub.c: In function &#8216;do_vfsub_mkdir&#8217;:
ubuntu/aufs/vfsub.c:246: warning: passing argument 3 of &#8216;vfs_mkdir&#8217; makes pointer from integer without a castubuntu/aufs/vfsub.c:246: error: too few arguments to function &#8216;vfs_mkdir&#8217;
ubuntu/aufs/vfsub.c: In function &#8216;do_vfsub_rmdir&#8217;:
ubuntu/aufs/vfsub.c:268: error: too few arguments to function &#8216;vfs_rmdir&#8217;
ubuntu/aufs/vfsub.c: In function &#8216;do_vfsub_unlink&#8217;:
ubuntu/aufs/vfsub.c:290: error: too few arguments to function &#8216;vfs_unlink&#8217;
make[3]: *** [ubuntu/aufs/vfsub.o] Error 1
make[2]: *** [ubuntu/aufs] Error 2
make[1]: *** [ubuntu] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [debian/stamp-build-kernel] Error 2
root@user-desktop:/usr/src/linux#



Please let know how to overcome these errors.


Thanks,
Babu

---

### Post by babu_neelam on 2009-03-14
I made changes to get through these compilation errors by passing dummy arguments to the functions appeared in compilation errors.

After that, I am observing some linking issues:

  LD [M]  lib/zlib_deflate/zlib_deflate.o
  Building modules, stage 2.
  MODPOST 2268 modules
ERROR: "dlm_posix_lock" [ubuntu/gfs/gfs.ko] undefined!
ERROR: "dlm_lock" [ubuntu/gfs/gfs.ko] undefined!
ERROR: "dlm_posix_get" [ubuntu/gfs/gfs.ko] undefined!
ERROR: "dlm_posix_unlock" [ubuntu/gfs/gfs.ko] undefined!
ERROR: "dlm_release_lockspace" [ubuntu/gfs/gfs.ko] undefined!
ERROR: "dlm_unlock" [ubuntu/gfs/gfs.ko] undefined!
ERROR: "dlm_new_lockspace" [ubuntu/gfs/gfs.ko] undefined!
WARNING: modpost: Found 12 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [debian/stamp-build-kernel] Error 2
root@user-desktop:/usr/src/linux# 


Does anyone know how to overcome these linking errors ?


Thanks,
Babu

---

