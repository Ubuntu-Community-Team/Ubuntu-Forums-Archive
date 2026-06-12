---
title: "best filesystem for recordings"
date: 2011-01-13
forum: Mythbuntu
---

### Post by sami8519 on 2011-01-13
Hi,

I want a help regarding the best file system for recrordings? Is it ext4, JFS or something else? And why it is the best? I am right now using mythbuntu and have an external USB HDD formatted with ext4 filesystem for recordings, but since I am at the begining of my project I wish to know from now so that I never need to change it. 

Thanks and best wishes
Sami

---

### Post by ian dobson on 2011-01-13
Hi,

I've been using ext4 now for sometime on my big MythTV server (6Tb RAID 5 array), and have not had any problems.

I rather like to stay with "in kernel" drivers/modules that are activly being supported/developed.

XFS was the filesystem to use with large files (before ext4) but I've heard of problems when you need to fsck a very large file system (memory requirements of fsck).

I'd stay with ext4.

Regards
Ian Dobson

---

### Post by vanadium on 2011-01-13
Any modern robust file system will in practice do, indeed. Of more importance is the way your disk is connected to the system. With USB, you loose performance compared to an internal disk. Even then, it won't be a problem, I suppose.

---

### Post by sami8519 on 2011-01-13
Thanks guys for your help. I love this forum:)

BTW, I did not figure out so far how to mark a topic as "SOLVED", could you please tell me howto?

Thanks and Best Regards
Sami

---

### Post by ian dobson on 2011-01-13
Hi,

So what fs are you going for, if this thread is solved?

I think you can mark the thread as solved under the thread tools at the top od the page.

Regards
Ian Dobson

---

### Post by sami8519 on 2011-01-13
Hi Ian,

I just thought I am sticking with the ext4 file system because I was initially unsure whether ext4 has solved the problem with slow file deletion that was present in ext3. But since you have a good experience with ext4 and me thinking that ext4 has to  solve the drawbacks in ext3, led me to conclude that ext4 is the right option.

Thanks
Sami

---

### Post by psusi on 2011-01-13
> **sami8519 said:**
> 
I just thought I am sticking with the ext4 file system because I was initially unsure whether ext4 has solved the problem with slow file deletion that was present in ext3.

Yes, it did.

---

### Post by sami8519 on 2011-01-13
Thanks for the confirmation, Psusi.

Best Regards
Sami

---

