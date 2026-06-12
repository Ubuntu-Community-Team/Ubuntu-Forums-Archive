---
title: "Issues with Kernel 2.6.38-x and BCM4328 Wireless card on Lucid."
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by TuxIsAwesome on 2011-02-23
Hello, I am having some issues getting the broadcom sta driver installed on Kernels 2.6.36 up through 2.6.38.

Before I continue, I'll list my specs
Release: Xubuntu 10.04.2 LTS (64-Bit)
Wireless Card: Broadcom BCM4328
Kernel: 2.6.38-x (Any version), and 2.6.36 and above

EDIT:

Yes! Yes! I got it to work, for those that are having issues, install this packages. Disregard that it says that there is an older version available in a software. The bcmwl-kernel-source for Natty works on Lucid!

64-Bit: [http://launchpadlibrarian.net/62008106/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_amd64.deb](http://launchpadlibrarian.net/62008106/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_amd64.deb)

32-Bit: [http://launchpadlibrarian.net/62008128/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_i386.deb](http://launchpadlibrarian.net/62008128/bcmwl-kernel-source_5.100.82.38%2Bbdcom-0ubuntu2_i386.deb) 

Install one of these and check your Hardware Drivers, they will probably say that the Broadcom STA driver is installed but not in use. If you then proceed to restart it should be up and running, this way you can use kernels 2.6.36+ and still use the Broadcom STA driver!

Can an Administrator change this to Solved

---

### Post by Cenoforums on 2011-04-03
Get the latest bcmwl-kernel-source package from natty... great idea!

I upgrade my kernel to 26.38 from the kernel team ppa, and naturally, the bcmwl package from the reps stopped working. This works, thank you so much for doing a follow up edit!

---

