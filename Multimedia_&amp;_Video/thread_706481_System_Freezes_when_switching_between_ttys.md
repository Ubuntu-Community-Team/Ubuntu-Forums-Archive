---
title: "System Freezes when switching between ttys"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by Noiano on 2008-02-24
Hello everybody
I am using Ubuntu 7.10 ati proprietary driver with my ati radeon 9500 pro. I was unable to use the latest ati driver so I had to switch to the Ubuntu maintained one. The problem is that when I try to switch from the gdm to another tty with ctrl+Fn I cannot return to gdm (ctrl+f7) because system freezes.
Same thing happens when I logout from gnome. The logs seems ok, I only can see the following error in Xorg.0.log:

```

(==) fglrx(0): Using hardware cursor
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

```

What can I do?

Thanks for your attention ;)

---

### Post by jeffus_il on 2008-02-24
You have some library remaining from the driver you installed manually which is being incorrectly accessed by the driver from the repository. You have to try to completely uninstall the previous driver. This is the problem with installing software not in the repository, the uninstall is not clean ...

---

### Post by Noiano on 2008-02-24
> **jeffus_il said:**
> You have some library remaining from the driver you installed manually which is being incorrectly accessed by the driver from the repository. You have to try to completely uninstall the previous driver. This is the problem with installing software not in the repository, the uninstall is not clean ...

I think I have removed all the packages...can you give my some advice?:confused:

---

