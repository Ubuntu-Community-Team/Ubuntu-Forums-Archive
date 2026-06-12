---
title: "How Do I call X, so I can reconfigure it?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by chris_andrew on 2011-04-03
Hi, all!

Because of my graphic card/ monitor combination, X does not usually configure automatically, and I need to run Xorg -configure.

This usually works without a problem, but after 11.04 installation (Natty), I don't see a grub boot menu in order to enter recovery mode, prior to re-configuring X.

If I let the machine boot normally, I can switch to a virtual terminal and this is where I would normally kill X, if needed. I have tried killing it and it re-spawns. When I switch to run-level 3 (telinit 3), X still seems to be running. Can anyone help me kill X or boot without X, so I can configure it properly?

Any help appreciated.

Cheers,

Chris.

---

### Post by kio_http on 2011-04-03
Boot Ubuntu in recovery mode:

At the blue (ncurses) prompt chose drop to root shell
Type
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cariboo on 2011-04-03
Holding the shift key during boot, should show the grub menu.

---

### Post by chris_andrew on 2011-04-04
> **kio_http said:**
> Boot Ubuntu in recovery mode:

At the blue (ncurses) prompt chose drop to root shell
Type
```
sudo dpkg-reconfigure xserver-xorg
```

I'm not near the PC, but I was under the impression that that option was dropped several years ago; I'll give it a try anyway.

Thanks,

Chris.

---

### Post by cariboo on 2011-04-04
What type of graphics card does your system have, as there are a couple of ways to create an xorg.conf file.

---

### Post by kio_http on 2011-04-06
> **chris_andrew said:**
> I'm not near the PC, but I was under the impression that that option was dropped several years ago; I'll give it a try anyway.

Thanks,

Chris.

Well, it wasn't exactly dropped, but it is now automatic i.e instead of letting you chose your hardware, it detects it and accordingly configures the system.

---

