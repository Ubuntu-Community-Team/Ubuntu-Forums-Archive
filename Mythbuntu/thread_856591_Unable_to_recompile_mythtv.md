---
title: "Unable to recompile mythtv"
date: 2008-07-11
forum: Mythbuntu
---

### Post by erland on 2008-07-11
I'm unable to compile the mythtv package, my intention was to apply some patches on the standard installation and then rebuild it with the same flags as the one included with the Mythbuntu 8.04 distribution.

I got problems when I tried to add som patches in debian/patches/ and run debuild, so I did a simple test and just built the standard distribution. 

After installing dependencies with "sudo apt-get build-dep mythtv" and installtion the source with "apt-get source mythtv" I just tried to run "debuild". It compiles for a while and then I get the following problem:
```

ccache g++ -c -pipe -march=i686 -fomit-frame-pointer -O3 -DNDEBUG -g -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -Wno-non-virtual-dtor -D__STDC_CONSTANT_MACROS -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_GLX_PROC_ADDR_ARB -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr\" -DLIBDIR=\"/usr/lib\" -D_LARGEFILE_SOURCE -DUSING_OSS -DUSING_H264TOOLS -DUSING_X11 -DUSING_XV -DUSING_XVMC -DUSING_XVMCW -DUSING_XVMC_VLD -DUSING_OPENGL -DUSING_OPENGL_VSYNC -DUSING_OPENGL_VIDEO -DUSING_FRONTEND -DUSING_FFMPEG_THREADS -DUSING_V4L -DUSING_LINUX_FIREWIRE -DUSING_FIREWIRE -DUSING_LIBAVC_5_3 -DUSING_DBOX2 -DUSING_IPTV -DUSING_HDHOMERUN -DUSING_IVTV -DUSING_DVB -DUSING_BACKEND -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include -I/usr/include -I../.. -I.. -I. -I../libmyth -I../libavcodec -I../libavutil -I../libmythmpeg2 -Idvbdev -Impeg -Iiptv -I../libmythlivemedia/BasicUsageEnvironment/include -I../libmythlivemedia/groupsock/include -I../libmythlivemedia/liveMedia/include -I../libmythlivemedia/UsageEnvironment/include -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o previouslist.o previouslist.cpp
ccache g++ -c -pipe -march=i686 -fomit-frame-pointer -O3 -DNDEBUG -g -Wall -Wno-switch -Wpointer-arith -Wredundant-decls -Wno-non-virtual-dtor -D__STDC_CONSTANT_MACROS -I/usr/include/kde/artsc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_GLX_PROC_ADDR_ARB -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr\" -DLIBDIR=\"/usr/lib\" -D_LARGEFILE_SOURCE -DUSING_OSS -DUSING_H264TOOLS -DUSING_X11 -DUSING_XV -DUSING_XVMC -DUSING_XVMCW -DUSING_XVMC_VLD -DUSING_OPENGL -DUSING_OPENGL_VSYNC -DUSING_OPENGL_VIDEO -DUSING_FRONTEND -DUSING_FFMPEG_THREADS -DUSING_V4L -DUSING_LINUX_FIREWIRE -DUSING_FIREWIRE -DUSING_LIBAVC_5_3 -DUSING_DBOX2 -DUSING_IPTV -DUSING_HDHOMERUN -DUSING_IVTV -DUSING_DVB -DUSING_BACKEND -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include -I/usr/include -I../.. -I.. -I. -I../libmyth -I../libavcodec -I../libavutil -I../libmythmpeg2 -Idvbdev -Impeg -Iiptv -I../libmythlivemedia/BasicUsageEnvironment/include -I../libmythlivemedia/groupsock/include -I../libmythlivemedia/liveMedia/include -I../libmythlivemedia/UsageEnvironment/include -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -o dbcheck.o dbcheck.cpp
dbcheck.cpp: In function ‘bool UpgradeTVDatabaseSchema()’:
dbcheck.cpp:526: internal compiler error: in var_ann, at tree-flow-inline.h:127
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.2/README.Bugs>.
make[3]: *** [dbcheck.o] Error 1
make[3]: Leaving directory `/usr/src/mythtv/mythtv-0.21.0+fixes16838/libs/libmythtv'
make[2]: *** [sub-libmythtv] Error 2
make[2]: Leaving directory `/usr/src/mythtv/mythtv-0.21.0+fixes16838/libs'
make[1]: *** [sub-libs] Error 2
make[1]: Leaving directory `/usr/src/mythtv/mythtv-0.21.0+fixes16838'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
debuild: fatal error at line 1329:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```

Should it work to just run:
1. sudo apt-get source mythtv
2. sudo apt-get build-dep mythtv
3. debuild

Or do I need to install something else to make it work ?
(build-essential and devscripts are already installed)

When I try to compile it with applied patches it fails almost immediately unless I delete the ../mythtv_0.21.0+fixes16838-0ubuntu3.1.diff.gz and ../mythtv_0.21.0+fixes16838.orig.tar.gz files before I run debuild. When I run it with patches I run "dch -i" and change the version before I run debuild.

---

### Post by laga on 2008-07-12
Does that internal compiler error always happen on the same file?

---

### Post by erland on 2008-07-12
> **laga said:**
> Does that internal compiler error always happen on the same file?

I'll have to check next time, I successfully got it to compile by manually instead of debuild running:
fakeroot dpkg-buildpackage -b -uc -us

---

