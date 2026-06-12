---
title: "Adding data to an existing CPIO archive"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by metallica1973 on 2011-10-29
I created a CPIO archive I wanted to add addition data to it but am having issues:


```


-rw-r--r-- 1 test test 629295104 2011-10-28 12:41 /home/test/Downloads/test.cpio


```

I tried:


```


sudo find /tmp -depth | cpio -oAO /home/test/Downloads/test.cpio
cpio: premature end of file


```

and


```


sudo find /tmp -depth | cpio -oAF /home/test/Downloads/test.cpio
cpio: premature end of file

```

Any ideas ??

---

### Post by metallica1973 on 2011-11-01
Not exactly what I want but inspirational and untested

```

'cat cpio1 cpio2 > | gzip > cpio_all'

```

Will test a return the results

---

