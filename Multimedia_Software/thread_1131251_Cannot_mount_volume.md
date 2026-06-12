---
title: "Cannot mount volume"
date: 2009-04-20
forum: Multimedia Software
---

### Post by uzzo2 on 2009-04-20
I am getting an error when trying to unmount some avi files on a dvd that my daughter burned with her vista machine. These are avi movie files which I have converted before using DeVeDe. After I put the disc in, I get a box that pops up that says "Cannot Mount Volume, Invalid mount option when attempting to mount the volume 'UDF Volume'." I was just wondering if anyone has had this problem before. Thanks in Advance.

---

### Post by drs305 on 2009-04-20
I am not familiar with the problem but if you open gconf-editor with the command below it will show the UDF mount options:
```

gconf-editor /system/storage/default_options/udf/mount_options

```

On my machine, which I haven't played with UDF, *mount_options* shows:
> uid=,exec

---

### Post by uzzo2 on 2009-04-20
> **drs305 said:**
> I am not familiar with the problem but if you open gconf-editor with the command below it will show the UDF mount options:
```

gconf-editor /system/storage/default_options/udf/mount_options

```

On my machine, which I haven't played with UDF, *mount_options* shows:
I tried both options, i get the same error, maybe a bad disk?

---

