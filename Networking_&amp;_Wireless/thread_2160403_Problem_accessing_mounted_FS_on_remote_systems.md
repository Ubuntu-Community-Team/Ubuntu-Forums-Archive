---
title: "Problem accessing mounted FS on remote systems"
date: 2013-07-06
forum: Networking &amp; Wireless
---

### Post by cjsmall on 2013-07-06
Ubuntu 12.10 64-bit
Asus U56E System
Gnome 3.6.0
Nautilus 3.4.2

I have a Solaris 10 system  which performs a normal read/write mount of a disk onto /v and another disk onto /x.   I have a few symbolic links located on the root disk (/) and on the /v disk which point to directory hierarchies located on /x.

For example, I have a Nautilus "bookmark" to  /u/jeff/lib/images on the remote Solaris system which contains image files.  All the local files under that directory can be accessed.  Within that directory is a symbolic link to a directory located on the /x disk which contains additional image files.  However, Nautilus does not show that symbolic link and will not access that remote directory.

I have another "bookmark" to the root of the Solaris filesystem and I can get nautilus to step down into /x and see the remainder of the images.  Even when the root remote mount is active, Nautilus refuses to display the symlink under /u/jeff/lib/image.

 I only have one Solaris system at the moment, but when I administered multiple networked systems I never ran into this problem.  Is this a hard limitation of Linux or is there some sort of work-around that will allow Ubuntu/Nautilus to properly navigate these cross-file-system symbolic links?

Thanks.

---

