---
title: "VLC Compiling error (link error)"
date: 2010-03-10
forum: Multimedia Software
---

### Post by mononom on 2010-03-10
I tried to compile the latest VLC as the instruction of [http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119), except that giving configure option '--enable-vaapi' when compiling ffmpeg.

But, i got below error messages, and don't know what to do.

My system is as follows.
Ubuntu 9.10 Karmic Koala
Intel C2Q Q6600
Gigabyte P35-DS3R 
Geforce 8500GT 256MB
WD Raptor 36GB * 2 (RAID 0 Striped)
24" and 20" dual monitor (1920x1200 and 1600x1200 with TwinView)

```
  CCLD   libtheora_plugin.la
/usr/bin/ld: error: /usr/local/lib/libtheora.a(decapiwrapper.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(decode.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(huffdec.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(quant.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(state.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(x86state.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(encapiwrapper.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(encode.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(enquant.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(rate.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(tokenize.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(x86enc.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(analyze.o): requires unsupported dynamic reloc; recompile with -fPIC
/usr/bin/ld: error: /usr/local/lib/libtheora.a(mcenc.o): requires unsupported dynamic reloc; recompile with -fPIC

```

and, when i try to run mplayer using vd-pau, vd-pau gives an error "insufficient resource".
Is there any method that running vdpau on 256MB VRAM? I don't wanna turn off compiz.

Sorry for poor english.

---

### Post by Gyzel1989 on 2010-03-10
Are you trying to play a DVD-disk? 

If so you have to run these commands first. 

 sudo /usr/share/doc/libdvdread4/install-css.sh

And you need to download ubuntu restricted extra's 

 sudo apt-get install ubuntu-restricted-extras

Hope it helps.:D

---

### Post by mononom on 2010-03-10
> **Gyzel1989 said:**
> Are you trying to play a DVD-disk? 

If so you have to run these commands first. 

 sudo /usr/share/doc/libdvdread4/install-css.sh

And you need to download ubuntu restricted extra's 

 sudo apt-get install ubuntu-restricted-extras

Hope it helps.:D

Unfortunately, this doesn't help me...sorry.

---

### Post by mononom on 2010-03-10
Appending to the original article, 

I have tried that configure with "--with-pic" option and define CFLAGS as '-fPIC', and these two were not effective.

---

### Post by mononom on 2010-03-10
I solved it.
I ran the command for linking library as in the makefile, and it worked.
But, i dont know what causes the problem.

```

cd modules/codec
/bin/bash ../../libtool --silent --tag=CC   --mode=link gcc -std=gnu99 `top_srcdir="../.." top_builddir="../.." ../../vlc-config --cflags plugin libtheora_plugin.la` -fPIC -Wall -Wextra -Wsign-compare -Wundef -Wpointer-arith -Wbad-function-cast -Wwrite-strings -Wmissing-prototypes -Wvolatile-register-var -Werror-implicit-function-declaration -rpath '/usr/local/lib/vlc/plugins/codec' -avoid-version -module -export-symbol-regex ^vlc_entry -shrext .so -rpath "/usr/local/lib/vlc/plugins/codec" -no-undefined `top_srcdir="../.." top_builddir="../.." ../../vlc-config --ldflags plugin libtheora_plugin.la`  -o libtheora_plugin.la  libtheora_plugin_la-theora.lo  `top_srcdir="../.." top_builddir="../.." ../../vlc-config -libs plugin libtheora_plugin.la` ../../src/libvlccore.la ../../compat/libcompat.la

```

---

### Post by andrew.46 on 2010-03-10
Hi mononom,

Is this a copy of theora that you have compiled yourself (the location of the file certainly hints at this)? If so could you mention which version of theora you have installed and are you running 64 bit or 32? There should be a neater solution I suspect... BTW feel free to post problems with compiling vlc-git in that guide you mentioned, there are several keen vlc users who would jump at the opportunity to help out :).

All the best,

Andrew

---

