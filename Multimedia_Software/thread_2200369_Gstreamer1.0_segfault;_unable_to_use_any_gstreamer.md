---
title: "Gstreamer1.0 segfault; unable to use any gstreamer applications"
date: 2014-01-18
forum: Multimedia Software
---

### Post by quequotion on 2014-01-18
I already filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1270422") for this.

No gstreamer1.0 applications are usable for me. Gstreamer itself seems to be what's broken. I can't get a full list of the installed plugins from gst-inspect-1.0, which segfaults.

The core dump produced by gst-inspect-1.0 didn't show anything useful when I ran it through gdb. I've installed, reinstalled, and tried every allowable combination of gstreamer packages according to apt, aptitude, and synaptic; no dependencies are missing and no packages are conflicting (assuming the DEPENDS and CONFLICTS flags for the gstreamer packages are correctly set).

I've tried removing the registry cache (for both gst-1.0 and gst-0.10) but it has no effect.

This is one of a great many problems I've had since upgrading to Saucy (13.10).

There are too many bugs to tell them apart.

---

