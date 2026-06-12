---
title: "Error building fglrx packages - new Dapper install"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by r00tzz on 2006-12-31
Hi,

I've just installed Ubuntu Dapper.

Here's what I did:
used Ubuntu 5.10 install CD and installed SERVER, then change all the repositories to Dapper.

Ran "aptitude update && aptitude dist-upgrade && aptitude install xubuntu-desktop"

Then I get ati-driver-installer-8.32.5-x86.x86_64.run and tried:

sudo ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/dapper

But I ended with this:
```

<snipped>
dh_makeshlibs
dh_installdeb
LD_PRELOAD= dh_shlibdeps
dpkg: /usr/x86_64-linux-gnu/lib64/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libgcc_s.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXrandr.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libXrender.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libXext.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libX11.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libpthread.so.0 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libdl.so.2 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libc.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libm.so.6 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libstdc++.so.5 not found.
dpkg: /usr/x86_64-linux-gnu/lib/librt.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib/libGL.so.1 not found.
dpkg: /usr/x86_64-linux-gnu/lib64/libfglrx_gamma.so.1 not found.
dpkg-shlibdeps: failure: dpkg --search gave error exit status 1
dh_shlibdeps: command returned error code 256
make: *** [binary] Error 1
make: Leaving directory `/tmp/fglrx.8Df1Ay'
Removing temporary directory: fglrx-install
~$

```

Any help? I have installed all the packages and even used the script to install that's here in the forum: ati-8.32.5-builder.sh  

[HTML]
http://www.ubuntuforums.org/showpost.php?p=1887352&postcount=86
[/HTML]

---

### Post by r00tzz on 2007-01-01
Anybody? I've seen this error in other threads, but looks like it was 'magicaly' solved....

---

