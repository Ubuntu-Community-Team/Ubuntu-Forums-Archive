---
title: "Compiling wired, gtk error"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by kapetanski on 2006-06-11
When compiling wired-libs-0.2 I got this error: 
```
checking for GTK+ version...
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent
```

Seems strange to me, or do I have to compile gtk from source?

---

### Post by Sanne on 2006-06-11
Hi,

I don't know your level of knowledge, so I may make too much words. If so, please forgive me.

This: > checking for GTK+ - version >= 2.0.0... no
and this: > The development files for GTK+ were not found. For GTK+ 2, please ensure that pkg-config is in the path and that gtk+-2.0.pc is installed. 
would tell me to look for GTK+2 development files, that are not installed in Ubuntu by default. Usually they are called something like <libname>-dev. To find out the exact name of the package you need to install, it is best to look for some filename that is not found and search from there. Here's how:

We see that the output complained about the file gtk+-2.0.pc not being there. So we  go to [packages.ubuntu.com]("http://packages.ubuntu.com") and go find the section "Search the contents of packages". Put the filename "gtk+-2.0.pc" into the search box, set the options to match your distro, and search.

The result page that tells us the package name is libgtk2.0-dev. Voila! :)

So install this package with the package manager of your choice and try to compile again. If you get other configure errors, repeat this procedure.

Good luck, Sanne

---

