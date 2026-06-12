---
title: "From Knoppmyth to Mythbuntu without loosing LVM"
date: 2008-03-06
forum: Mythbuntu
---

### Post by mndbndr on 2008-03-06
I want to move from Knoppmyth to Mythbuntu but I have some concerns.  I currently have a 1.3TB LVM with recordings, movies, and music using about 350 GB.  The / partition is only 4.7GB (Knoppmyth's default size).

I want to increase my / partition size and keep my LVM.  Please advise on my install path.

MnDBnDr

---

### Post by uopjohnson on 2008-03-08
Is knopmyth using lvm1 or lvm2?  What file system d you have on the lvm (ext3, xfs)? Do you mean you want to shrink the lvm partition in order to grow the / partition?  The / partition on my primary backend mythbuntu install is only about 2gb the frontends are more crowded with their media so its hard to tell exactly what their size is, but someone could probably tell you what you need.  So you may not need to do this.

---

### Post by mndbndr on 2008-03-09
It is LVM2, ext3.  I was able to reenable it using vgchange -ay and adding it to fstab.  I had to install LVM2 first of course.  Thank you.

---

