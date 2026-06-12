---
title: "mtpfs make problem!!"
date: 2008-09-10
forum: Multimedia Software
---

### Post by netpumber on 2008-09-10
Hi all out there !! i have a little prob...:S i want to install mtpfs-0.7 . So i download the source from the site and did the next steps after extract it:


```
./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FUSE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: executing depfiles commands
```

 ```
make
gcc -DPACKAGE_NAME=\"MTPfs\" -DPACKAGE_TARNAME=\"mtpfs\" -DPACKAGE_VERSION=\"0.6\" -DPACKAGE_STRING=\"MTPfs\ 0.6\" -DPACKAGE_BUGREPORT=\"Chris\ Debenham\ \<chris@adebenham.com\>\" -DPACKAGE=\"mtpfs\" -DVERSION=\"0.6\" -DDEBUG=0 -I.  -DFUSE_USE_VERSION=22 -D_FILE_OFFSET_BITS=64 -pthread -I/usr/local/include -I/usr/include/fuse -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -g -O2 -MT mtpfs-mtpfs.o -MD -MP -MF .deps/mtpfs-mtpfs.Tpo -c -o mtpfs-mtpfs.o `test -f 'mtpfs.c' || echo './'`mtpfs.c
mtpfs.c: In function ‘save_playlist’:
mtpfs.c:142: error: too many arguments to function ‘LIBMTP_Create_New_Playlist’
mtpfs.c: In function ‘mtpfs_release’:
mtpfs.c:416: error: too many arguments to function ‘LIBMTP_Send_Track_From_File_Descriptor’
mtpfs.c:432: error: too many arguments to function ‘LIBMTP_Send_File_From_File_Descriptor’
mtpfs.c: In function ‘mtpfs_mkdir’:
mtpfs.c:845: error: too few arguments to function ‘LIBMTP_Create_Folder’
make: *** [mtpfs-mtpfs.o] Error 1

```

What is the prob here ...? Thanx anyway!! ;) cyaz!!

---

