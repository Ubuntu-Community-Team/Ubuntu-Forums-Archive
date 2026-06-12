---
title: "How do I upgrade to xserver-xorg-video-intel 2.9.1?"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Nakor BlueRider on 2009-11-01
There seems to be a problem with winforms not displaying text under 2.9.0, and a couple pages I've seen mention that upgrading the driver to 2.9.1 resolves the problem:

[http://www.mail-archive.com/mono-bugs@lists.ximian.com/msg68497.html](http://www.mail-archive.com/mono-bugs@lists.ximian.com/msg68497.html)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/462349](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/462349)

However, 2.9.1 is not in the Karmic repositories yet.  I downloaded and extracted the xf86-video-intel-2.9.1 source, and successfully ran ./configure, make, and make install, however despite seeming to work, it doesn't appear to have actually updated the driver on my system.  This is what I got while doing the above:

```
root@<compname>:/home/<myusername>/xf86-video-intel-2.9.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for bash... /bin/bash
checking if dolt supports this host... yes, replacing libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GEN4ASM... no
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for mprotect... yes
checking if XINERAMA is defined... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XF86DRI is defined... yes
checking if DPMSExtension is defined... yes
checking for XORG... yes
checking for XEXT... no
checking for ANSI C header files... (cached) yes
checking whether to include DRI support... checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for PCIACCESS... yes
checking for DRM... yes
checking for DRI... yes
checking for XVMCLIB... no
checking whether to include XvMC support... no
checking for NONE/share/sgml/X11/defs.ent... no
checking for linuxdoc... no
checking for ps2pdf... /usr/bin/ps2pdf
checking Whether to build documentation... no
checking Whether to build pdf documentation... yes
checking for sed... /bin/sed
configure: creating ./config.status
config.status: creating shave
config.status: creating shave-libtool
config.status: creating Makefile
config.status: creating uxa/Makefile
config.status: creating src/Makefile
config.status: creating src/xvmc/Makefile
config.status: creating src/xvmc/shader/Makefile
config.status: creating src/xvmc/shader/mc/Makefile
config.status: creating src/xvmc/shader/vld/Makefile
config.status: creating src/bios_reader/Makefile
config.status: creating src/ch7017/Makefile
config.status: creating src/ch7xxx/Makefile
config.status: creating src/ivch/Makefile
config.status: creating src/reg_dumper/Makefile
config.status: creating src/sil164/Makefile
config.status: creating src/tfp410/Makefile
config.status: creating man/Makefile
config.status: creating src/render_program/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
root@<compname>:/home/<myusername>/xf86-video-intel-2.9.1# make
Making all in uxa
Making all in src
Making all in xvmc
Making all in shader
Making all in mc
Making all in vld
Making all in bios_reader
Making all in ch7017
Making all in ch7xxx
Making all in ivch
Making all in sil164
Making all in tfp410
Making all in reg_dumper
Making all in render_program
Making all in man
root@<compname>:/home/<myusername>/xf86-video-intel-2.9.1# make install
Making install in uxa
Making install in src
Making install in xvmc
Making install in shader
Making install in mc
Making install in vld
Making install in bios_reader
Making install in ch7017
 /bin/bash /home/<myusername>/xf86-video-intel-2.9.1/./shave-libtool '../../doltlibtool'   --mode=install /usr/bin/install -c   ch7017.la '/usr/local/lib/xorg/modules/drivers'

Making install in ch7xxx
 /bin/bash /home/<myusername>/xf86-video-intel-2.9.1/./shave-libtool '../../doltlibtool'   --mode=install /usr/bin/install -c   ch7xxx.la '/usr/local/lib/xorg/modules/drivers'

Making install in ivch
 /bin/bash /home/<myusername>/xf86-video-intel-2.9.1/./shave-libtool '../../doltlibtool'   --mode=install /usr/bin/install -c   ivch.la '/usr/local/lib/xorg/modules/drivers'

Making install in sil164
 /bin/bash /home/<myusername>/xf86-video-intel-2.9.1/./shave-libtool '../../doltlibtool'   --mode=install /usr/bin/install -c   sil164.la '/usr/local/lib/xorg/modules/drivers'

Making install in tfp410
 /bin/bash /home/<myusername>/xf86-video-intel-2.9.1/./shave-libtool '../../doltlibtool'   --mode=install /usr/bin/install -c   tfp410.la '/usr/local/lib/xorg/modules/drivers'

Making install in reg_dumper
Making install in render_program
 /bin/bash /home/<myusername>/xf86-video-intel-2.9.1/./shave-libtool '../doltlibtool'   --mode=install /usr/bin/install -c   intel_drv.la '/usr/local/lib/xorg/modules/drivers'

Making install in man
 /usr/bin/install -c -m 644 intel.4 '/usr/local/share/man/man4'
```

Incidentally, make ran far faster than I'm used to -- a matter of seconds.  I have a feeling that I'm missing a step somewhere.  What exactly do you need to do to install the 2.9.1 driver from source (or otherwise)?

---

### Post by hugmenot on 2009-11-01
2.9.1 is in the xorg-edgers PPA.

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

```
add-apt-repository ppa:xorg-edgers/ppa
```

I would disable this repo after upgrading though. It pushes unstable snapshots regularly and sometimes things break for a while. The current snapshot works here, though.

---

### Post by Nakor BlueRider on 2009-11-01
That seems to have done it.  It's still saying that 2.9.0 is installed, but mono is fixed.  Thanks!

---

### Post by hugmenot on 2009-11-01
I don&#8217;t know why the number didn&#8217;t get bumped. But it&#8217;s even newer than 2.9.1. I guess in the master branch things don&#8217;t get tagged with release numbers. No idea.

---

### Post by Major Squirrel on 2009-11-02
> **hugmenot said:**
> 2.9.1 is in the xorg-edgers PPA.

[https://edge.launchpad.net/~xorg-edgers/+archive/ppa]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa")

```
add-apt-repository ppa:xorg-edgers/ppa
```I would disable this repo after upgrading though. It pushes unstable snapshots regularly and sometimes things break for a while. The current snapshot works here, though.


Hey how do I know if the driver is actually working? I installed 2.9.1 from intellinux and it worked I think, how do I know? I also added those lines to my repos but how do I know if it upgraded? Sorry I'm quite new to ubuntu

---

### Post by hugmenot on 2009-11-03
```
$ apt-cache policy xserver-xorg-video-intel
xserver-xorg-video-intel:
  Installed: 2:2.9.0+git20091026.10946118-0ubuntu0tormod
  Candidate: 2:2.9.0+git20091026.10946118-0ubuntu0tormod
  Version table:
 *** 2:2.9.0+git20091026.10946118-0ubuntu0tormod 0
        100 /var/lib/dpkg/status
     2:2.9.0-1ubuntu2 0
        500 http://de.archive.ubuntu.com karmic/main Packages

```

Run » apt-cache policy xserver-xorg-video-intel «. The version with tormod in the name is the up-to-date driver.

With this line you can see which module is loaded:

```
grep "LoadModule: \"intel\"" /var/log/Xorg.0.log -A5
```

---

### Post by weaver4 on 2010-01-14
I try to get this from the repository and I get this error:

sudo add-apt-repository ppa:xorg-edgers/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 165D673674A995B3E64BF0CF4F191A5A8844C542
gpg: requesting key 8844C542 from hkp server keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Can someone help!

---

### Post by hugmenot on 2010-01-14
Sounds like a simple network error. Try again?

---

