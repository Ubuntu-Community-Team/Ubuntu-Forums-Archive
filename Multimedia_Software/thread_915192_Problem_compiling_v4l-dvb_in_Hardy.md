---
title: "Problem compiling v4l-dvb in Hardy"
date: 2008-09-09
forum: Multimedia Software
---

### Post by nolodude on 2008-09-09
Hi there, I'm running Ubuntu 8.04.1 server and I'm trying to compile DVB drivers taken from mercurial. I have been able to compile them in earlier versions of Ubuntu.

So this is what I did:
```

cd /usr/src
hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb
make all
```
And this is what I get:
```
make -C /usr/src/v4l-dvb/v4l all
make[1]: Entering directory `/usr/src/v4l-dvb/v4l'
No version yet, using 2.6.24-16-server
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make[1]: Entering directory `/usr/src/v4l-dvb/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.24
File not found: /lib/modules/2.6.24-16-server/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make[1]: Entering directory `/usr/src/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.24
File not found: /lib/modules/2.6.24-16-server/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/usr/src/v4l-dvb/v4l'
make: *** [all] Error 2
```

I don't understand why there is no /lib/modules/2.6.24-16-server/build/.config file. I have installed linux-headers-2.6.24-16, linux-headers-2.6.24-16-server and linux-source-2.6.24.

Any ideas?

---

### Post by Tinbuctu on 2008-09-22
I have the same problem for a genistech x8000 hdtv card. If you 
make kernel-links
 while in root it will make build folder but not .config file.

---

### Post by Tinbuctu on 2008-09-22
I have the same problem for a genistech x8000 hdtv card. If you 
make kernel-links
 while in root it will make build folder but not .config file.

---

