---
title: "nVidia TwinView - Black Bar on Right Side of one Monitor"
date: 2007-01-19
forum: Multimedia &amp; Video
---

### Post by Redth on 2007-01-19
Ok,

I finally switched over to ubuntu (6.10) as my desktop OS..  I had been running Vista for awhile until it was not 'genuine' long enough that it actually stopped me from logging in.  That was the last straw (plus VMWare has a new version out that looks real nice, and virtualization is getting a whole lot better from here on in).

Anyways, I've got dual monitors and have had twinview setup and it works almost 100%, however one of my LCD's (Benq FP931) has problems when I plug it in over D-Sub (it works fine with DVI).  From my research, I've narrowed it down that the nvidia-glx driver is not getting the EDID from the monitor properly.  I've tried setting the UserEDID Option to "false" in my xorg.conf, but that causes twinview to stop working, and i'm stuck with one monitor (although it does fix the black bar).

Any ideas how I can get this to work properly?  I need to use D-Sub instead of DVI because I have a KVM Switch hooked up to that monitor.

Appreciate the help!

---

