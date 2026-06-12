---
title: "VIA DeltaChrome Graphics K8M890CE"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by maubp on 2006-08-21
I've been looking at buying Shuttle's new AM2 socket budget machine, the [SK22G2](http://eu.shuttle.com/en/DesktopDefault.aspx/tabid-72/170_read-13232/).

It has on board graphics with this integrated graphics controller:

VIA DeltaChrome 128-bit 2D/3D graphics engine
DirectX 9.0 compliant, shared Memory max. 256 MB

According to the Shuttle specification's PDF,

VIA K8M890CE / VT8237R+
Integrated VIA DeltaChrome Graphics

**Does anyone know what the status of the DeltaChrome  drivers is in Ubuntu?**

VIA does seem to have some linux drivers available for some distributions, and a [source driver](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=164).

I had a look at the ReleaseNotes.txt file from k8m890xf40069-kernel-src_20060620.tgz and it said:

*This document describes how to compile the VIA DeltaChrome family Linux display driver source code on Fedora Core Linux 4, Mandriva Linux 2006.0 and SuSE Linux 10.0.  This software package supports 2D and TV-Out. ...*

The ReleaseNotes.txt from k8m800_890-p4m890xf41068-kernel-src_20060707.tgz says:

*This document describes how to compile the VIA UniChrome/DeltaChrome family Linux display driver source code on Fedora Core Linux 4 (x86_64). This software package supports 2D, TV-Out, hardware video mpeg2(K8M800) and hardware video overlay. ...*

Sounds like no 3D effects for now :(

---

