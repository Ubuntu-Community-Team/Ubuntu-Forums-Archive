---
title: "Building schroedinger library"
date: 2011-10-21
forum: Multimedia Software
---

### Post by dwalker0044 on 2011-10-21
Hi everyone,

I'm trying to build schroedinger-1.0.10, but I get the following error:

wavelet_2d.o:wavelet_2d.c:(.text+0x13): undefined reference to `_orc_code_orc_interleave2_s16'
wavelet_2d.o:wavelet_2d.c:(.text+0x78): undefined reference to `_orc_code_orc_deinterleave2_s16'

I have build and installed orc-0.4.16 and have added the PKG_CONFIG_PATH to point to a location where orc-0.4.pc can be found. I also added LDFLAGS to point to a directory where liborc-0.4. (a), (dll.a) and (la) exist.
 
In case its important I'm using MinGW on Windows.

Can anyone explain what the error is about?

Thanks!

---

