---
title: "FGLRX driver on customized kernel"
date: 2008-04-21
forum: Multimedia &amp; Video
---

### Post by niobos on 2008-04-21
Hi,

I know that my situation is officially not supported, but I'll ask anyway.

I'm trying to get 2 thins to work together:
[LIST]
[*]Standby (suspend-to-ram)
[*]fglrx
[/LIST]

If I use the standard ubuntu kernel (2.6.22.9-generic) the fglrx works fine, but I can't get my machine into standby.
If I boot my custom-made gentoo-kernel, the standby works, but I need to compile the fglrx kernel-module.

I'm looking for some guidlines to do one of:
[LIST]
[*]Get the FGLRX-kernel-module compiled under ubuntu
[*]Get the ubuntu-kernel configured/recompiled/whatever to get standby working
[/LIST]

Can anyone help me with this?
Please note: I'm an ubuntu-newbie, but I have 5+ years of Gentoo-experience.

If you need any more info about my system, don't hesitate to ask

---

### Post by xzero1 on 2008-04-21
You might try to compile the kernel using the slab allocator (the default for Gutsy is slub) as there were some suspend issues relating to that.
See: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/84991](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/84991)

Good luck.

---

### Post by niobos on 2008-04-22
Thanks for the reply.
I read the bug, but I don't think it's the same issue. I can't get my machine INTO standby, even with the VESA driver.

---

