---
title: "nvidia build error when doing apt-get dist-upgrade and getting new kernel"
date: 2015-02-23
forum: Mythbuntu
---

### Post by GaryP2 on 2015-02-23
Hello – I’m wondering if anyone else is having issues with the nvidia drivers not building when doing an apt-get dist-upgrade with mythbuntu 14.04 and getting a new kernel.

About a month ago when I did an update on each of my systems (sudo apt-get update/upgrade/dist-upgrade), I noticed the error when upgrading to kernel 3.13.0-44. The error is:
> Error! Bad return status for module build on kernel: 3.13.0-44-generic (x86_64)
Consult /var/lib/dkms/nvidia-331/331.113/build/make.log for more information.
The log file is never created. My systems have been working okay since that time, but after reading problems in [this long bug report]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331-updates/+bug/1268257") (been going on over a year now), I’m nervous about doing another update. The comments in the bug report range from a simple annoyance to rendering systems unusable. 

The error happened on all three of my frontends, each reinstalled from scratch with the mythbuntu 14.04.1 ISO back in November. I’ve only done about three updates since that time and didn’t notice the DKMS nvidia driver build error right away (it may not have appeared the first couple updates, or I may simply not have seen it). Each of my frontends has different nvidia graphics.

---

