---
title: "need Help compiling VLC 1.1.10"
date: 2011-07-14
forum: Multimedia Software
---

### Post by X_Splinter on 2011-07-14
Hey I running Ubuntu 10.04 and I am trying to compile VLC 1.1.10 after fulfilling all dependencies in configure part.

Now when compiling I got this:

```
	/bin/bash ./config.status --file=src/../include/vlc/libvlc_version.h
config.status: creating src/../include/vlc/libvlc_version.h
(git --git-dir="../.git/" describe --tags --long \
		--match '?.*.*' --always || echo exported) > revision.tmp
fatal: Not a git repository: '../.git/'
if diff revision.tmp revision.txt >/dev/null 2>&1; then \
	else \
		mv -f -- revision.tmp revision.txt; \
	fi 2>&1
MAKE     : .
MAKE     : test
MAKE     : libs/srtp
MAKE     : libs/unzip
MAKE     : bin
/bin/bash ../libtool  --tag=CC   --mode=link gcc -std=gnu99 `top_srcdir=".." top_builddir=".." ../vlc-config --cflags vlc` -DTOP_BUILDDIR=\"$(cd ".."; pwd)\" -DTOP_SRCDIR=\"$(cd ".."; pwd)\"  -Wall -Wextra -Wsign-compare -Wundef -Wpointer-arith -Wbad-function-cast -Wwrite-strings -Wmissing-prototypes -Wvolatile-register-var -Werror-implicit-function-declaration `top_srcdir=".." top_builddir=".." ../vlc-config --ldflags vlc` -no-install -static  -o vlc-static vlc_static-vlc.o vlc_static-override.o ../src/libvlc.la ../src/libvlccore.la `top_srcdir=".." top_builddir=".." ../vlc-config -libs vlc`  -ldl 
make: *** [all] Error 2

```

What do I need to do?

---

