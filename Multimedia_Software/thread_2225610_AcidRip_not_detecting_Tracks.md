---
title: "AcidRip not detecting Tracks"
date: 2014-05-22
forum: Multimedia Software
---

### Post by canishk on 2014-05-22
I have recently upgraded my ubuntu to 14.04. After this my acidrip is not working at all. When we are trying to rip a DVD, it only shows DVD OK and not loading any tracks. Can anyone please let me know how to solve this issue.

Contents of Acidrip.log file
===========================
AcidRip message - video_passes has been set to 2
AcidRip message - Reading DVD / file(s)... please wait
$VAR1 = {};
AcidRip message - DVD read ok
AcidRip message - Crop detection in progress... please wait
crop detect failedAcidRip message - Crop detection failed, is the DVD loaded?
AcidRip message - AcidRip 0.14, "Written" by C.Phillips <acid_kewpie@users.sf.net>
===========================

Thanks!

---

### Post by Yellow Pasque on 2014-05-22
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746163](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=746163)
[https://bugs.launchpad.net/ubuntu/+source/acidrip/+bug/1310049](https://bugs.launchpad.net/ubuntu/+source/acidrip/+bug/1310049)

---

### Post by canishk on 2014-05-23
Can you please smiply tell me how I can resolve this issue ?

---

### Post by Yellow Pasque on 2014-05-23
Build your own lsdvd using patch, wait for Ubuntu 14.10, or use a different ripper.

---

