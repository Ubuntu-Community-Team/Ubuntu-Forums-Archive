---
title: "How to Install ATI driver?"
date: 2009-05-17
forum: Multimedia Software
---

### Post by lilychef on 2009-05-17
Once again, I remain new to Ubuntu....  Can anybody tell me how to install this ATI driver from a grub command prompt after I download it?  I can't boot into Ubuntu because my new (old) ATI X1300 video card won't work....  I realize this may be simple stuff, but I'm still learning how to use Linux command prompt language..... I learned on DOS in the late 80's, but that only helps me with Windows... ha!  Here's the link to see what I'm talking about:

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English)

---

### Post by ssri on 2009-05-18
Sorry, but your card is not supported by Catalyst 9.4+, versions that can install in jaunty.  Jaunty uses xserver 1.6 and Catalyst versions 9.4 and above are the only versions you can use in Jaunty.  If you want 9.3 installed, then you have to go back to Intrepid.  Otherwise, you have to go with the opensource drivers in Jaunty: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

