---
title: "Mythtv Compile errors using Karmic source."
date: 2009-11-26
forum: Multimedia Software
---

### Post by dr_dred5 on 2009-11-26
Edit: This build conflicts with Build-Conflicts: libmyth-0.20-dev, libmyth-dev, libqt3-mt-dev

After removing them in Synaptic, the build worked fine.
* * * * * * * * * * * * * * * * * * * * * * * *


I'm attempting to build Mythtv from source using the Karmic Repo and I keep getting the following errors.

```
freesurround.cpp:32:21: error: qstring.h: No such file or directory
freesurround.cpp:33:23: error: qdatetime.h: No such file or directory
make[3]: *** [freesurround.o] Error 1
make[3]: Leaving directory `/usr/src/mythbuild/mythtv-0.22.0+fixes22594/libs/libmythfreesurround'
make[2]: *** [sub-libmythfreesurround] Error 2
make[2]: Leaving directory `/usr/src/mythbuild/mythtv-0.22.0+fixes22594/libs'
make[1]: *** [sub-libs] Error 2
make[1]: Leaving directory `/usr/src/mythbuild/mythtv-0.22.0+fixes22594'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

At first I thought it was because of the patches I was using, but I get the same error without using any patches.

I'm not sure if this is a dependency issue. I was able to install from the Mythtv SVN, but I prefer using the Ubuntu repo, as the plugins seem to work much better.

Here are the commands I'm using, perhaps a fresh set of eyes could point me in the right direction.

```
apt-get build-dep mythtv -y

apt-get source mythtv -y 

cd mythtv-0.22.0+fixes?????/

debuild -us -uc 
```

Thanks!

---

