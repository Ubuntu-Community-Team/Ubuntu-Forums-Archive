---
title: "Some radeon firmware files missing - low resolution problem"
date: 2013-09-09
forum: Multimedia Software
---

### Post by jack_walker on 2013-09-09
I have a MSI HD6870 video card and I'm using open source drivers. I have upgraded from kernel 3.8 to 3.11.0-031100 stable. 


  After reboot I had low resolution problem, that is my maximum  resolution is 1920x1080 but I can set and see only 1280x1024 as maximum  resolution.
  I already had solved this problem removing the nomodeset option from /etc/default/grub  when using kernel 3.8. So I decided to install kernel 3.11 and the low  resolution problem came back. It's strange because the grub still has no  nomodeset option now.

  I noticed that I have some radeon firmware files missing in kernel 3.11 that in kernel 3.8 was not, therefore I found this bug [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1183777](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1183777).
  They say that it has been solved with linux-firmware package v1.113 but I have linux-firmware 1.106 so maybe it's due to kernel 3.11 has been released for ubuntu 13.10 and I have 13.04, 
  so how can I solve this firmware files missing?


  I'm assuming that the radeon firmware files missing is related to my  resolution problem, but I'm not sure so please tell me if I'm wrong, if  so how can I solve the resolution problem?


  Thanks

---

