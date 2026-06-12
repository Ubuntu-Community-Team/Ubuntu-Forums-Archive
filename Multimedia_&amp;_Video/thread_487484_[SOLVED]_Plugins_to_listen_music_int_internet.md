---
title: "[SOLVED] Plugins to listen music int internet"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by neburzaragoza on 2007-06-29
Hi

I try to listen some music in internet from websites (like [this]("http://www.culturageneral.net/Juego/Test%20de%20Musica%20Clasica/)") for give an instance) I've tried to install several things that I read in the Documentation, but it wasn't succesfully.

I've installed:

***flashplayer d'Adobe***
- flashplugin-nonfree -> ok
- msttcorefonts et gsfonts-x11-> ok

***Gnash***
- cvs libogg-dev libvorbis-dev libsdl-mixer1.2-dev libsdl1.2-dev -> ok
- gnash mozilla-plugin-gnash -> **pas marché** il ne trouve pas le paquet

***nspluginwrapper***
- le paquet :  linux32 -> ok
- les paquets : ia32-libs ia32-libs-gtk ->**pas marché** il ne trouve pas le paquets
- le paquet alien -> ok

afterwards I try with the following command and It give me back the answer below (I also show you the documents that I downloaded following the documentation)

```
xx@xx-laptop:~/nspw$ ls
nspluginwrapper-0.9.91.4-1.x86_64.rpm  nspluginwrapper-i386-0.9.91.4-1.x86_64.rpm
```

```
rumbaruben@rumbaruben-laptop:~/nspw$ sudo alien -i nspluginwrapper*.rpm
Warning: Skipping conversion of scripts in package nspluginwrapper: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/nspluginwrapper
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: ldd on `debian/nspluginwrapper/usr/lib/nspluginwrapper/x86_64/linux/npconfig' gave error exit status 1
dh_shlibdeps: command returned error code 256
make: [binary-arch] Error 1 (no tiene efecto)
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: nspluginwrapper-0.9.91.4: No existe el fichero ó directorio
```

and before finishing I also show you the response of my firefox when I ask him for my plugins with *about:plugins*

[[img]http://img440.imageshack.us/img440/4815/aboutpluginssb7.th.png[/img]](http://img440.imageshack.us/my.php?image=aboutpluginssb7.png)

any idea?

thak you all

---

### Post by neburzaragoza on 2007-06-30
Up?

---

### Post by neburzaragoza on 2007-07-22
I finally installed *media player connectivity*. It's good, work nicely and it takes care of everything, about all the multimedias in a website.

enjoy

---

