---
title: "Home Partition Doesn't Mount During Startup"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by HalfEmptyHero on 2011-04-22
My root partition is on /dev/sda1 and my home is on /dev/sdb1. During startup I get a checkfile error saying that /home can't be mounted. It gives me 3 options: Ignore, Skip Mounting, and Manually Fix (or something like that). When I choose the manual option I can manually mount it using sudo mount /dev/sdb1 /home and then hit Ctrl D. That works fine, but what should I do to get it to stop that.

Running Kubuntu Natty with all updates.

---

### Post by scottmuz on 2011-04-22
Can you post your /etc/fstab file

---

### Post by seeker5528 on 2011-04-22
> **HalfEmptyHero said:**
> When I choose the manual option I can manually mount it using sudo mount /dev/sdb1 /home and then hit Ctrl D. That works fine, but what should I do to get it to stop that.

And did you try fixing it before mounting it?

By fixing I mean 
```

fsck /dev/sdb1

```

If you are in single user mode, there is no reason to use sudo, you are already root.

Later, Seeker

---

### Post by HalfEmptyHero on 2011-04-25
Thanks for the help, but I think it was just a bad install. I had several other things acting up as well, so I just started fresh again and haven't had any issues.

---

