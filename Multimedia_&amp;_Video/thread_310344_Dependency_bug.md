---
title: "Dependency bug?"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by ked on 2006-12-01
Hi all,
I need to install the libpostproc-dev package, but I face:

The following packages have unmet dependencies:
  libpostproc-dev: Depends: libavcodec-dev (= 3:0.cvs20050918-4ubuntu1) but 3:0.cvs20050918-4ubuntu1.1 is to be installed.

Should I report this as a bug?

Cheers,
Ked

---

### Post by ciscosurfer on 2006-12-01
> **ked said:**
> Hi all,
I need to install the libpostproc-dev package, but I face:

The following packages have unmet dependencies:
  libpostproc-dev: Depends: libavcodec-dev (= 3:0.cvs20050918-4ubuntu1) but 3:0.cvs20050918-4ubuntu1.1 is to be installed.

Should I report this as a bug?

Cheers,
KedCan you downgrade libavcodec-dev 3:0.cvs20050918-4ubuntu1.1 to its previous version of libavcodec-dev 3:0.cvs20050918-4ubuntu1 ?

---

### Post by ked on 2006-12-01
I guess it's possible, but I don't know how to do it wit synaptic or apt-get. Can you help me out?
I think the package were upgraded due to security issues in Mplayer or soomething, but I never use that, so I probably could use the older version.

Cheers,
Ked

---

### Post by ciscosurfer on 2006-12-01
> **ked said:**
> I guess it's possible, but I don't know how to do it wit synaptic or apt-get. Can you help me out?
I think the package were upgraded due to security issues in Mplayer or soomething, but I never use that, so I probably could use the older version.

Cheers,
KedIf you still have the previous version, it will most likely be located under /var/cache/apt/archive(s) [I away from my Ubuntu machine at the moment and so I can't remember if it's archive or archives, try them both] and then simply search for the file and reinstall it. :D

---

### Post by ked on 2006-12-11
> **ciscosurfer said:**
> If you still have the previous version, it will most likely be located under /var/cache/apt/archive(s) [I away from my Ubuntu machine at the moment and so I can't remember if it's archive or archives, try them both] and then simply search for the file and reinstall it. :D

I found the previous version, and I'll give it a try when I get my camcorder back. Thanx for the tip

Ked

---

