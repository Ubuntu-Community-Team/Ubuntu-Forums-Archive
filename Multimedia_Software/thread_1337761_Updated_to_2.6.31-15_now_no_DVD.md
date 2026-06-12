---
title: "Updated to 2.6.31-15 now no DVD"
date: 2009-11-25
forum: Multimedia Software
---

### Post by epatch0321 on 2009-11-25
I just updated to kernel 2.6.31-15 a few hours ago and now I cannot mount DVD movies.  I am able to mount CDs.  2.6.31-14 mounted DVDs just fine, and my windows partition mounts them just fine as well.

The CD/DVD Drive icon under computer:/// disappears when I insert a movie into the drive.  Reappears when I take it out.???

Any help appreciated.

---

### Post by epatch0321 on 2009-11-25
Fixed it, ran the following:
sudo /usr/share/doc/libdvdread4/install-css.sh

---

