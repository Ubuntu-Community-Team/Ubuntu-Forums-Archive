---
title: "Can't make gnomad2-2.9.1"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by disk11 on 2008-04-04
The gnomad2 in the repo doesn't work for me, I get a malloc error.  So I go the latest gnomad2 and libnjb source, and make for gnomad2 doesn't finish.  I get this:
```
matt@laptop:/media/hda3/gnomad2-2.9.1$ make
Making all in src
make[1]: Entering directory `/media/hda3/gnomad2-2.9.1/src'
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DBUSGLIB=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT gnomad2.o -MD -MP -MF .deps/gnomad2.Tpo -c -o gnomad2.o gnomad2.c
gnomad2.c: In function ‘main’:
gnomad2.c:724: error: ‘dbus_error’ undeclared (first use in this function)
gnomad2.c:724: error: (Each undeclared identifier is reported only once
gnomad2.c:724: error: for each function it appears in.)
gnomad2.c:725: error: ‘dbus_session_conn’ undeclared (first use in this function)
make[1]: *** [gnomad2.o] Error 1
make[1]: Leaving directory `/media/hda3/gnomad2-2.9.1/src'
make: *** [all-recursive] Error 1

```

I've gotten all the packages except for libnjb that come up in "apt-get build-dep gnomad2" and getting all the dbus* files but nothing fixes the error I get.  How do I fix this?

---

### Post by disk11 on 2008-04-05
More issues, the gnomad2 available in the repositories seems to corrupt libc6.  I can transfer 1 song then I get this
```
matt@laptop:~$ gnomad2 
LIBMTP_Get_First_Device: No Devices Attached
This is a PDE device
*** glibc detected *** gnomad2: malloc(): memory corruption: 0xb5e92b80 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76b5636]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x90)[0xb76b6fc0]
/usr/lib/libid3tag.so.0(id3_util_compress+0x42)[0xb77f0462]
======= Memory map: ========
08048000-0806f000 r-xp 00000000 03:01 2140537    /usr/bin/gnomad2
0806f000-08070000 rw-p 00027000 03:01 2140537    /usr/bin/gnomad2
08070000-084ad000 rw-p 08070000 00:00 0          [heap]
b5ce2000-b5dfa000 r-xp 00000000 03:01 2136109    /usr/lib/libxml2.so.2.6.30
b5dfa000-b5dff000 rw-p 00118000 03:01 2136109    /usr/lib/libxml2.so.2.6.30
b5dff000-b5ef4000 rw-p b5dff000 00:00 0 
b5ef4000-b5f00000 ---p b5ef4000 00:00 0 
b5f44000-b5f90000 r--p 00000000 03:01 2363499    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
b5f90000-b6014000 r--p 00000000 03:01 2365055    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b604d000-b6057000 r-xp 00000000 03:01 2394403    /lib/libgcc_s.so.1
b6057000-b6058000 rw-p 0000a000 03:01 2394403    /lib/libgcc_s.so.1
b6058000-b6067000 r-xp 00000000 03:01 2394375    /lib/libbz2.so.1.0.4
b6067000-b6068000 rw-p 0000f000 03:01 2394375    /lib/libbz2.so.1.0.4
b6068000-b609a000 r-xp 00000000 03:01 2135459    /usr/lib/libcroco-0.6.so.3.0.1
b609a000-b609d000 rw-p 00031000 03:01 2135459    /usr/lib/libcroco-0.6.so.3.0.1
b609d000-b60cd000 r-xp 00000000 03:01 2135701    /usr/lib/libgsf-1.so.114.0.7
b60cd000-b60d0000 rw-p 0002f000 03:01 2135701    /usr/lib/libgsf-1.so.114.0.7
b60d0000-b60d1000 rw-p b60d0000 00:00 0 
b60d1000-b6101000 r-xp 00000000 03:01 2135999    /usr/lib/librsvg-2.so.2.18.2
b6101000-b6102000 rw-p 00030000 03:01 2135999    /usr/lib/librsvg-2.so.2.18.2
b6113000-b6114000 r-xp 00000000 03:01 2198997    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6114000-b6115000 rw-p 00000000 03:01 2198997    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b6115000-b6116000 ---p b6115000 00:00 0 
b6116000-b6916000 rw-p b6116000 00:00 0 
b6916000-b6976000 rw-s 00000000 00:09 458765     /SYSV00000000 (deleted)
b6976000-b6a01000 r--p 00000000 03:01 2365056    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6a01000-b6a03000 r-xp 00000000 03:01 2265326    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6a03000-b6a04000 rw-p 00001000 03:01 2265326    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6a04000-b6a0a000 r--s 00000000 03:01 183916     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6a0a000-b6a0d000 r--s 00000000 03:01 183930     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6a0d000-b6a11000 r--s 00000000 03:01 183913     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6a11000-b6a12000 r--s 00000000 03:01 183923     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6a12000-b6a13000 r--s 00000000 03:01 183903     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6a13000-b6a16000 r--s 00000000 03:01 183918     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6a16000-b6a17000 r--s 00000000 03:01 183909     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b6a17000-b6a1d000 r--s 00000000 03:01 179572     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6a1d000-b6a1f000 r--s 00000000 03:01 183927     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6a1f000-b6a27000 r--s 00000000 03:01 183931     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6a27000-b6a2d000 r--s 00000000 03:01 183895     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6a2d000-b6a2e000 r--s 00000000 03:01 183901     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6a2e000-b6a30000 r--s 00000000 03:01 183928     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6a30000-b6a36000 r--s 00000000 03:01 183925     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6a36000-b6a3a000 r--s 00000000 03:01 183893     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6a3a000-b6a3c000 r--s 00000000 03:01 183987     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6a3c000-b6a3d000 r--s 00000000 03:01 183935     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b6a3d000-b6a3e000 r--s 00000000 03:01 183932     /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b6a3e000-b6a3f000 r--s 00000000 03:01 183922     /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b6a3f000-b6a42000 r--s 00000000 03:01 183920     /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b6a42000-b6a45000 r--s 00000000 03:01 183936     /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b6a45000-b6a47000 r--s 00000000 03:01 183892     /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b6a47000-b6a48000 r--s 00000000 03:01 183933     /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b6a48000-b6a49000 r--s 00000000 03:01 183897     /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b6a49000-b6a4a000 r--s 00000000 03:01 183917     /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b6a4a000-b6a4f000 r--s 00000000 03:01 183912     /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b6a4f000-b6a54000 r--s 00000000 03:01 183894     /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b6a54000-b6a56000 r--s 00000000 03:01 183910     /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b6a56000-b6a59000 r--s 00000000 03:01 183904     /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b6a59000-b6a5a000 r--s 00000000 03:01 183929     /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b6a5a000-b6a5b000 r--s 00000000 03:01 183900     /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b6a5b000-b6a5e000 r--s 00000000 03:01 183898     /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b6a5e000-b6a64000 r--s 00000000 03:01 183896     /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b6a64000-b6a65000 r--s 00000000 03:01 183914     /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b6a65000-b6a6d000 r--s 00000000 03:01 179417     /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b6a6d000-b6a6f000 r--s 00000000 03:01 183915     /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b6a6f000-b6a73000 r--s 00000000 03:01 183921     /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6a73000-b6a76000 r--s 00000000 03:01 183905     /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6a76000-b71d5000 r--p 00000000 03:01 85988      /usr/share/icons/gnome/icon-theme.cache
b71d5000-b7280000 r--p 00000000 03:01 85985      /usr/share/icons/Tangerine/icon-theme.cache
b7280000-b73e6000 r--p 00000000 03:01 84620      /usr/share/icons/Human/icon-theme.cache
b73e6000-b73f8000 r-xp 00000000 03:01 2198963    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b73f8000-b73f9000 rw-p 00011000 03:01 2198963    /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b73f9000-b7402000 r-xp 00000000 03:01 2397780    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7402000-b7404000 rw-p 00008000 03:01 2397780    /lib/tls/i686/cmov/libnss_files-2.6.1.so
b7404000-b740c000 r-xp 00000000 03:01 2397784    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b740c000-b740e000 rw-p 00007000 03:01 2397784    /lib/tls/i686/cmov/libnss_nis-2.6.1.so
b740e000-b7422000 r-xp 00000000 03:01 2397774    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7422000-b7424000 rw-p 00013000 03:01 2397774    /lib/tls/i686/cmov/libnsl-2.6.1.so
b7424000-b7426000 rw-p b7424000 00:00 0 
b7426000-b742d000 r-xp 00000000 03:01 2397776    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b742d000-b742f000 rw-p 00006000 03:01 2397776    /lib/tls/i686/cmov/libnss_compat-2.6.1.so
b7436000-b7437000 rw-p b7436000 00:00 0 
b7437000-b743b000 r-xp 00000000 03:01 2198989    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b743b000-b743c000 rw-p 00003000 03:01 2198989    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b743c000-b743d000 rw-p b743c000 00:00 0 
b743d000-b743e000 r-xp 00000000 03:01 2140720    /usr/lib/gconv/ISO8859-1.so
b743e000-b7440000 rw-p 00000000 03:01 2140720    /usr/lib/gconv/ISO8859-1.so
b7440000-b747f000 r--p 00000000 03:01 2199795    /usr/lib/locale/en_US.utf8/LC_CTYPE
b747f000-b755f000 r--p 00000000 03:01 2199794    /usr/lib/locale/en_US.utf8/LC_COLLATE
b755f000-b7561000 rw-p b755f000 00:00 0 
b7561000-b7565000 r-xp 00000000 03:01 2135348    /usr/lib/libXdmcp.so.6.0.0
b7565000-b7566000 rw-p 00003000 03:01 2135348    /usr/lib/libXdmcp.so.6.0.0
b7566000-b7588000 r-xp 00000000 03:01 2135963    /usr/lib/libpng12.so.0.15.0
b7588000-b7589000 rw-p 00021000 03:01 2135963    /usr/lib/libpng12.so.0.15.0
b7589000-b758b000 r-xp 00000000 03:01 2135337    /usr/lib/libXau.so.6.0.0
b758b000-b758c000 rw-p 00001000 03:01 2135337    /usr/lib/libXau.so.6.0.0
b758c000-b75aa000 r-xp 00000000 03:01 2135539    /usr/lib/libexpat.so.1.0.0
b75aa000-b75ac000 rw-p 0001e000 03:01 2135539    /usr/lib/libexpat.so.1.0.0
b75ac000-b75ad000 rw-p b75ac000 00:00 0 
b75ad000-b7619000 r-xp 00000000 03:01 2135553    /usr/lib/libfreetype.so.6.3.16
b7619000-b761d000 rw-p 0006b000 03:01 2135553    /usr/lib/libfreetype.so.6.3.16
b761d000-b764a000 r-xp 00000000 03:01 2135936    /usr/lib/libpangoft2-1.0.so.0.1800.2
b764a000-b764b000 rw-p 0002c000 03:01 2135936    /usr/lib/libpangoft2-1.0.so.0.1800.2
b764b000-b778f000 r-xp 00000000 03:01 2397763    /lib/tls/i686/cmov/libc-2.6.1.so
b778f000-b7790000 r--p 00143000 03:01 2397763    /lib/tls/i686/cmov/libc-2.6.1.so
b7790000-b7792000 rw-p 00144000 03:01 2397763    /lib/tls/i686/cmov/libc-2.6.1.so
b7792000-b7795000 rw-p b7792000 00:00 0 
b7795000-b77a9000 r-xp 00000000 03:01 2397789    /lib/tls/i686/cmov/libpthread-2.6.1.so
b77a9000-b77ab000 rw-p 00013000 03:01 2397789    /lib/tls/i686/cmov/libpthread-2.6.1.so
b77ab000-b77ae000 rw-p b77ab000 00:00 0 
b77ae000-b77d0000 r-xp 00000000 03:01 2135878    /usr/lib/libmtp.so.6.0.1
b77d0000-b77d3000 rw-p 00022000 03:01 2135878    /usr/lib/libmtp.so.6.0.1
b77d3000-b77e7000 r-xp 00000000 03:01 2136115    /usr/lib/libz.so.1.2.3.3
b77e7000-b77e8000 rw-p 00013000 03:01 2136115    /usr/lib/libz.so.1.2.3.3
b77e8000-b77f6000 r-xp 00000000 03:01 2139664    /usr/lib/libid3tag.so.0.3.0
b77f6000-b77f8000 rw-p 0000d000 03:01 2139664    /usr/lib/libid3tag.so.0.3.0
b77f8000-b78b4000 r-xp 00000000 03:01 2135631    /usr/lib/libglib-2.0.so.0.1400.1
b78b4000-b78b5000 rw-p 000bc000 03:01 2135631    /usr/lib/libglib-2.0.so.0.1400.1
b78b5000-b78b7000 r-xp 00000000 03:01 2397769    /lib/tls/i686/cmov/libdl-2.6.1.so
b78b7000-b78b9000 rw-p 00001000 03:01 2397769    /lib/tls/i686/cmov/libdl-2.6.1.so
b78b9000-b78bc000 r-xp 00000000 03:01 2135641    /usr/lib/libgmodule-2.0.so.0.1400.1
b78bc000-b78bd000 rw-p 00002000 03:01 2135641    /usr/lib/libgmodule-2.0.so.0.1400.1
b78bd000-b78be000 rw-p b78bd000 00:00 0 
b78be000-b78f8000 r-xp 00000000 03:01 2135681    /usr/lib/libgobject-2.0.so.0.1400.1
b78f8000-b78f9000 rw-p 0003a000 03:01 2135681    /usr/lib/libgobject-2.0.so.0.1400.1
b78f9000-b78fd000 r-xp 00000000 03:01 2135354    /usr/lib/libXfixes.so.3.1.0
b78fd000-b78fe000 rw-p 00003000 03:01 2135354    /usr/lib/libXfixes.so.3.1.0
b78fe000-b79eb000 r-xp 00000000 03:01 2135331    /usr/lib/libX11.so.6.2.0
b79eb000-b79ef000 rw-p 000ed000 03:01 2135331    /usr/lib/libX11.so.6.2.0
b79ef000-b7a64000 r-xp 00000000 03:01 2135441    /usr/lib/libcairo.so.2.11.5
b7a64000-b7a66000 rw-p 00074000 03:01 2135441    /usr/lib/libcairo.so.2.11.5
b7a66000-b7aa1000 r-xp 00000000 03:01 2135932    /usr/lib/libpango-1.0.so.0.1800.2
b7aa1000-b7aa3000 rw-p 0003b000 03:01 2135932    /usr/lib/libpango-1.0.so.0.1800.2
b7aa3000-b7aa5000 r-xp 00000000 03:01 2135346    /usr/lib/libXdamage.so.1.1.0
b7aa5000-b7aa6000 rw-p 00001000 03:01 2135346    /usr/lib/libXdamage.so.1.1.0
b7aa6000-b7aa7000 rw-p b7aa6000 00:00 0 
b7aa7000-b7aa9000 r-xp 00000000 03:01 2135342    /usr/lib/libXcomposite.so.1.0.0
b7aa9000-b7aaa000 rw-p 00001000 03:01 2135342    /usr/lib/libXcomposite.so.1.0.0
b7aaa000-b7ab2000 r-xp 00000000 03:01 2135344    /usr/lib/libXcursor.so.1.0.2
b7ab2000-b7ab3000 rw-p 00007000 03:01 2135344    /usr/lib/libXcursor.so.1.0.2
b7ab3000-b7ab8000 r-xp 00000000 03:01 2135372    /usr/lib/libXrandr.so.2.1.0
b7ab8000-b7ab9000 rw-p 00005000 03:01 2135372    /usr/lib/libXrandr.so.2.1.0
b7ab9000-b7ac0000 r-xp 00000000 03:01 2135360    /usr/lib/libXi.so.6.0.0
b7ac0000-b7ac1000 rw-p 00006000 03:01 2135360    /usr/lib/libXi.so.6.0.0
b7ac1000-b7ac3000 r-xp 00000000 03:01 2135362    /usr/lib/libXinerama.so.1.0.0
b7ac3000-b7ac4000 rw-p 00001000 03:01 2135362    /usr/lib/libXinerama.so.1.0.0
b7ac4000-b7acb000 r-xp 00000000 03:01 2135374    /usr/lib/libXrender.so.1.3.0
b7acb000-b7acc000 rw-p 00006000 03:01 2135374    /usr/lib/libXrender.so.1.3.0
b7acc000-b7acd000 rw-p b7acc000 00:00 0 
b7acd000-b7ada000 r-xp 00000000 03:01 2135352    /usr/lib/libXext.so.6.4.0
b7ada000-b7adb000 rw-p 0000d000 03:01 2135352    /usr/lib/libXext.so.6.4.0
b7adb000-b7afe000 r-xp 00000000 03:01 2135545    /usr/lib/libfontconfig.so.1.2.0
b7afe000-b7b06000 rw-p 00023000 03:01 2135545    /usr/lib/libfontconfig.so.1.2.0
b7b06000-b7b0e000 r-xp 00000000 03:01 2135934    /usr/lib/libpangocairo-1.0.so.0.1800.2
b7b0e000-b7b0f000 rw-p 00007000 03:01 2135934    /usr/lib/libpangocairo-1.0.so.0.1800.2
b7b0f000-b7b32000 r-xp 00000000 03:01 2397771    /lib/tls/i686/cmov/libm-2.6.1.so
b7b32000-b7b34000 rw-p 00023000 03:01 2397771    /lib/tls/i686/cmov/libm-2.6.1.so
b7b34000-b7b4b000 r-xp 00000000 03:01 2135593    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7b4b000-b7b4c000 rw-p 00016000 03:01 2135593    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
b7b4c000-b7b65000 r-xp 00000000 03:01 2135410    /usr/lib/libatk-1.0.so.0.2009.1
b7b65000-b7b67000 rw-p 00018000 03:01 2135410    /usr/lib/libatk-1.0.so.0.2009.1
b7b67000-b7b68000 rw-p b7b67000 00:00 0 
b7b68000-b7bec000 r-xp 00000000 03:01 2135591    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7bec000-b7bef000 rw-p 00084000 03:01 2135591    /usr/lib/libgdk-x11-2.0.so.0.1200.0
b7bef000-b7f6c000 r-xp 00000000 03:01 2135746    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7f6c000-b7f73000 rw-p 0037c000 03:01 2135746    /usr/lib/libgtk-x11-2.0.so.0.1200.0
b7f73000-b7f74000 rw-p b7f73000 00:00 0 
b7f74000-b7f7a000 r-xp 00000000 03:01 2394473    /lib/libusb-0.1.so.4.4.4
b7f7a000-b7f7c000 rw-p 00005000 03:01 2394473    /lib/libusb-0.1.so.4.4.4
b7f7c000-b7fa3000 r-xp 00000000 03:01 2297021    /usr/local/lib/libnjb.so.5.1.0
b7fa3000-b7fa4000 rw-p 00027000 03:01 2297021    /usr/local/lib/libnjb.so.5.1.0
b7fa4000-b7fab000 r-xp 00000000 03:01 2397793    /lib/tls/i686/cmov/librt-2.6.1.so
b7fab000-b7fad000 rw-p 00006000 03:01 2397793    /lib/tls/i686/cmov/librt-2.6.1.so
b7fad000-b7fb1000 r-xp 00000000 03:01 2135743    /usr/lib/libgthread-2.0.so.0.1400.1
b7fb1000-b7fb2000 rw-p 00003000 03:01 2135743    /usr/lib/libgthread-2.0.so.0.1400.1
b7fb2000-b7fb3000 rw-p b7fb2000 00:00 0 
b7fb3000-b7fb4000 r--p 00000000 03:01 2199800    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7fb4000-b7fb5000 r--p 00000000 03:01 2199803    /usr/lib/locale/en_US.utf8/LC_TIME
b7fb5000-b7fb6000 r--p 00000000 03:01 2199798    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7fb6000-b7fb7000 r--p 00000000 03:01 2199804    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7fb7000-b7fb8000 r--p 00000000 03:01 2199801    /usr/lib/locale/en_US.utf8/LC_PAPER
b7fb8000-b7fb9000 r--p 00000000 03:01 2199799    /usr/lib/locale/en_US.utf8/LC_NAME
b7fb9000-b7fba000 r--p 00000000 03:01 2199793    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7fba000-b7fbb000 r--p 00000000 03:01 2199802    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7fbb000-b7fbc000 r--p 00000000 03:01 2199797    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7fbc000-b7fc3000 r--s 00000000 03:01 2133864    /usr/lib/gconv/gconv-modules.cache
b7fc3000-b7fc4000 r--p 00000000 03:01 2199796    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7fc4000-b7fc5000 rw-p b7fc4000 00:00 0 
b7fc5000-b7fdf000 r-xp 00000000 03:01 2397516    /lib/ld-2.6.1.so
b7fdf000-b7fe1000 rw-p 00019000 03:01 2397516    /lib/ld-2.6.1.so
bfdfc000-bfe12000 rw-p bfdfc000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

If I reinstall libc6, it works for a bit then I eventually get the core dump again.

---

### Post by xc3RnbFO8P on 2008-04-05
I dont know if it helps, but read it:
[http://www.debianhelp.org/node/12820]("http://www.debianhelp.org/node/12820")

---

### Post by disk11 on 2008-04-08
I finally got the new gnomad2 to compile and install, but I get the same error.

I also installed a newer libc6 from debian.org and it still crashes.  Gonna run memtest.

---

### Post by Be_Nooze on 2008-04-15
Hi,
I cannot make it neither, I get the following log:

```
ben@ben-desktop:~/Download/gnomad2-2.9.1$ sudo make
Making all in src
make[1]: entrant dans le répertoire « /home/ben/Download/gnomad2-2.9.1/src »
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT id3read.o -MD -MP -MF .deps/id3read.Tpo -c -o id3read.o id3read.c
mv -f .deps/id3read.Tpo .deps/id3read.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT gnomad2.o -MD -MP -MF .deps/gnomad2.Tpo -c -o gnomad2.o gnomad2.c
mv -f .deps/gnomad2.Tpo .deps/gnomad2.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT prefs.o -MD -MP -MF .deps/prefs.Tpo -c -o prefs.o prefs.c
mv -f .deps/prefs.Tpo .deps/prefs.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT filenaming.o -MD -MP -MF .deps/filenaming.Tpo -c -o filenaming.o filenaming.c
mv -f .deps/filenaming.Tpo .deps/filenaming.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF .deps/jukebox.Tpo -c -o jukebox.o jukebox.c
mv -f .deps/jukebox.Tpo .deps/jukebox.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT util.o -MD -MP -MF .deps/util.Tpo -c -o util.o util.c
mv -f .deps/util.Tpo .deps/util.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT mp3file.o -MD -MP -MF .deps/mp3file.Tpo -c -o mp3file.o mp3file.c
mv -f .deps/mp3file.Tpo .deps/mp3file.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT editmeta.o -MD -MP -MF .deps/editmeta.Tpo -c -o editmeta.o editmeta.c
mv -f .deps/editmeta.Tpo .deps/editmeta.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT filesystem.o -MD -MP -MF .deps/filesystem.Tpo -c -o filesystem.o filesystem.c
mv -f .deps/filesystem.Tpo .deps/filesystem.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT playlists.o -MD -MP -MF .deps/playlists.Tpo -c -o playlists.o playlists.c
mv -f .deps/playlists.Tpo .deps/playlists.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT xfer.o -MD -MP -MF .deps/xfer.Tpo -c -o xfer.o xfer.c
mv -f .deps/xfer.Tpo .deps/xfer.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT data.o -MD -MP -MF .deps/data.Tpo -c -o data.o data.c
mv -f .deps/data.Tpo .deps/data.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT player.o -MD -MP -MF .deps/player.Tpo -c -o player.o player.c
mv -f .deps/player.Tpo .deps/player.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT metadata.o -MD -MP -MF .deps/metadata.Tpo -c -o metadata.o metadata.c
mv -f .deps/metadata.Tpo .deps/metadata.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT wmaread.o -MD -MP -MF .deps/wmaread.Tpo -c -o wmaread.o wmaread.c
mv -f .deps/wmaread.Tpo .deps/wmaread.Po
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.1\" -DPACKAGE_STRING=\"gnomad2\ 2.9.1\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT wavfile.o -MD -MP -MF .deps/wavfile.Tpo -c -o wavfile.o wavfile.c
mv -f .deps/wavfile.Tpo .deps/wavfile.Po
gcc  -g -O2   -o gnomad2 id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o  -pthread -lgthread-2.0 -lrt -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -lmtp -lusb  
make[1]: quittant le répertoire « /home/ben/Download/gnomad2-2.9.1/src »
Making all in doc
make[1]: entrant dans le répertoire « /home/ben/Download/gnomad2-2.9.1/doc »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /home/ben/Download/gnomad2-2.9.1/doc »
Making all in po
make[1]: entrant dans le répertoire « /home/ben/Download/gnomad2-2.9.1/po »
file=`echo ca | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ca.po
/bin/sh: -o: not found
make[1]: *** [ca.gmo] Erreur 127
make[1]: quittant le répertoire « /home/ben/Download/gnomad2-2.9.1/po »
make: *** [all-recursive] Erreur 1
```

Any idea about what may be causing this?
Thanks,

---

### Post by KeithUK on 2008-05-18
If you download the .deb file for Gnomad2 2.9.1 from the Debian SID site you can install it using dpkg (need to install libtagc0 from the Ubuntu repositories). It installs and runs ok but I get a crash when transferring fiels from the player to the PC. 

Bug report made to Gnomad2 project site, see [http://sourceforge.net/tracker/index.php?func=detail&aid=1966486&group_id=65573&atid=511470](http://sourceforge.net/tracker/index.php?func=detail&aid=1966486&group_id=65573&atid=511470)

---

