---
title: "Is mediabuntu repository broken - i get 404 errors"
date: 2010-03-20
forum: Multimedia Software
---

### Post by juha_teuvonnen on 2010-03-20
I upgraded my friend's computer to 9.10 a couple of days ago and it worked fine. I am updating mine and it looks like mediabuntu repository is broken - I get 404s when I try to download stuff:

$ sudo aptitude install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  libdvdcss2 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.1kB of archives. After unpacking 111kB will be used.
Writing extended state information... Done
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free libdvdcss2 1.2.10-0.3medibuntu1
  404  Not Found
E: Failed to fetch [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb:](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb:) 404  Not Found

---

