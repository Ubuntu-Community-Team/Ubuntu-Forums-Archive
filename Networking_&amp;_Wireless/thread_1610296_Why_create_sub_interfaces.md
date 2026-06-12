---
title: "Why create sub interfaces"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by acontibun on 2010-10-31
Hello,

What is the use of creating sub interfaces, for example eth0.1 etc...
can someone please give an example of a situation where it would be useful

thanks

---

### Post by Iowan on 2010-10-31
Are you talking bout an alias - like eth0:1?

---

### Post by acontibun on 2010-10-31
yes

sorry for the incorrect wording

can you explain pls

---

### Post by SeijiSensei on 2010-10-31
Many times providers offer an "IP subnet" as well as a single IP address (usually for an additional fee).  If you run secure HTTP servers, the best method is to assign each server a separate IP address within your assigned subnet.  There are many other applications where it's valuable to have a server that listens on multiple addresses.

---

