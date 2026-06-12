---
title: "No ethernet connection"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by NCLI on 2010-05-20
I recently installed a new CPU and motherboard in my Media Server, but the ethernet port isn't showing up under ifconfig. Is there any way to install additional drivers?

EDIT: The model is Realtek RTL8111/8160B.

---

### Post by NCLI on 2010-05-21
Bump.

---

### Post by Iowan on 2010-05-21
**ifconfig -a** *might* reveal more information... but **sudo lshw -C network** would be better yet.

---

### Post by NCLI on 2010-05-21
I ended up reinstalling, works now. I'll try your advice if it screws up again though.

---

