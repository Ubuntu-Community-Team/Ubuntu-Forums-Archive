---
title: "Installing and using Handbrake on Ubuntu 10.04"
date: 2011-05-30
forum: Multimedia Software
---

### Post by imjakes on 2011-05-30
Hi,

I have tryed to find at tutorial on how to install Handbrake on Unbutu 10.04 command lin server, but cant find one??

I hav found the documantation on how to use it using commandlind here:
[https://trac.handbrake.fr/wiki/CLIGuide](https://trac.handbrake.fr/wiki/CLIGuide)

Hope someone can help me make a guide how to install it

Regards,
Jacob

---

### Post by BicyclerBoy on 2011-05-30
Just use you're man's ppa..

[http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu)

If you have to build it from source then the instructions will be with the source code..

---

### Post by handy on 2011-05-30
[http://www.jonathanmoeller.com/screed/?p=2991](http://www.jonathanmoeller.com/screed/?p=2991)

---

### Post by BicyclerBoy on 2011-05-30
The nightly builds from Mr Stebbin's ppa work just fine on 11.04 & 10.04, contrary to some of the comments on the previous post's link..

The best info about using 3rd party ppas is to be found in the Ubuntu website.
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by imjakes on 2011-05-30
Hi,

Thanks for the advises i found a install guide her:
[http://r3dux.org/2010/05/how-to-build-a-working-version-of-handbrake-for-ubuntu-10-04/](http://r3dux.org/2010/05/how-to-build-a-working-version-of-handbrake-for-ubuntu-10-04/)

But now i get these errors:

```

make[3]: *** [libmpeg2arch_la-idct_mmx.lo] Error 1
make[3]: Leaving catalog '/home/handbrake/hb-trunk/build/contrib/mpeg2dec/mpeg2dec/libmpeg2'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving catalog '/home/handbrake/hb-trunk/build/contrib/mpeg2dec/mpeg2dec/libmpeg2'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving catalog '/home/handbrake/hb-trunk/build/contrib/mpeg2dec/mpeg2dec'
make: *** [contrib/mpeg2dec/.stamp.build] Error 2

```

Any ideas?

Regards,
Jacob

---

### Post by BicyclerBoy on 2011-05-31
Yes, follow my advice and use the pre-compiled binaries in the ppa.

Once you have something working then try DIY builds..

---

### Post by Cpierce on 2011-05-31
I just install the getdeb package from here:

[http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install)

update; then open your software center and you will have two Handbrake to chose from; the cli version and the GUI version. I would recommend the GUI.

If they don't show up the first time, update and reboot.

---

