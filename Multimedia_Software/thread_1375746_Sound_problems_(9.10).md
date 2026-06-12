---
title: "Sound problems (9.10)"
date: 2010-01-08
forum: Multimedia Software
---

### Post by Raghu1990 on 2010-01-08
I just updated to Ubuntu 9.10 and everything is great except for the fact that there is no sound. I've already tried the Comprehensive Sound Problems thread, and it didn't help.

With Google's help, i think i've found the problem. A particular site says:

"If it worked on 9.04 but not in 9.10 check that you are booting from the kernel included in 9.10: vmlinux-2.6.31-14-generic and not the one from 9.04 vmlinux-2.6.28-16-generic. This can happen if you clicked off a dialog asking you to update grub's menu.lst during installation."

During installation, I remember selecting an option like 'retain previous settings' or something similar when prompted to take action regarding menu.lst.

uname -a says:

```
vamsi@gkp-home-desktop:~$ uname -a
Linux gkp-home-desktop 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009 i686 GNU/Linux

```

So, i'm assuming that the problem is as stated and I'm booting from the wrong kernel.

Question: Is this actually the problem? If it is, how do I fix it?

---

