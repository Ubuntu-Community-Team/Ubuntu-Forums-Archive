---
title: "Extract img file"
date: 2009-01-11
forum: Multimedia Software
---

### Post by valros on 2009-01-11
Hey, I used dd_rhelp to read data from a possibly failing drive, it placed all the data in a 74.5 .img file, all id like to do is extract these files.

---

### Post by jpkotta on 2009-01-12
You should be able to mount it as a ext3 image, if I understand correctly what dd_rhelp does.
```
sudo mount -o loop /mnt output_of_dd_rhelp.img
```

---

