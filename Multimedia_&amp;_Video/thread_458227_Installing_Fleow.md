---
title: "Installing Fleow"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by ikkefc3 on 2007-05-29
I want to install Fleow, but if i type ./configure it says that mono misses.
Taurus said:
> **taurus said:**
> You also need the -devel of mono as well...

```
sudo aptitude install mono-devel
```

I have installed the mono-devel, but i have still te same problem:
```
I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running aclocal -I .  ...
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... configure: error: Package requirements (mono >= 1.1.13) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by Harmshi on 2008-07-20
I have the exact same issue.
Does anyone know which package to install?

---

