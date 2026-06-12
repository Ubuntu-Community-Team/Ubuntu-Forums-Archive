---
title: "NFS /exports file"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-03-22
Currently I have an export such as 192.168.2.0/24(something), and I'm also needing to have another network have access.  So I added this to exports:

/mydir 192.168.2.0/24(something) 192.168.5.0/24(something)

Can I re-write that as:

/midir 192.168.0.0/16(something)

Would this work as well?

---

### Post by SeijiSensei on 2012-03-22
Yes.

---

