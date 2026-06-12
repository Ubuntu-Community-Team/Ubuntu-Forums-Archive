---
title: "MediaExpress: symbol lookup error"
date: 2010-04-01
forum: Multimedia Software
---

### Post by prule on 2010-04-01
Hi, can anyone help me debug this problem?

Running MediaExpress ([http://www.blackmagic-design.com/downloads/software_readme/Media_Express_Linux_2.0.3.txt](http://www.blackmagic-design.com/downloads/software_readme/Media_Express_Linux_2.0.3.txt)) from the command line shows this error:
> 
paul@paul-laptop:~$ MediaExpress 
MediaExpress: symbol lookup error: /usr/lib/libQtSvg.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

ldd shows:

> paul@paul-laptop:~$ ldd /usr/bin/MediaExpress
	linux-gate.so.1 =>  (0x00d46000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00fb2000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x008f2000)
	libQtCore.so.4 => /usr/lib/blackmagic/libQtCore.so.4 (0x0021b000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x00ed4000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00516000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00f6f000)
	libQtGui.so.4 => /usr/lib/blackmagic/libQtGui.so.4 (0x00fb6000)
	libQtSvg.so.4 => /usr/lib/libQtSvg.so.4 (0x00110000)
	libGLU.so.1 => /usr/lib/libGLU.so.1 (0x00163000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00499000)
	libQtOpenGL.so.4 => /usr/lib/blackmagic/libQtOpenGL.so.4 (0x00645000)
	libQtSingleApplication.so => /usr/lib/blackmagic/libQtSingleApplication.so (0x001d3000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00e05000)
	libQtNetwork.so.4 => /usr/lib/blackmagic/libQtNetwork.so.4 (0x007bc000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x0096a000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x001e0000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00a5c000)
	libz.so.1 => /lib/libz.so.1 (0x001fe000)
	/lib/ld-linux.so.2 (0x00787000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x0045c000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00f60000)
	libglib-2.0.so.0 => /lib/libglib-2.0.so.0 (0x00ba1000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00db1000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x0091c000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00462000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x006d2000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00487000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00751000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x004fd000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00920000)
	libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0x00490000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00216000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00507000)
	libdrm.so.2 => /usr/lib/libdrm.so.2 (0x0076c000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00c58000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x0050d000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00776000)
	libexpat.so.1 => /lib/libexpat.so.1 (0x00c89000)

> paul@paul-laptop:~$ ls -al /usr/lib/blackmagic/
total 14392
drwxr-xr-x   2 root root     4096 2010-04-01 14:11 .
drwxr-xr-x 269 root root    81920 2010-04-01 14:52 ..
-r-xr--r--   1 root root     1959 2010-02-22 17:24 blackmagic-loader
-rwxr-xr-x   1 root root   238432 2010-02-22 17:25 BlackmagicPreferencesStartup
-r-xr--r--   1 root root     3548 2010-02-22 17:24 blackmagic-setup
lrwxrwxrwx   1 root root       18 2010-04-01 14:09 libQtCore.so -> libQtCore.so.4.5.0
lrwxrwxrwx   1 root root       18 2010-04-01 14:09 libQtCore.so.4 -> libQtCore.so.4.5.0
lrwxrwxrwx   1 root root       18 2010-04-01 14:09 libQtCore.so.4.5 -> libQtCore.so.4.5.0
-rw-r--r--   1 root root  2361096 2009-09-01 10:04 libQtCore.so.4.5.0
lrwxrwxrwx   1 root root       17 2010-04-01 14:09 libQtGui.so -> libQtGui.so.4.5.0
lrwxrwxrwx   1 root root       17 2010-04-01 14:09 libQtGui.so.4 -> libQtGui.so.4.5.0
lrwxrwxrwx   1 root root       17 2010-04-01 14:09 libQtGui.so.4.5 -> libQtGui.so.4.5.0
-rw-r--r--   1 root root 10231388 2009-09-01 10:04 libQtGui.so.4.5.0
lrwxrwxrwx   1 root root       21 2010-04-01 14:09 libQtNetwork.so -> libQtNetwork.so.4.5.0
lrwxrwxrwx   1 root root       21 2010-04-01 14:09 libQtNetwork.so.4 -> libQtNetwork.so.4.5.0
lrwxrwxrwx   1 root root       21 2010-04-01 14:09 libQtNetwork.so.4.5 -> libQtNetwork.so.4.5.0
-rw-r--r--   1 root root  1158792 2009-09-01 10:04 libQtNetwork.so.4.5.0
lrwxrwxrwx   1 root root       20 2010-04-01 14:09 libQtOpenGL.so -> libQtOpenGL.so.4.5.0
lrwxrwxrwx   1 root root       20 2010-04-01 14:09 libQtOpenGL.so.4 -> libQtOpenGL.so.4.5.0
lrwxrwxrwx   1 root root       20 2010-04-01 14:09 libQtOpenGL.so.4.5 -> libQtOpenGL.so.4.5.0
-rw-r--r--   1 root root   573828 2009-09-01 10:04 libQtOpenGL.so.4.5.0
-rw-r--r--   1 root root    62227 2010-03-10 10:27 libQtSingleApplication.so

> paul@paul-laptop:~$ ls -al /usr/lib/libQtSvg*
-rw-r--r-- 1 root root    591 2009-10-15 08:30 /usr/lib/libQtSvg.prl
lrwxrwxrwx 1 root root     17 2010-04-01 14:52 /usr/lib/libQtSvg.so -> libQtSvg.so.4.5.2
lrwxrwxrwx 1 root root     17 2010-04-01 14:44 /usr/lib/libQtSvg.so.4 -> libQtSvg.so.4.5.2
lrwxrwxrwx 1 root root     17 2009-11-03 22:26 /usr/lib/libQtSvg.so.4.5 -> libQtSvg.so.4.5.2
-rw-r--r-- 1 root root 338864 2009-10-15 08:34 /usr/lib/libQtSvg.so.4.5.2

Is this a packaging problem with MediaExpress, or a problem with QT on my system (Ubuntu 9.10).

Thanks.

[update] just tried on Kbuntu 9.10, and had the same problem.

---

### Post by nickp on 2010-04-27
Hi,

I had the same problem for a while.

The solution is to download the latest Decklink drivers (7.6) from the website, install these, and then the version of MediaExpress that comes with the Decklink drivers.

Everything should then work fine.

Cheers,
Nick

---

