---
title: "gnome-mplayer installation - what happened?"
date: 2012-05-30
forum: Multimedia Software
---

### Post by hakamade on 2012-05-30
Hello

I was attempting to compile and install latest gnome-mplayer (version 1.0.6). Once I got it compiled and installed, it wouldn't run with an error message:

> gnome-mplayer: error while loading shared libraries: libgmlib.so.0: cannot open shared object file: No such file or directoryI didn't manage to figure this out, so I installed gnome-mplayer from the repositories (version 1.0.5). After installation, it started up OK, and the about dialog says its version is 1.0.6!?

I was just wondering what happened here... what version of gnome-mplayer do I have or is it somehow a hybrid of two versions?

--hakamade

---

### Post by mc4man on 2012-05-30
gnome-mplayer 1.0.5 & 1.0.6 will probably both run using the 1.0.5 or 1.0.6 versions of libgmlib0 & libgmtk0 shared libs

But the 1.0.6 source should not of built or even passed a configure without the  1.0.6 versions of those libraries & headers

So what did you do in that regard?

It's likely now you are using the 1.0.6 version with the 1.0.5 .so's that were installed when you installed the repo gnome-mplayer

If you used the default config in the build then it would have installed to /usr/local/bin

run
```
which gnome-mplayer
```

---

### Post by hakamade on 2012-06-02
Thanks for your reply

Here's the guide I used for compiling gnome-mplayer:
[http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/](http://eosvision.wordpress.com/2011/06/13/gnome-mplayer-compile-guide/)

```
which gnome-mplayer
``` shows /usr/local/bin/gnome-mplayer
Running that, gnome-mplayer says version 1.0.6, and after it stops there's a message "in media state change with state = 1".

There's another gnome-mplayer in /usr/bin/, which says version 1.0.5. It runs without the state message.

How do I get gnome-mplayer to use the newer libs?

---

### Post by mc4man on 2012-06-02
What release of Ubuntu are you using? 

If you still have your build folder for gnome-mplayer could you open it up.
Directly inside is a file "config.log", open it up in a text editor, search GM & post the sections. Ex. in screen.

Or right click on "config.log" > compress, choose .gz. Compress and then attach "config.log.gz" to a post

---

### Post by hakamade on 2012-06-09
I've got Ubuntu 12.04.

I didn't have the build folder anymore, but I downloaded the gnome-mplayer tar and retried configure. Here's the "gm" parts from config.log:

> configure:6989: checking for gmsgfmt
configure:8538: checking for GMLIB
configure:8545: $PKG_CONFIG --exists --print-errors "gmlib >= 1.0.6"
configure:8548: $? = 0
configure:8561: $PKG_CONFIG --exists --print-errors "gmlib >= 1.0.6"
configure:8564: $? = 0
configure:8623: result: yes
configure:8632: checking for GMTK
configure:8639: $PKG_CONFIG --exists --print-errors "gmtk >= 1.0.6"
configure:8642: $? = 0
configure:8655: $PKG_CONFIG --exists --print-errors "gmtk >= 1.0.6"
configure:8658: $? = 0
configure:8717: result: yes
configure:9717: gmlib is using gsettings for preference storage
ac_cv_env_GMLIB_CFLAGS_set=
ac_cv_env_GMLIB_CFLAGS_value=
ac_cv_env_GMLIB_LIBS_set=
ac_cv_env_GMLIB_LIBS_value=
ac_cv_env_GMTK_CFLAGS_set=
ac_cv_env_GMTK_CFLAGS_value=
ac_cv_env_GMTK_LIBS_set=
ac_cv_env_GMTK_LIBS_value=
ac_cv_path_GMSGFMT=/usr/bin/msgfmt
pkg_cv_GMLIB_CFLAGS='-I/usr/local/include/gmtk  '
pkg_cv_GMLIB_LIBS='-L/usr/local/lib -lgmlib  '
pkg_cv_GMTK_CFLAGS='-I/usr/local/include/gmtk  '
pkg_cv_GMTK_LIBS='-L/usr/local/lib -lgmtk  '
CATALOGS=' ar.gmo bg.gmo ca.gmo cs.gmo da.gmo de.gmo el.gmo en_GB.gmo es.gmo et.gmo eu.gmo fi.gmo fo.gmo fr.gmo fy.gmo gl.gmo he.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo kk.gmo ko.gmo lt.gmo nl.gmo pl.gmo pt.gmo pt_BR.gmo ro.gmo ru.gmo si.gmo sr.gmo [EMAIL="sr@latin.gmo"]sr@latin.gmo[/EMAIL] sv.gmo th.gmo tr.gmo ug.gmo uk.gmo vi.gmo zh_CN.gmo zh_HK.gmo zh_TW.gmo'
CATOBJEXT='.gmo'
GMLIB_CFLAGS='-I/usr/local/include/gmtk  '
GMLIB_LIBS='-L/usr/local/lib -lgmlib  '
GMOFILES=' ar.gmo bg.gmo ca.gmo cs.gmo da.gmo de.gmo el.gmo en_GB.gmo es.gmo et.gmo eu.gmo fi.gmo fo.gmo fr.gmo fy.gmo gl.gmo he.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo kk.gmo ko.gmo lt.gmo nl.gmo pl.gmo pt.gmo pt_BR.gmo ro.gmo ru.gmo si.gmo sr.gmo [EMAIL="sr@latin.gmo"]sr@latin.gmo[/EMAIL] sv.gmo th.gmo tr.gmo ug.gmo uk.gmo vi.gmo zh_CN.gmo zh_HK.gmo zh_TW.gmo'
GMSGFMT='/usr/bin/msgfmt'
GMTK_CFLAGS='-I/usr/local/include/gmtk  '
GMTK_LIBS='-L/usr/local/lib -lgmtk  '

---

### Post by mc4man on 2012-06-09
Did ask you orig. how you provided libgm* 1.0.6, anyway you are probably now using the libgm* libs you put in /usr/local/* (1.0.6) & could go ahead & remove gnome-mplayer 1.0.5, ect.

If in fact you built  the gmtk-1.0.6 source, after installing you need to run  a ldconfig, (sudo ldconfig), so what likely happened was when you installed the repo packaged gnome-mplayer a ldconfig was run & then your built version was able to find the /usr/local/ ones

So while not always needed it doesn't hurt  whenever building & installing with either sudo make install or sudo checkinstall to run a sudo ldconfig afterwards

Assuming your gnome-mplayer build was installed to /usr/local & you haven't removed the gmtk libs from /usr/local/ then you could confirm with this, should return a location of /usr/local/.. for libgmlib.so.0 & libgmtk.so.0

```
ldd /usr/local/bin/gnome-mplayer |grep libgm
```

---

### Post by hakamade on 2012-06-10
That shows:

> libgmlib.so.0 => /usr/local/lib/libgmlib.so.0 (0x00007fcf03570000)
libgmtk.so.0 => /usr/local/lib/libgmtk.so.0 (0x00007fcf03358000)
libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fcf01dd0000)I'm not sure what to make of that, but I guess this means gnome-mplayer is using the libraries in /usr/local? I got the versions of gmtk and gmlib off pkg-config, they're reading as 1.0.6, and I don't find any duplicate gmtk or gmlib outside /usr/local. I also uninstalled gnome-mplayer 1.0.5 and 1.0.6 is still working all right. The issue's solved, I suppose.

---

### Post by mc4man on 2012-06-10
everything's fine  - 
In the future if you build a source that builds & installs ok but then produces a 'error while loading shared libraries ....', try running 
```
sudo ldconfig
```

That will resolve the issue in many cases
(or as I mentioned just run that command after any build & install, can't hurt, sometimes is needed

---

### Post by hakamade on 2012-06-11
Thanks, I'll have to remember that. Especially since I also got the shared libraries error with smplayer. I built and installed both according to online guides and neither had any mention of ldconfig.

---

