---
title: "problem with mesa driver"
date: 2011-05-03
forum: Multimedia Software
---

### Post by valj on 2011-05-03
Hello all,

After I updated Ubuntu to version 10.04, I had a problem with my ATI card like many other people. I had read on internet that my card wasn't supported anymore, and since I needed to run some OpenGL applications I finally switched to Mesa. I read many contradictory things online so I'm not pretty sure I installed it correctly (glxgears seems to work though).

When I run wg (the OpenGL display application for the [http://www.cimms.ou.edu/~lakshman/WDSS2/index.shtml]("http://www.cimms.ou.edu/~lakshman/WDSS2/index.shtml") software), I get the following error, suggesting that my install may have not been correctly done.

> WDSS-II (c) 2001-2010 University of Oklahoma. All rights reserved. See [http://www.wdssii.org/](http://www.wdssii.org/)
Segmentation Fault.
crawl: Input/output error
Error tracing through process 2124

2124: wg
(No symbols found in )
(No symbols found in /usr/lib/mesa/libGL.so.1)
(No symbols found in /usr/lib/libGLU.so.1)
(No symbols found in /usr/lib/libfreetype.so.6)
(No symbols found in /lib/libbz2.so.1)
(No symbols found in /lib/libz.so.1)
(No symbols found in /usr/lib/libgtkglext-x11-1.0.so.0)
(No symbols found in /usr/lib/libgdkglext-x11-1.0.so.0)
(No symbols found in /usr/lib/libXmu.so.6)
(No symbols found in /usr/lib/libXt.so.6)
(No symbols found in /usr/lib/libSM.so.6)
(No symbols found in /usr/lib/libICE.so.6)
(No symbols found in /usr/lib/libgtk-x11-2.0.so.0)
(No symbols found in /usr/lib/libgdk-x11-2.0.so.0)
(No symbols found in /usr/lib/libatk-1.0.so.0)
(No symbols found in /usr/lib/libgdk_pixbuf-2.0.so.0)
(No symbols found in /usr/lib/libpangocairo-1.0.so.0)
(No symbols found in /usr/lib/libpango-1.0.so.0)
(No symbols found in /usr/lib/libcairo.so.2)
(No symbols found in /usr/lib/libgmodule-2.0.so.0)
(No symbols found in /usr/lib/libgthread-2.0.so.0)
(No symbols found in /usr/lib/libgobject-2.0.so.0)
(No symbols found in /lib/libglib-2.0.so.0)
(No symbols found in /usr/lib/libcurl.so.3)
(No symbols found in /lib/tls/i686/cmov/libdl.so.2)
(No symbols found in /usr/lib/libstdc++.so.6)
(No symbols found in /lib/tls/i686/cmov/libm.so.6)
(No symbols found in /lib/libgcc_s.so.1)
(No symbols found in /lib/tls/i686/cmov/libc.so.6)
(No symbols found in /usr/lib/libX11.so.6)
(No symbols found in /usr/lib/libXext.so.6)
(No symbols found in /usr/lib/libXxf86vm.so.1)
(No symbols found in /usr/lib/libXdamage.so.1)
(No symbols found in /usr/lib/libXfixes.so.3)
(No symbols found in /lib/libdrm.so.2)
(No symbols found in /usr/lib/libpangox-1.0.so.0)
(No symbols found in /usr/lib/libpangoft2-1.0.so.0)
(No symbols found in /usr/lib/libgio-2.0.so.0)
(No symbols found in /usr/lib/libfontconfig.so.1)
(No symbols found in /lib/libuuid.so.1)
(No symbols found in /usr/lib/libXrender.so.1)
(No symbols found in /usr/lib/libXinerama.so.1)
(No symbols found in /usr/lib/libXi.so.6)
(No symbols found in /usr/lib/libXrandr.so.2)
(No symbols found in /usr/lib/libXcursor.so.1)
(No symbols found in /usr/lib/libXcomposite.so.1)
(No symbols found in /lib/tls/i686/cmov/librt.so.1)
(No symbols found in /usr/lib/libpixman-1.so.0)
(No symbols found in /usr/lib/libdirectfb-1.2.so.0)
(No symbols found in /usr/lib/libfusion-1.2.so.0)
(No symbols found in /usr/lib/libdirect-1.2.so.0)
(No symbols found in /lib/libpng12.so.0)
(No symbols found in /usr/lib/libxcb-render-util.so.0)
(No symbols found in /usr/lib/libxcb-render.so.0)
(No symbols found in /usr/lib/libxcb.so.1)
(No symbols found in /lib/libpcre.so.3)
(No symbols found in /usr/lib/libidn.so.11)
(No symbols found in /usr/lib/liblber-2.4.so.2)
(No symbols found in /usr/lib/libldap_r-2.4.so.2)
(No symbols found in /usr/lib/libgssapi_krb5.so.2)
(No symbols found in /lib/i686/cmov/libssl.so.0.9.8)
(No symbols found in /lib/i686/cmov/libcrypto.so.0.9.8)
(No symbols found in /lib/ld-linux.so.2)
(No symbols found in /lib/tls/i686/cmov/libresolv.so.2)
(No symbols found in /lib/libselinux.so.1)
(No symbols found in /lib/libexpat.so.1)
(No symbols found in /usr/lib/libXau.so.6)
(No symbols found in /usr/lib/libXdmcp.so.6)
(No symbols found in /usr/lib/libsasl2.so.2)
(No symbols found in /usr/lib/libgnutls.so.26)
(No symbols found in /usr/lib/libkrb5.so.3)
(No symbols found in /usr/lib/libk5crypto.so.3)
(No symbols found in /lib/libcom_err.so.2)
(No symbols found in /usr/lib/libkrb5support.so.0)
(No symbols found in /lib/libkeyutils.so.1)
(No symbols found in /usr/lib/libtasn1.so.3)
(No symbols found in /lib/libgcrypt.so.11)
(No symbols found in /lib/libgpg-error.so.0)
(No symbols found in /lib/tls/i686/cmov/libnss_compat.so.2)
(No symbols found in /lib/tls/i686/cmov/libnsl.so.1)
(No symbols found in /lib/tls/i686/cmov/libnss_nis.so.2)
(No symbols found in /lib/tls/i686/cmov/libnss_files.so.2)
(No symbols found in /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so)
(No symbols found in /usr/lib/libcanberra-gtk.so.0)
(No symbols found in /usr/lib/libcanberra.so.0)
(No symbols found in /usr/lib/libvorbisfile.so.3)
(No symbols found in /usr/lib/libvorbis.so.0)
(No symbols found in /usr/lib/libogg.so.0)
(No symbols found in /usr/lib/libtdb.so.1)
(No symbols found in /usr/lib/libltdl.so.7)
(No symbols found in /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so)
(No symbols found in /usr/lib/dri/swrast_dri.so)
0x00c5e422: _fini + 0x7f82eAborting WDSS-II program. Stack trace printed.
Aborted

I have no way to check the source code, and I didn't get much help on the WDSSII forum. That's why I'm here. Anyone has an idea how to fix this?

thanks

---

### Post by advection on 2011-05-08
I had the same problem trying to install WDSS-II. I was able to get it to work by installing mesa with```
sudo apt-get install libgl1-mesa-swx11

```

---

### Post by valj on 2011-06-09
Thanks a lot! Problem fixed.

---

### Post by Yellow Pasque on 2011-06-10
> **valj said:**
> Thanks a lot! Problem fixed.
You probably didn't remove fglrx/Catalyst driver properly. Note that libgl1-mesa-swx11 is not hardware-accelerated like libgl1-mesa-glx.
I suggest you do these 6 commands: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

