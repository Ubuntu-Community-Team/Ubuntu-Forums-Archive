---
title: "Problem with mplayer"
date: 2008-08-30
forum: Multimedia Software
---

### Post by Alipacino on 2008-08-30
Hi
i'm new in linux (very new) and i use ubuntu
i've downloaded mplayer from it's own website but when i'm trying to configure it inthe end it says: Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.
where can i find them?
and if there is anything else i should download please tell me.
thanks

---

### Post by TenPlus1 on 2008-08-30
Follow this guide and add the medibunto repositories:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install mplayer using synaptic package manager and finally goto [www.getdeb.net](www.getdeb.net) and download SMPlayer for the front-end (everything works fine :)

---

### Post by Alipacino on 2008-08-31
thanks man it worked well
i know it shouldn't be here but ihave another question:
when i try to configure a software (downloader for X) iget this error:

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables

i have the same problem with some other softwares.
is there anything else i should download and install before these softwares? please help me
thanks in advance

---

### Post by shirilover on 2008-08-31
You need to install the build-essential meta-package.

---

