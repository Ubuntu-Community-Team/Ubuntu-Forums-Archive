---
title: "DD backup fails"
date: 2009-07-13
forum: Multimedia Software
---

### Post by theevilhamster on 2009-07-13
I am trying to make a backup of an old game (on a CD) for a friend using ```
dd if=/dev/scd0 of=/media/disk-1/backup
```.

It runs for a while, then I get

"dd: reading `/dev/scd0': Input/output error
3280+0 records in
3280+0 records out
1679360 bytes (1.7 MB) copied, 13.7628 s, 122 kB/s"

what am I doing wrong? It works for other disks.

can I suppress the error and get DD to continue, or is there another way round it?

Many thanks!

---

### Post by theevilhamster on 2009-07-14
bump?

---

### Post by zetman on 2009-07-14
I don't know what's wrong, but why are you using dd and not something like Brasero?  or at least something with some sort of error checking if you don't like GUIs?  Is there a specific need to use dd?

---

### Post by theevilhamster on 2009-07-14
No, no specific need for dd, just what I'm used to for creating a raw backup. And yes, I do prefer a CLI.

Thanks for the reply, greatly appreciated.

Its things like this that annoy me, as my linux knowledge is pretty reasonable. I know most of the filesystem, and lots of the basic system files, like the bashrc very well.

Thanks again.

---

### Post by mtreece on 2009-07-17
I'm having problems with dd myself.
For me, I keep getting this:
```

dd: reading `/dev/sr0': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00249717 s, 0.0 kB/s

```

I am able to mount the CD using normal GUI / magic / behind-the-scenes Ubuntu interface, but I'd love to use "dd" in order to copy the CD at the bit-level.

You can, however, try something like this
```
dd if=/dev/scd0 of=/media/disk-1/backup conv=noerror
```

I think this will bypass any error you get and keep on working, but don't hold me to this.

However, this might not be a good idea (bypassing any error), since any data that isn't copied correctly for an application (including games) could result in a crash.

You might also want to try and clean the CD / medium.  I've known dd to stop after it hits something it can't read.

---

### Post by theevilhamster on 2009-07-18
Many thanks, I will give this ago when I get a chance, and I hope it works!

---

