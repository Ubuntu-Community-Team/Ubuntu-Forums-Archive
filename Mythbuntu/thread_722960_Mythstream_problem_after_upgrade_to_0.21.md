---
title: "Mythstream problem after upgrade to 0.21"
date: 2008-03-13
forum: Mythbuntu
---

### Post by axelsvag on 2008-03-13
When I try to start mythstream after the upgrade to 0.21 I just get a message that the libmyth is wrong and that I have to make a distclean. Should I really do that or should I try something else to make mythstream to work again.

---

### Post by ahood on 2008-03-13
Same for me...I updated the packages via the Ubuntu package notification tool last night (Wednesday, March 12).

---

### Post by nasha on 2008-03-13
Try:
```
sudo apt-get upgrade mythstream
```
I had myth video problems when updating to 0.21, and for some reason mythvideo didnt update

---

### Post by elj4176 on 2008-03-13
to fix the mythvideo problem if you haven't fixed it already:

sudo aptitude remove mythdvd

sudo aptitude install mythvideo

---

### Post by Monsieur Gonzalez on 2008-03-13
Same thing is happening to me. The exact message is :

"The mythstream plugin was compiled against libmyth version:0.20.20070821-1,but the installed libmyth is at version: 0.21.20080304-1. You probably want to recompile the mythstream plugin after doing a make distclean"

Apt-get upgrading doesn't show any new packages. Maybe we should file a bug??

---

### Post by straxus on 2008-03-13
I'm having the same problem with mythstream.

"The mythstream plugin was compiled against libmyth version: 0.20.20070821-1, but the installed libmyth is at version: 0.21.20080304-1. You probably want to recompile the mythstream plugin after doing a make distclean."

"sudo apt-get upgrade mythstream" doesn't do anything, and I've already fixed the mythvideo problem.

---

### Post by rich86 on 2008-03-13
the mythstream in the universe repositary seems to still be the 0.18.1 verson it doesn't seem to have been updated to a 0.21 version as i guess it should have been. I tried compiling from source using the myth wiki guide but get hundreds of errors. It seem that it can't find some of the files here is my output:
```

main.cpp:1:32: error: mythtv/mythcontext.h: No such file or directory
main.cpp:2:30: error: mythtv/mythdbcon.h: No such file or directory
main.cpp:3:34: error: mythtv/mythpluginapi.h: No such file or directory

```
Anyone got it to work or know why the version of mythstream is not updated?

EDIT: i was being silly reason for not compiling was not having libmyth-dev installed

---

### Post by straxus on 2008-03-14
> **rich86 said:**
> 
Anyone got it to work or know why the version of mythstream is not updated?


My guess (and that's all it is) is that because 0.18.1 is still the newest version of mythstream, the maintainer didn't think to update the package.  Unfortunately, it needs to be compiled against libmyth 0.21 in order to work now.  Easy enough for many of us to do but it should be fixed, whatever the reason is.

---

### Post by Fopper on 2008-03-14
When you use the mythstream package form [https://launchpad.net/~mythbuntu-trunk/+archive](https://launchpad.net/~mythbuntu-trunk/+archive) (gutsy) it works fine, but it should be fixed in the backports.

---

### Post by tedrogers on 2008-03-22
Thanks...using Mythbuntu and that problem was doing my head in!

To anyone else, just install the package called...

mythstream_0.18.1-0.21.0+trunk16733-0ubuntu0~mythbuntu1_i386.deb

---

### Post by firekool on 2008-03-23
Thanks that worked for me too. I just had to uninstall the old version first.

---

### Post by DJ-Power on 2008-03-24
Thanks for the tip worked for me. I can now use mythstream again.

Regards
DJP :)

---

### Post by silverdulcet on 2008-04-14
I'm having trouble with Mythstream again. It loads fine and displays the default feeds. When you try to view a feed such as an apple trailer or a radio stream it fetches some data and then says no data and returns to idle. It looks like something to do with Mplayer from the backtrace.

```
*** glibc detected *** mplayer: realloc(): invalid pointer: 0x00007f239f49464c ***
======= Backtrace: =========
/lib/libc.so.6(realloc+0x3c9)[0x7f239b7e0139]
/lib/libnss_wins.so.2(Realloc+0x7a)[0x7f239569348a]
/lib/libnss_wins.so.2(debug_add_class+0x93)[0x7f239567f1b3]
/lib/libnss_wins.so.2(debug_init+0x55)[0x7f239567f305]
/lib/libnss_wins.so.2(setup_logging+0x1e)[0x7f239567f33e]
/lib/libnss_wins.so.2(_nss_wins_gethostbyname_r+0x262)[0x7f239562f0a2]
/lib/libc.so.6(gethostbyname2_r+0x19e)[0x7f239b85690e]
/lib/libc.so.6(gethostbyname2+0xc7)[0x7f239b856647]
mplayer(connect2Server_with_af+0x15a)[0x612cfa]
mplayer(connect2Server+0x58)[0x613248]
mplayer(http_send_request+0x176)[0x60f7a6]
mplayer[0x60df14]
mplayer[0x60e9ed]
mplayer(open_stream_plugin+0x1ad)[0x5ffacd]
mplayer(open_stream_full+0xbf)[0x5ffd3f]
mplayer(main+0xdd9)[0x474329]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f239b7861c4]
mplayer(atan+0x349)[0x470ba9]
======= Memory map: ========
00400000-00cdf000 r-xp 00000000 08:01 194377                             /usr/bin/mplayer
00ede000-00f63000 rw-p 008de000 08:01 194377                             /usr/bin/mplayer
00f63000-011ee000 rw-p 00f63000 00:00 0                                  [heap]
7f2394ff4000-7f2394ff6000 r-xp 00000000 08:01 211948                     /lib/libnss_mdns4.so.2
7f2394ff6000-7f23951f6000 ---p 00002000 08:01 211948                     /lib/libnss_mdns4.so.2
7f23951f6000-7f23951f7000 rw-p 00002000 08:01 211948                     /lib/libnss_mdns4.so.2
7f23951f7000-7f23951fb000 r-xp 00000000 08:01 33015504                   /lib/libnss_dns-2.7.so
7f23951fb000-7f23953fb000 ---p 00004000 08:01 33015504                   /lib/libnss_dns-2.7.so
7f23953fb000-7f23953fd000 rw-p 00004000 08:01 33015504                   /lib/libnss_dns-2.7.so
7f23953fd000-7f23953ff000 r-xp 00000000 08:01 211949                     /lib/libnss_mdns4_minimal.so.2
7f23953ff000-7f23955fe000 ---p 00002000 08:01 211949                     /lib/libnss_mdns4_minimal.so.2
7f23955fe000-7f23955ff000 rw-p 00001000 08:01 211949                     /lib/libnss_mdns4_minimal.so.2
7f23955ff000-7f23956ef000 r-xp 00000000 08:01 210728                     /lib/libnss_wins.so.2
7f23956ef000-7f23958ee000 ---p 000f0000 08:01 210728                     /lib/libnss_wins.so.2
7f23958ee000-7f23958fd000 rw-p 000ef000 08:01 210728                     /lib/libnss_wins.so.2
7f23958fd000-7f239590e000 rw-p 7f23958fd000 00:00 0 
7f239590e000-7f2395918000 r-xp 00000000 08:01 33015505                   /lib/libnss_files-2.7.so
7f2395918000-7f2395b18000 ---p 0000a000 08:01 33015505                   /lib/libnss_files-2.7.so
7f2395b18000-7f2395b1a000 rw-p 0000a000 08:01 33015505                   /lib/libnss_files-2.7.so
7f2395b1a000-7f2395b59000 r--p 00000000 08:01 200302                     /usr/lib/locale/en_US.utf8/LC_CTYPE
7f2395b59000-7f2395b5c000 r-xp 00000000 08:01 210556                     /lib/libgpg-error.so.0.3.0
7f2395b5c000-7f2395d5b000 ---p 00003000 08:01 210556                     /lib/libgpg-error.so.0.3.0
7f2395d5b000-7f2395d5c000 rw-p 00002000 08:01 210556                     /lib/libgpg-error.so.0.3.0
7f2395d5c000-7f2395da8000 r-xp 00000000 08:01 210569                     /lib/libgcrypt.so.11.2.3
7f2395da8000-7f2395fa7000 ---p 0004c000 08:01 210569                     /lib/libgcrypt.so.11.2.3
7f2395fa7000-7f2395faa000 rw-p 0004b000 08:01 210569                     /lib/libgcrypt.so.11.2.3
7f2395faa000-7f2395fba000 r-xp 00000000 08:01 195946                     /usr/lib/libtasn1.so.3.0.12
7f2395fba000-7f23961b9000 ---p 00010000 08:01 195946                     /usr/lib/libtasn1.so.3.0.12
7f23961b9000-7f23961ba000 rw-p 0000f000 08:01 195946                     /usr/lib/libtasn1.so.3.0.12
7f23961ba000-7f2396235000 r-xp 00000000 08:01 195996                     /usr/lib/libgnutls.so.13.9.1
7f2396235000-7f2396434000 ---p 0007b000 08:01 195996                     /usr/lib/libgnutls.so.13.9.1
7f2396434000-7f239643e000 rw-p 0007a000 08:01 195996                     /usr/lib/libgnutls.so.13.9.1
7f239643e000-7f2396456000 r-xp 00000000 08:01 202291                     /usr/lib/libsasl2.so.2.0.22
7f2396456000-7f2396656000 ---p 00018000 08:01 202291                     /usr/lib/libsasl2.so.2.0.22
7f2396656000-7f2396657000 rw-p 00018000 08:01 202291                     /usr/lib/libsasl2.so.2.0.22
7f2396657000-7f2396659000 r-xp 00000000 08:01 210572                     /lib/libkeyutils-1.2.so
7f2396659000-7f2396858000 ---p 00002000 08:01 210572                     /lib/libkeyutils-1.2.so
7f2396858000-7f2396859000 rw-p 00001000 08:01 210572                     /lib/libkeyutils-1.2.so
7f2396859000-7f2396860000 r-xp 00000000 08:01 196292                     /usr/lib/libkrb5support.so.0.1
7f2396860000-7f2396a5f000 ---p 00007000 08:01 196292                     /usr/lib/libkrb5support.so.0.1
7f2396a5f000-7f2396a60000 rw-p 00006000 08:01 196292                     /usr/lib/libkrb5support.so.0.1
7f2396a60000-7f2396a65000 r-xp 00000000 08:01 196001                     /usr/lib/libXdmcp.so.6.0.0
7f2396a65000-7f2396c64000 ---p 00005000 08:01 196001                     /usr/lib/libXdmcp.so.6.0.0
7f2396c64000-7f2396c65000 rw-p 00004000 08:01 196001                     /usr/lib/libXdmcp.so.6.0.0
7f2396c65000-7f2396c6b000 r-xp 00000000 08:01 197775                     /usr/lib/libgpm.so.1.19.6
7f2396c6b000-7f2396e6a000 ---p 00006000 08:01 197775                     /usr/lib/libgpm.so.1.19.6
7f2396e6a000-7f2396e6b000 rw-p 00005000 08:01 197775                     /usr/lib/libgpm.so.1.19.6
7f2396e6b000-7f2396e8d000 r-xp 00000000 08:01 194740                     /usr/lib/libexpat.so.1.5.2
7f2396e8d000-7f239708d000 ---p 00022000 08:01 194740                     /usr/lib/libexpat.so.1.5.2
7f239708d000-7f239708f000 rw-p 00022000 08:01 194740                     /usr/lib/libexpat.so.1.5.2
7f239708f000-7f239709d000 r-xp 00000000 08:01 195891                     /usr/lib/liblber-2.4.so.2.0.3
7f239709d000-7f239729c000 ---p 0000e000 08:01 195891                     /usr/lib/liblber-2.4.so.2.0.3
7f239729c000-7f239729d000 rw-p 0000d000 08:01 195891                     /usr/lib/liblber-2.4.so.2.0.3
7f239729d000-7f23972de000 r-xp 00000000 08:01 195893                     /usr/lib/libldap_r-2.4.so.2.0.3
7f23972de000-7f23974de000 ---p 00041000 08:01 195893                     /usr/lib/libldap_r-2.4.so.2.0.3
7f23974de000-7f23974e0000 rw-p 00041000 08:01 195893                     /usr/lib/libldap_r-2.4.so.2.0.3
7f23974e0000-7f23974e2000 rw-p 7f23974e0000 00:00 0 
7f23974e2000-7f23974e4000 r-xp 00000000 08:01 210553                     /lib/libcom_err.so.2.1
7f23974e4000-7f23976e3000 ---p 00002000 08:01 210553                     /lib/libcom_err.so.2.1
7f23976e3000-7f23976e4000 rw-p 00001000 08:01 210553                     /lib/libcom_err.so.2.1
7f23976e4000-7f2397707000 r-xp 00000000 08:01 196211                     /usr/lib/libk5crypto.so.3.1
7f2397707000-7f2397906000 ---p 00023000 08:01 196211                     /usr/lib/libk5crypto.so.3.1
7f2397906000-7f2397908000 rw-p 00022000 08:01 196211                     /usr/lib/libk5crypto.so.3.1
7f2397908000-7f239799c000 r-xp 00000000 08:01 196291                     /usr/lib/libkrb5.so.3.3
7f239799c000-7f2397b9c000 ---p 00094000 08:01 196291                     /usr/lib/libkrb5.so.3.3
7f2397b9c000-7f2397b9f000 rw-p 00094000 08:01 196291                     /usr/lib/libkrb5.so.3.3
7f2397b9f000-7f2397bc8000 r-xp 00000000 08:01 196189                     /usr/lib/libgssapi_krb5.so.2.2
7f2397bc8000-7f2397dc8000 ---p 00029000 08:01 196189                     /usr/lib/libgssapi_krb5.so.2.2
7f2397dc8000-7f2397dca000 rw-p 00029000 08:01 196189                     /usr/lib/libgssapi_krb5.so.2.2
7f2397dca000-7f2397ddc000 r-xp 00000000 08:01 33015511                   /lib/libresolv-2.7.so
7f2397ddc000-7f2397fdc000 ---p 00012000 08:01 33015511                   /lib/libresolv-2.7.so
7f2397fdc000-7f2397fde000 rw-p 00012000 08:01 33015511                   /lib/libresolv-2.7.so
7f2397fde000-7f2397fe0000 rw-p 7f2397fde000 00:00 0 
7f2397fe0000-7f2397fe9000 r-xp 00000000 08:01 33015498                   /lib/libcrypt-2.7.so
7f2397fe9000-7f23981e8000 ---p 00009000 08:01 33015498                   /lib/libcrypt-2.7.so
7f23981e8000-7f23981ea000 rw-p 00008000 08:01 33015498                   /lib/libcrypt-2.7.so
7f23981ea000-7f2398218000 rw-p 7f23981ea000 00:00 0 
7f2398218000-7f2398244000 r-xp 00000000 08:01 196225                     /usr/lib/libpixman-1.so.0.10.0
7f2398244000-7f2398444000 ---p 0002c000 08:01 196225                     /usr/lib/libpixman-1.so.0.10.0
7f2398444000-7f2398446000 rw-p 0002c000 08:01 196225                     /usr/lib/libpixman-1.so.0.10.0
7f2398446000-7f2398471000 r-xp 00000000 08:01 199544                     /usr/lib/libpangoft2-1.0.so.0.2000.1
7f2398471000-7f2398671000 ---p 0002b000 08:01 199544                     /usr/lib/libpangoft2-1.0.so.0.2000.1
7f2398671000-7f2398672000 rw-p 0002b000 08:01 199544                     /usr/lib/libpangoft2-1.0.so.0.2000.1
7f2398672000-7f239867b000 r-xp 00000000 08:01 194864                no buffer to write to 

```

---

