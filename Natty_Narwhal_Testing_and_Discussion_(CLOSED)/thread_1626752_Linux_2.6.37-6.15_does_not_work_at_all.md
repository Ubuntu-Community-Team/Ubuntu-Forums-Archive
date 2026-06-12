---
title: "Linux 2.6.37-6.15 does not work at all"
date: 2010-11-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2010-11-20
Made a new thread about this.

I just installed the newest 6 series kernel 2.6.37-6-15 with dpkg on Natty 64-bit.
In my system all kernels have worked OK up to this one.
It does not load at all and ends up in busybox.
I had to remove it and right now I am using the 2.6.37-5.14 flavour.

Here
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15](https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15)

---

### Post by plun on 2010-11-20
I haven't test this one but this is maybe scaring...:D
> 
  * Rebase to Linus 2.6.37-rc2+**git**

GIT is always more or less unstable....

All info:
[https://lists.ubuntu.com/archives/natty-changes/2010-November/001667.html](https://lists.ubuntu.com/archives/natty-changes/2010-November/001667.html)

For sure there will be no meta-package if this one brakes...

---

### Post by Harry33 on 2010-11-22
Right,
now this 2.6.37-6.15 kernel update has been rejected.

[https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15](https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15)

---

### Post by chrismine on 2010-11-22
For me no of the 2.6.37 kernels work, it does not detect my network adapter, otherwise for the short time I used it it booted into a desktop.

---

### Post by Quackers on 2010-11-22
> **Harry33 said:**
> Right,
now this 2.6.37-6.15 kernel update has been rejected.

[https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15](https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.15)

It's about time too! What a joke that was.

---

### Post by Harry33 on 2010-11-23
More issues with kernel 2.6.37-6 in Launchpad,
this time with the versions 2.6.37-6.16 and 2.6.37-6.17.

Build failures and a funny error message:
No space left on device
Here:
[https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.17](https://launchpad.net/ubuntu/natty/+source/linux/2.6.37-6.17).

But, the again, people at PPA xorg-edgers have managed to build this latest flavour 2.6.37-6.17
and it works just fine.
Right now using it on my 64-bit Natty (not with Unity but with Gnome-shell from Ricotz PPA).

---

### Post by Quackers on 2010-11-23
If I feel strong enough I'll have a look after a snooze :-)
Thanks for the update.

---

### Post by moviemaniac on 2010-11-23
jeez. And there I was scratching my head yesterday as to why my own vanilla build of -rc3 failed to boot with the same error message

---

### Post by cariboo on 2010-11-23
I just updated to 2.6.37-6-17 on three system, they all restarted with zero problems.

```
Linux chilanko-natty 2.6.37-6-generic #17-Ubuntu SMP Mon Nov 22 20:05:19 UTC 2010 x86_64 GNU/Linux
```

---

### Post by Harry33 on 2010-11-24
> **cariboo907 said:**
> I just updated to 2.6.37-6-17 on three system, they all restarted with zero problems.


Same here.
The latest 2.6.37-6.17 (built on 23th November) on Natty repos works fine.

---

### Post by Quackers on 2010-11-24
I just installed this and it is definitely much better! 
The updates did remove part of evolution, so that won't start any more and it won't let me re-install it due to dependencies issues.
Most of my previous problems have disappeared though :-)

---

