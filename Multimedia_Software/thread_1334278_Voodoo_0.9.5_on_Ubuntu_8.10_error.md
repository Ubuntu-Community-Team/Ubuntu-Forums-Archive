---
title: "Voodoo 0.9.5 on Ubuntu 8.10 error"
date: 2009-11-22
forum: Multimedia Software
---

### Post by stoneage on 2009-11-22
Hi everyone.

I am trying to run Voodoo 0.9.5 on Ubuntu 8.10 64 bit. I have what is probably a paths error, but I don't know how to fix it.

The error:-
> organic@organic-desktop:~/applications/voodoo-x86Linux-0.9.5$ bin/voodoobin/voodoo: error while loading shared libraries: libQtOpenGL.so.4: cannot open shared object file: No such file or directory

Also:-
> organic@organic-desktop:~/applications/voodoo-x86Linux-0.9.5$ ldd bin/voodoo
	linux-gate.so.1 =>  (0xf7f0c000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ed4000)
	libQtGui.so.4 => /usr/lib32/libQtGui.so.4 (0xf75d1000)
	libQtCore.so.4 => /usr/lib32/libQtCore.so.4 (0xf73a2000)
	[COLOR="Blue"]libQtOpenGL.so.4 => not found
	libQt3Support.so.4 => not found
	libQtSql.so.4 => not found[/COLOR]
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf72b3000)
	libm.so.6 => /lib32/libm.so.6 (0xf728c000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf727d000)
	libc.so.6 => /lib32/libc.so.6 (0xf711f000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf70ae000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf6ff4000)
	/lib/ld-linux.so.2 (0xf7f0d000)
	libaudio.so.2 => /usr/lib32/libaudio.so.2 (0xf6fdc000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6fb5000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6fac000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6f94000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6f7e000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf6ec7000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6ebd000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6eb2000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6eab000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6e35000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6e08000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6df9000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6d0a000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf6d03000)
	librt.so.1 => /lib32/librt.so.1 (0xf6cfa000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6cf6000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf5e8e000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf5e8c000)
	libXt.so.6 => /usr/lib32/libXt.so.6 (0xf5e3a000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf5e10000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf5de9000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf5de6000)
	libxcb-xlib.so.0 => /usr/lib32/libxcb-xlib.so.0 (0xf5de3000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf5dc9000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf5dc4000)

I have the libs that were not found installed in /usr/lib Perhaps voodoo is looking in /usr/lib32 ?

The missing libs are also included in voodoo-x86Linux-0.9.5/bin

Voodoo Installation:-
[http://www.digilab.uni-hannover.de/download.html](http://www.digilab.uni-hannover.de/download.html)

---

