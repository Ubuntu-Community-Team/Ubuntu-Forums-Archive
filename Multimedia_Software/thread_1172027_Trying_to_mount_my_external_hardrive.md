---
title: "Trying to mount my external hardrive"
date: 2009-05-28
forum: Multimedia Software
---

### Post by Lakeside5 on 2009-05-28
Can someone be so kind as to walk me through this? I would be eternally grateful :) I'm thinking I have to mount my external hard drive, as it stopped showing up in the 'computer' directory. I read about creating a directory/mounting the hardrive, and tried it but it didn't work. I mad a directory 'external' in /mnt and ran a mount command to mount to that directory.  I think my hardrive (Lacie 500gb) is a fat format, that's all I know. I need to transfer some files on my external, and also on my Linux computer, onto the other, windows computer, so I really need this. thanks

---

### Post by cariboo on 2009-05-28
Could you open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and post the output in your next post. The above command will tell us if your external drive is detected properly.

---

### Post by Lakeside5 on 2009-05-28
Thanks cariboo907, her it is:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8474    68067373+  83  Linux
/dev/sda2           16248       30401   113692005    f  W95 Ext'd (LBA)
/dev/sda3   *        8475       16247    62436622+  83  Linux
/dev/sda5           16710       30401   109980958+   7  HPFS/NTFS
/dev/sda6           16585       16709     1003999+  82  Linux swap / Solaris
/dev/sda7           16248       16584     2706889+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Lakeside5 on 2009-05-29
I think the sda3 one is the external hardrive?

---

### Post by JCoster on 2009-05-29
> **Lakeside5 said:**
> I read about creating a directory/mounting the hardrive, and tried it but it didn't work.

What didn't work?  What was the error message given in the terminal?  If it had an unclean unmount from Windows then you may need to shut it down properly or alternatively if the drive is the NTFS one shown in your fdisk -l output, then you can use the following to mount it:

```
sudo mount -t ntfs-3g /dev/sda*x* /media/*[directory to mount to]* -o force
```

Also, note that if you're trying to mount it to a directory with spaces in, say, 'My Drive', you must enter this as 'My\ Drive'.

---

### Post by Lakeside5 on 2009-05-29
Thanks very much for this advice, I will get to it later on today :)

---

### Post by JCoster on 2009-05-29
No problem, let me know how you get on...

---

