---
title: "How to log ttyS0"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by coderx on 2009-07-18
Hi , 

It there any way how to log the activity of the Serial ports on Ubuntu ?

---

### Post by wojox on 2009-07-18
Download ttylog in repos I think.

Then in terminal:

```
ttylog -b 9600 -d /dev/ttyS0 > file.txt
```

---

### Post by coderx on 2009-07-18
Thanks , a lot! It work's fine.

---

