---
title: "Davfs webdav speed work-around with Nautilus"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by gylf on 2008-12-20
I have a webdav drive I need mounted and cannot use Nautilus because there is a "@" sign in both the URI and username (using %40 for the @ does not work, this is a known bug).  So I installed davfs2 and added the necessary line to my fstab (there are other posts on this in these forums) and I'm able to access my webdav share.

However, the drive was REALLY slow.  I tried installing Pcman, but same speed issues.  I optimized the davfs configuration file for gui usage, still very slow.

Long story short, I realized putting the mount point outside my home directory solves speed problem.  I had mounted the drive to a folder in my home directory.  Nautilus saw it and of course listed it on the desktop as a mounted drive.  Noticeably, placing the mount point outside my home directory prevents Gnome (Nautilus?) from placing a "drive" icon on my desktop.

Hopefully the above work around helps someone with similar speed problems using webdav.  Anyone happen to know what is causing this behavior?

---

