---
title: "Compiling fglrx 8.28.8 with kernel 2.6.18"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by dutchmega on 2006-11-13
Hey,

I have a Radeon 8500 and the 8.28.8 version of fglrx is the last to support is. But because I'm running a custom kernel ( Edgy, vanilla 2.6.18.1 ) I need to compile it.

So I downloaded the linux drivers. Generated .deb packages and installed it according to [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide).
But instead of using module-assistent, I extracted the fglrx-tar in /usr/src and applied the 2.6.18.1 patch to it (or else it doesn't compile), found at [http://www.jikos.cz/jikos/dev/fglrx_8.12.26_kernel_2.6.18-rc4.patch](http://www.jikos.cz/jikos/dev/fglrx_8.12.26_kernel_2.6.18-rc4.patch).

Compile log:
```
robbie@cc1074988-a:/usr/src/modules/fglrx$ sudo ./make.sh
ATI module generator V 2.0
==========================
initializing...
./make.sh: line 444: [: =: unary operator expected
./make.sh: line 518: [: =: unary operator expected
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
 Assuming default VMAP API
doing Makefile based build for kernel 2.6.x and higher
./make.sh: line 887: cd: 2.6.x: No such file or directory
make -C /lib/modules/2.6.18.1/build SUBDIRS=/usr/src/modules/fglrx modules
make[1]: Entering directory `/usr/src/linux-2.6.18.1'
  CC [M]  /usr/src/modules/fglrx/firegl_public.o
/usr/src/modules/fglrx/firegl_public.c:449: warning: initialization from incompatible pointer type
/usr/src/modules/fglrx/firegl_public.c: In function &#8216;firegl_stub_open&#8217;:
/usr/src/modules/fglrx/firegl_public.c:572: warning: assignment discards qualifiers from pointer target type
  LD [M]  /usr/src/modules/fglrx/fglrx.o
  Building modules, stage 2.
  MODPOST
  LD [M]  /usr/src/modules/fglrx/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-2.6.18.1'
build succeeded with return value 0
ln: creating symbolic link `./fglrx.ko' to `2.6.x/fglrx.ko': File exists
duplication skipped - generator was not called from regular lib tree
done.
```

Only some warnings. Also /usr/srx/linux points to the 2.6.18.1 source.
But after editing xorg.conf to include fglrx:

sudo modprobe fglrx
```
FATAL: Error running install command for fglrx
```

dmesg | tail doesn't get me any new messages. fglrx is also added to restricted modules. Composite is disabled.. Forcing to gcc4.0 doesn't work...
Any ideas?

---

