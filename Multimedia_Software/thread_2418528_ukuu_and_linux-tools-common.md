---
title: "ukuu and linux-tools-common"
date: 2019-05-07
forum: Multimedia Software
---

### Post by ttoommxx on 2019-05-07
Dear all,
I would like to install ukuu and update the kernel of my laptop, but I would also like to keep linux-tools-common installed on my laptop. I searched in the linux mainline website, where the kernels are, but there is no version of linux-tools-common for no kernel there. What I am afraid of is that on the ubuntu repository there's only those version relative to the maintained kernels, such as 4.15 and 4.18. Has anybody tried to install it after installing a kernel from ukuu which is not from any distro? (say 4.19)

---

### Post by dino99 on 2019-05-08
linux-tools-common is a dependency of several kernels (aws, kvm, osp, ...) and is found into the archive.

---

