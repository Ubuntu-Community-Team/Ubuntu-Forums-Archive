---
title: "problem building mythbuntu packages with custom patch"
date: 2009-12-13
forum: Mythbuntu
---

### Post by tube013 on 2009-12-13
I'm trying to rebuild the mythbuntu mythtv packages with a custom patch (which fixes a/v sync from one of my channels)

This is what I've done.

apt-get build-dep mythtv
apt-get install devscripts
apt-get source mythtv

I copied the patch into the debian/patches folder, and added it to the 00list file.

dch -i (filled in information)
debuild  (I can see the patch is correctly applied in messages before the configure is run)

But I keep running into this error one every attempt to compile (both on a karmic and a jaunty install).

```
sh \"/home/byron/build/deb-build/mythtv-0.22.0+fixes22957/version.sh\" \"/home/byron/build/deb-build/mythtv-0.22.0+fixes22957\" \"": http://svn.mythtv.org/svn/branches/release-0-22-fixes/mythtv/version.pro "\"
sh: Can't open "/home/byron/build/deb-build/mythtv-0.22.0+fixes22957/version.sh"

```

any help is appreciated.

Thanks.

---

### Post by tube013 on 2009-12-13
Well the error above actually occurs only after my first attempt at building...

on a fresh go here's the build output:  [http://pastebin.com/f75c64673](http://pastebin.com/f75c64673)

seems the first errors are:

```
ccache gcc -c -pipe -g -march=i686 -fomit-frame-pointer -O3 -DNDEBUG -g -O2 -D_ISOC99_SOURCE -D_POSIX_C_SOURCE=200112 -std=c99 -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -pthread -g -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -Wcast-qual -Wwrite-strings -Wtype-limits -Wundef -fno-math-errno -fno-signed-zeros -fPIC -DPIC -w -D_REENTRANT  -DMMX -Di386 -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -I/usr/share/qt3/mkspecs/default -I. -I. -I../.. -Idvdnav -I../libmythdb -o dvd_input.o dvdread/dvd_input.c
make[3]: *** [freesurround.o] Error 1
make[3]: Leaving directory `/home/byron/build/deb-build/mythtv-0.22.0+fixes22957/libs/libmythfreesurround'
make[2]: *** [sub-libmythfreesurround] Error 2
make[2]: *** Waiting for unfinished jobs....

```

---

### Post by mxander on 2010-01-10
I've tried to apply a patch to solve the issue described in the ticket 7515:
"SRT subtitle timings wildly variable"
[http://svn.mythtv.org/trac/ticket/7515](http://svn.mythtv.org/trac/ticket/7515)

Tried to follow the instructions on this page:
"[Newbie/8.04]Mythstream, Mythbrowser, Howto apply patches?"
[http://ubuntuforums.org/showthread.php?t=758593](http://ubuntuforums.org/showthread.php?t=758593)
But I cannot manage to follow the first step of their Howto:


sudo apt-get build-dep mythtv
[sudo] password for MyUserName: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages have unmet dependencies:
nvidia-185-libvdpau-dev: Depends: nvidia-185-libvdpau (>= 185.18.36) but it is not going to be installed
E: Build-dependencies for mythtv could not be satisfied.

Can you help me?

---

### Post by Neon Dusk on 2010-01-11
It looks like you're using the mythbuntu auto-builds repo but don't have the source code repo added. As a result 'sudo apt-get build-dep mythtv' is trying to install the dependencies for the version of mythtv that came with 9.10

To fix it I think you need to manually add a 'deb-src' apt line to your software sources that matches the existing auto builds line.

---

### Post by mxander on 2010-01-12
I'll check my sources.list tonight.
Thanks a lot

---

### Post by mxander on 2010-01-16
You're right.
Where can I find the repository to add to my sources.list ?

---

### Post by Neon Dusk on 2010-01-16
It looks like the mythbuntu repos are listed in /etc/apt/source.list.d/mythbuntu-repos.list not sources.list

If you're using the 0.22 fixes auto-builds from ppa you should have 
```

deb http://ppa.launchpad.net/mythbuntu/trunk-0.22/ubuntu karmic main

```

so you just need to add
```

deb-src http://ppa.launchpad.net/mythbuntu/trunk-0.22/ubuntu karmic main

```

I did it through the gui so the deb-src line did end up in sources.list

---

### Post by mxander on 2010-01-18
I've activated it in [http://mythbuntu.org/auto-builds](http://mythbuntu.org/auto-builds) clicking in "Activate Auto Builds".
I'll add the line manually. If it doesn't work tha way I'll use the "Mythbuntu Control Center" to disable and then re-enable it.
Thanks a lot

---

