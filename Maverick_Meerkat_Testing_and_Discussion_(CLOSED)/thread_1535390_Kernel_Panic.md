---
title: "Kernel Panic"
date: 2010-07-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by fleamour on 2010-07-20
Hi

I am finding latest Maverick Kernel unstable, where it will panic locking up and flash with blinking lights.

How do I file a bug against the kernel itself?  As is not part of any package I believe.

---

### Post by sisco311 on 2010-07-20
Hi, 

Please read the stickies from the *Maverick Meerkat Testing and Discussion* sub-forum.

---

### Post by Iowan on 2010-07-20
Moved to Maverick Meerkat Testing and Discussion.

---

### Post by VMC on 2010-07-20
> **fleamour said:**
> Hi

I am finding latest Maverick Kernel unstable, where it will panic locking up and flash with blinking lights.

How do I file a bug against the kernel itself?  As is not part of any package I believe.

I seemed to remember having a kernel panic on a earlier iso. Are you zsyn-ing or just updating from a previous install?

---

### Post by fleamour on 2010-07-21
2.6.35-9 generic experiences random kernel panic. 2.6.35-7/8 seemed fine, I upgraded from 2.6.32-23.

What do you mean by "zsyn-ing"?

---

### Post by fleamour on 2010-07-21
Seems to happen reliably when removing power jack.

---

### Post by ranch hand on 2010-07-21
I think that to file a bug on this you would file it on ubuntu as the package.  If I am wrong, hopefully some one will jump me on it.
```

ubuntu-bug ubuntu

```
I expect that you will be asked to send some log files to document this.

---

### Post by fleamour on 2010-07-21
It was in the stickies @sisco311 mentioned.

Thanks.

---

### Post by fleamour on 2010-07-21
[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)

[https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeam/KernelTeamBugPolicies)

```
ubuntu-bug -p linux
```

Although the -p is obsolete, but still worked, but wiki needs updating.

Kernel panic was induced reliably by removing power jack, also happened randomly on all test kernels reducing laptop to a non booting error state.  It is testing only after all.  Managed to fire off bug report before crash.

Will roll back to Lucid for now, disappointing as Maverick solved a few bugs.

---

