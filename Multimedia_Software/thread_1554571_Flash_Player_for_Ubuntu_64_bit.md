---
title: "Flash Player for Ubuntu 64 bit"
date: 2010-08-16
forum: Multimedia Software
---

### Post by elwayisgod on 2010-08-16
Hi,

When I goto install Flash Player, I choose the APT for Ubuntu 9.04+.  It downloads and then this message appears...

Package 'adobe-flashplugin' is virtual.

Flash is still not working.. Any ideas?  I do have the 'libflashplayer.so' file on my desktop.  However if I try and move it to the 'usr->lib64->mozilla->plugins' folder I get permission denied...

Stumped...

---

### Post by TheKid965 on 2010-08-17
Try moving it into your ~/.mozilla/plugins directory (create it, if it doesn't exist), restart Firefox, and see if that makes a difference.

---

