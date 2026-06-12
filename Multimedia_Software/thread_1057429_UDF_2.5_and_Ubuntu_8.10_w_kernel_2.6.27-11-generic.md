---
title: "UDF 2.5 and Ubuntu 8.10 w/ kernel 2.6.27-11-generic"
date: 2009-02-01
forum: Multimedia Software
---

### Post by CyrusComputers on 2009-02-01
I have several people who have started giving me disks burnt with Windows Vista and the UDF 2.5 file system. Some searching as found that this is not compatible with Ubuntu 8.10 (kernel 2.6.27-11-generic). I have found the Linux-UDF project at [http://sourceforge.net/projects/linux-udf](http://sourceforge.net/projects/linux-udf) but I do not know how to compile a kernel. When will that project be merged into the main Ubuntu kernel, or at least added into the repositories so that I could install it. (If someone want to walk me through compiling my own kernel, I'm also up for that.) Thanks for any help I can get!

---

### Post by mc4man on 2009-02-02
8.10 does support up to UDF 2.5, just not the vista 'live system'. I'm pretty sure what your linking to will be of no added value. There is a patch and or compiled module available for hardy 2.6.24-xx that does enable support both UDF 2.5 and vista live system disks.

I haven't seen any patches for > 2.6.25, though that doesn't mean there isn't.


Here's a page for info that shows how the orig. UDF patch needed add. for the vista live system format.
[http://sourceforge.net/tracker/index.php?func=detail&aid=1882910&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1882910&group_id=295&atid=300295)

In lieu of a 2.6.27 solution you could ask your friends to format the disks with the 'mastered' format

---

### Post by CyrusComputers on 2009-02-03
Ok, thanks for the info. Do you know if support for the Vista "live system" disks will be added any time soon?

---

