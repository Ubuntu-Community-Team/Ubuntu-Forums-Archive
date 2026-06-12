---
title: "Wings3D modeller is slow - Ubuntu specific problem"
date: 2007-06-06
forum: Multimedia Production
---

### Post by deadcabbit on 2007-06-06
Wings is a polygon modeller tool which I really like - unfortunately its 3d performace is horrible on Ubuntu. Fine on Windows and other distros (got Gentoo and Arch), but on Ubuntu higher resolution meshes slows things down terribly (there is a strong visible lag on mouseover selection/vertex highlight) - can anyone help me with this?

Using Nvidia drivers (tried both restricted and original from nvidia site) on a pci-ex Geforce 7200; also tried messing around with xorg.conf nvidia params, but no use. Any ideas?

EDIT:
I did not purge the old nvidia-glx before adding the original driver - 
just apt-get remove nvidia glx, use envy to install the newest driver and there you go.

---

