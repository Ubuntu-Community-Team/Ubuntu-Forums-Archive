---
title: "scp doesn't work, shows horizontal line"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by pratiks19 on 2011-10-30
Hello,

I have a user "user1" on my ubuntu machine with hostname "kernel-panic".

scp (initiated on my laptop) to user1's home directory just shows a horizontal line but does not copy.

> psd@hp-laptop:~$ scp debug.log user1@kernel-panic:
user1@kernel-panic's password:
 _________________________________________________________________
psd@hp-laptop:~$


but scp initiated by user1 on kernel-panic succeeds.
Also there is a user2 on kernel-panic, and scp to user2 from my laptop has no issues.

Could any one please help me with this ?

Thanks.

---

