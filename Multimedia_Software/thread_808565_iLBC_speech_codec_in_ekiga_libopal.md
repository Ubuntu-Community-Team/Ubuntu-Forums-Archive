---
title: "iLBC speech codec in ekiga libopal"
date: 2008-05-26
forum: Multimedia Software
---

### Post by montun on 2008-05-26
I did the following to enable [iLBC]("http://www.ilbcfreeware.org/") in the libopal libary used in the sip softphone ekiga.

Is anyone having any experience using the iLBC codec with sip to fixed/mobile phones?
 
```

#!/bin/sh

mkdir  -p  ~/tmp/opal
cd ~/tmp/opal

# Get build tools and buid dependenies
sudo apt-get install fakeroot build-essential 
sudo apt-get build-dep libopal-2.2

# Get the liopal source
apt-get source libopal-2.2

# Modify the source to not remove support for iLBC
cd opal-2.2.11~dfsg1/debian
patch -p1 <<"EOF"
--- debian.orig/patches/00list	2008-05-26 21:30:30.000000000 +0200
+++ debian/patches/00list	2008-05-26 21:30:44.986321791 +0200
@@ -1,4 +1,3 @@
 libname
 notrace
-remove_ilbc
 speexcodec
diff -ruN debian.orig/rules debian/rules
--- debian.orig/rules	2008-05-26 21:30:30.000000000 +0200
+++ debian/rules	2008-05-26 21:31:04.506322886 +0200
@@ -125,11 +125,11 @@
 	$(MAKE) $(MAKE_BUILD_PARAM) docs
 	touch build-indep-stamp
 
-clean: check-ilbc clean-patched unpatch
+clean: clean-patched unpatch
 clean-patched:
 	dh_testdir
 	dh_testroot
-	rm -f build-arch-stamp build-indep-stamp patch-stamp check-ilbc
+	rm -f build-arch-stamp build-indep-stamp patch-stamp
 	rm -f config.status config.log autotools
 	if [ -f Makefile ];then \
 		$(MAKE) $(MAKE_BUILD_PARAM) optclean debugclean clean;\
EOF

cd ..

# Get the sourcode for iLBC
mkdir src/codec/iLBC
cd src/codec/iLBC
wget http://www.ietf.org/rfc/rfc3951.txt
wget http://www.ilbcfreeware.org/documentation/extract-cfile.awk
awk -f extract-cfile.awk  rfc3951.txt 
cd -

# Build new binary libopal package
export CXXFLAGS="-march=pentium-m -O2 -pipe -fomit-frame-pointer"
export CFLAGS="${CXXFLAGS}"
export FFLAGS="${CXXFLAGS}"
dpkg-buildpackage -us -uc -b
sudo dpkg -i ../libopal-2.2_2.2.*dfsg*-*ubuntu*_i386.deb
sudo apt-get install ekiga

```

---

