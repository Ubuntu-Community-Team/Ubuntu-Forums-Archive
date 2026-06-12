---
title: "Kernel broke wireless; reverted to old kernel to fix..."
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by Moozillaaa on 2010-06-10
I upgraded the kernel in an update, and it broke the wireless configuration.

I booted the old kernel, 2.6.31-21-generic, instead of 2.6.31-22, and it's working like it was.

What's the proper solution - booting the old kernel every time?

++++++++++++++++++++++++++++


Another 'issue' is that after desktop loads, wireless is still taking a minute to connect. Karmic has done this since installing, whereas Hardy was connected when dtop finished loading...

---

### Post by 11hjpphty76lkjj on 2010-06-10
What's the wireless device you are using?

---

### Post by Stancel on 2010-06-10
so it's the Linux kernel, not Lucid? So you're telling me this kind of problem is going to be widespread among all Linux distros? :confused:

It's worse than I thought....

I bet you have an Atheros adapter, don't you...so do I, Atheros AR5001 if I recall correctly....

---

### Post by 11hjpphty76lkjj on 2010-06-10
Or broadcom. 

eww.

A

---

### Post by Moozillaaa on 2010-06-14
Yep - Broadcom.

Wireless is perennially **THE** problem with Linux. I think many are still in Windows because of wireless... :confused:

---

### Post by 11hjpphty76lkjj on 2010-06-14
Getting Broadcom wifi devices to work isn't impossible.  It can be a bit of a process though.  I've gotten mine to work by installing the broadcom package.

```
sudo apt-get install bcmwl-kernel-source
```

Hope this helps.

A

---

