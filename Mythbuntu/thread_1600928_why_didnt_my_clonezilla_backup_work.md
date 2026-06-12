---
title: "why didnt my clonezilla backup work?"
date: 2010-10-19
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-10-19
I cloned my 10.04 setup before upgrading to 10.10 and recently tried to use the backup i had made.  Sadly i couldnt boot it as mythbuntu reported it couldnt mount /var/lib yet clonezilla had reported a sucessful clone earlier.

How do other people create a full bootable backup of there myth setups?

Thanks

---

### Post by yonkiman on 2010-10-19
> **geekyhawkes said:**
> How do other people create a full bootable backup of there myth setups?

I can't explain what went wrong with your clonezilla backup, but I can tell you that I've successfully cloned my mythbuntu application using the command-line dd command.  It is usually as simple as:
```
>dd if=/dev/sda of=/dev/sdb bs=1024k
```
substituting sda and sdb with the correct drive names for your system (but make sure you get it right or you'll find out why people call dd "delete disk").

I think clonezilla can be used for this though; maybe you missed a crucial setting?  It needs to copy your MBR as well as your partitions...

Finally, I've learned the hard way (as you have) to clone and then immediately *test* (remove the original, then mount and boot from the clone) the cloned drive to make sure it worked.  That's the best way I know to make sure the operation succeeded.

---

### Post by psusi on 2010-10-19
Sounds like you didn't clone that partition.

---

### Post by geekyhawkes on 2010-10-21
Arr maybe, i thought i had picked to drive copy with all partitions but now you mention it i think i only saw it go through one partition write and verify! 

Thought it must be simple!

---

### Post by CharlesA on 2010-10-21
What I usually do when I made an image of a machine is that I restore said image onto another machine to make sure it's a good image.

---

