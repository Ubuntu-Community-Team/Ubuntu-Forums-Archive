---
title: "Kernel panic when compiling Nvidia driver (using XEN-kernel)"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by jschneider on 2006-12-24
Hi,

I installed the xen-kernel. The kernel seems to work ok (sometimes the keyboard does not work). But now I tried to install the binary NVidia driver.
I followed the guide: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2_2)
But when I enter the command:

 sudo ./nvidia-installer -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/xen-headers-2.6.17-6-generic-xen0

I just get a kernel panic. 

Compiling the kernel using the default kernel works fine.

---

