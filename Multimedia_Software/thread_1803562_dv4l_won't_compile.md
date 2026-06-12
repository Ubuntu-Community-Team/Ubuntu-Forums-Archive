---
title: "dv4l won't compile"
date: 2011-07-13
forum: Multimedia Software
---

### Post by dangerjunkie2002 on 2011-07-13
Hi,

I'm trying to get a DataVideo DAC-100 DV interface to work as a V4L device so I can get analog video into VLC to stream.

I've got vloopback working but I can't get dv4l to compile. I've added the dev packages for all the prerequisites .configure was saying "no" to and that seems to be OK now:

```
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking libraw1394/raw1394.h usability... yes
checking libraw1394/raw1394.h presence... yes
checking for libraw1394/raw1394.h... yes
checking libiec61883/iec61883.h usability... yes
checking libiec61883/iec61883.h presence... yes
checking for libiec61883/iec61883.h... yes
checking libdv/dv.h usability... yes
checking libdv/dv.h presence... yes
checking for libdv/dv.h... yes
checking sys/xattr.h usability... yes
checking sys/xattr.h presence... yes
checking for sys/xattr.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating version.h
config.status: creating config.h
```



When I try to make it doesn't succeed:

```
cc -Wall -O3 -MMD    -c -o normfile.o normfile.c
normfile.c: In function &#8216;normalize&#8217;:
normfile.c:247: warning: ignoring return value of &#8216;getcwd&#8217;, declared with attribute warn_unused_result
cc -Wall -O3 -MMD    -c -o palettes.o palettes.c
cc -Wall -O3 -MMD    -c -o scale.o scale.c
cc -Wall -O3 -MMD    -c -o util.o util.c
cc -Wall -O3 -MMD    -c -o dv4l.o dv4l.c
dv4l.c: In function &#8216;mmap_mode&#8217;:
dv4l.c:789: warning: dereferencing type-punned pointer will break strict-aliasing rules
dv4l.c: In function &#8216;simple_frame_recv&#8217;:
dv4l.c:831: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
cc -lraw1394 -liec61883 -ldv -o dv4l normfile.o palettes.o scale.o util.o dv4l.o
cc -Wall -O3 -shared -fpic -Wl,-soname,libdv4l.so \
	-D DV4LLIBNAME=/usr/local/lib/libdv4l.so \
	-ldl -lraw1394 -liec61883 -ldv interdv4l.c \
	normfile.c scale.c palettes.c util.c -o libdv4l.so
In file included from interdv4l.c:46:
/usr/include/sys/stat.h:504: error: conflicting types for &#8216;stat64&#8217;
/usr/include/sys/stat.h:230: note: previous declaration of &#8216;stat64&#8217; was here
/usr/include/sys/stat.h:511: error: conflicting types for &#8216;lstat64&#8217;
/usr/include/sys/stat.h:278: note: previous declaration of &#8216;lstat64&#8217; was here
/usr/include/sys/stat.h:518: error: conflicting types for &#8216;fstat64&#8217;
/usr/include/sys/stat.h:232: note: previous declaration of &#8216;fstat64&#8217; was here
/usr/include/sys/stat.h:525: error: conflicting types for &#8216;fstatat64&#8217;
/usr/include/sys/stat.h:255: note: previous declaration of &#8216;fstatat64&#8217; was here
interdv4l.c:134: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c: In function &#8216;common_lstat64&#8217;:
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c:134: error: dereferencing pointer to incomplete type
interdv4l.c: At top level:
interdv4l.c:136: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c: In function &#8216;common___xstat64&#8217;:
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c:136: error: dereferencing pointer to incomplete type
interdv4l.c: At top level:
interdv4l.c:138: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c: In function &#8216;common___lxstat64&#8217;:
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c:138: error: dereferencing pointer to incomplete type
interdv4l.c: At top level:
interdv4l.c:167: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:167: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:167: error: conflicting types for &#8216;__xstat64&#8217;
/usr/include/sys/stat.h:436: note: previous declaration of &#8216;__xstat64&#8217; was here
interdv4l.c: In function &#8216;__xstat64&#8217;:
interdv4l.c:167: warning: passing argument 3 of &#8216;orig__xstat64&#8217; from incompatible pointer type
interdv4l.c:167: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c:167: warning: passing argument 3 of &#8216;common___xstat64&#8217; from incompatible pointer type
interdv4l.c:136: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c: At top level:
interdv4l.c:169: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:169: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:169: error: conflicting types for &#8216;__lxstat64&#8217;
/usr/include/sys/stat.h:438: note: previous declaration of &#8216;__lxstat64&#8217; was here
interdv4l.c: In function &#8216;__lxstat64&#8217;:
interdv4l.c:169: warning: passing argument 3 of &#8216;orig__lxstat64&#8217; from incompatible pointer type
interdv4l.c:169: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c:169: warning: passing argument 3 of &#8216;common___lxstat64&#8217; from incompatible pointer type
interdv4l.c:138: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c: At top level:
interdv4l.c:198: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:198: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:198: error: conflicting types for &#8216;lstat64&#8217;
/usr/include/sys/stat.h:278: note: previous declaration of &#8216;lstat64&#8217; was here
interdv4l.c: In function &#8216;lstat64&#8217;:
interdv4l.c:198: warning: passing argument 2 of &#8216;origlstat64&#8217; from incompatible pointer type
interdv4l.c:198: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c:198: warning: passing argument 3 of &#8216;common_lstat64&#8217; from incompatible pointer type
interdv4l.c:134: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c: At top level:
interdv4l.c:485: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:485: warning: &#8216;struct stat64&#8217; declared inside parameter list
interdv4l.c:485: error: conflicting types for &#8216;__fxstat64&#8217;
/usr/include/sys/stat.h:434: note: previous declaration of &#8216;__fxstat64&#8217; was here
interdv4l.c: In function &#8216;__fxstat64&#8217;:
interdv4l.c:485: warning: passing argument 3 of &#8216;orig__fxstat64&#8217; from incompatible pointer type
interdv4l.c:485: note: expected &#8216;struct stat64 *&#8217; but argument is of type &#8216;struct stat64 *&#8217;
interdv4l.c:485: error: dereferencing pointer to incomplete type
interdv4l.c:485: error: dereferencing pointer to incomplete type
interdv4l.c:485: error: dereferencing pointer to incomplete type
interdv4l.c: In function &#8216;ioctl&#8217;:
interdv4l.c:980: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
normfile.c: In function &#8216;normalize&#8217;:
normfile.c:247: warning: ignoring return value of &#8216;getcwd&#8217;, declared with attribute warn_unused_result
make: *** [libdv4l.so] Error 1

```

My C++ isn't quite strong enough to work out what's wrong here. I'd really appreciate any help you could give me in getting this working.

My platform is Ubuntu 10.10 32-bit.

Thanks,
Paul.

---

### Post by no2498 on 2011-07-14
they have stopped  using v4l it is v4l2 now

this may help you just the package 

AmyRose
November 24th, 2008, 08:15 PM
In Intrepid, to fix this problem, I installed the libv4l-0 package and preload it with Skype like this:

 env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

