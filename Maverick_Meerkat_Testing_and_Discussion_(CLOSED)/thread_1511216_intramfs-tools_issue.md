---
title: "intramfs-tools issue"
date: 2010-06-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jppr on 2010-06-16
initramfs-tools  update broke the system, I had to reinstall all system which I finished  just (amd 64)

---

### Post by taavikko on 2010-06-16
On what basis you blame this problem on initramfs?

---

### Post by yellerKat on 2010-06-16
Tweet:

> ubuntustatus WARNING: amd64 users on Maverick (10.10) should not upgrade now. We are seeing initramfs errors, which lead to broken boots.

---

### Post by jfernyhough on 2010-06-16
Oh great. Guess who just installed the initram upgrades!

I take it a downgrade would fix it?

--edit
Grr... packages.ubuntu.com doesn't seem to like maverick at the moment...

---

### Post by cariboo on 2010-06-16
initramfs-tools is held back on my system

---

### Post by MacUntu on 2010-06-16
There is no need to reinstall the whole system just because initramfs-tools killed your initrd. :confused: Just boot a live CD, download the old version of initramfs-tools, chroot in your broken system, downgrade the package, and run 'update-initramfs -c -k all'.

---

### Post by jfernyhough on 2010-06-16
Just so people know the broken version is 0.96.1ubuntu3

---

### Post by jppr on 2010-06-16
there is coming new version
[https://launchpad.net/ubuntu/maverick/+source/initramfs-tools/0.96.1ubuntu4](https://launchpad.net/ubuntu/maverick/+source/initramfs-tools/0.96.1ubuntu4)

---

### Post by cariboo on 2010-06-16
The problem doesn't affect 32-bit versions, only 64-bit.

---

### Post by tad1073 on 2010-06-16
same thing happened to me, I just reinstalled 10.04 64 bit and think I am goin to stay here for a while. too many other issues, nothing major, just cosmetic.

---

### Post by andrewthomas on 2010-06-16
They are done.
[https://launchpad.net/ubuntu/maverick/amd64/initramfs-tools/0.96.1ubuntu4](https://launchpad.net/ubuntu/maverick/amd64/initramfs-tools/0.96.1ubuntu4)
[https://launchpad.net/ubuntu/maverick/amd64/initramfs-tools-bin/0.96.1ubuntu4](https://launchpad.net/ubuntu/maverick/amd64/initramfs-tools-bin/0.96.1ubuntu4)

---

### Post by jppr on 2010-06-16
A new update came out and works fine :popcorn:

---

