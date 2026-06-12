---
title: "Slow internet but fast in live mode"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by teddy379 on 2012-11-26
Hi
I installed Mint (the latest one), and the realtek lan driver but my internet is slow. That being said, my inherent is totally fine if I'm booting from the live CD to install.

---

### Post by teddy379 on 2012-11-26
Bump. How do I fix it?

---

### Post by guardsman85 on 2012-11-26
> **teddy379 said:**
> Hi
I installed Mint

Have you tried the [Linux Mint Forums]("http://forums.linuxmint.com/")?    As this site is geared towards Ubuntu issues, you might not get quite the help you are wanting here.

---

### Post by dannyboy79 on 2012-11-26
> **teddy379 said:**
> Bump. How do I fix it?
please dont' bump your threads prior to it being at least 24 hours. We're all here voluntarily.

When you're using the live cd, you could open a terminal and issue lsmod and look to see which realtek module (driver) the kernel is using. Then make sure that same kernel module is being used for your hard drive install.

---

