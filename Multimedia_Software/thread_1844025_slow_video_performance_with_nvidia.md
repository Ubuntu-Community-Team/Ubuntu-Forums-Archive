---
title: "slow video performance with nvidia"
date: 2011-09-14
forum: Multimedia Software
---

### Post by dirkfanick on 2011-09-14
Hi!

Got a box with 2mhz and nvidia gf6200 and the nvidia-binary-driver. 3d works perfectly but I won't use it much.

Sadly the 2d apps like browsers (flash!) are somewhat horrible slow.

I've read that the open-source-nouveau-driver works faster with 2d and I thought about to install it on the terminal I am allowed to with-admin.

My fear: The last time I tried it (uninstallation of nvidia-bin and replacing it with nouveau) the screen went black after reboot and no tty was reachable. We had to reinstall and I really don't like that.

So how save is it to switch this driver?

---

### Post by realzippy on 2011-09-14
...on my machines the proprietary driver is much faster than nouveau,even
on 2D.
The nouveau driver should have worked out of the box before you installed the nvidia driver,so you have an idea about it's performance.

---

### Post by dirkfanick on 2011-09-14
[B][SIZE=1][FONT=Arial]From: [http://linuxupdate.blogspot.com/2007/07/nouveau-driver-2d-performance-exceeds.html](http://linuxupdate.blogspot.com/2007/07/nouveau-driver-2d-performance-exceeds.html)[/FONT][/SIZE]
[/B]

[B]
[/B]

**Thursday, July 12, _2007_**

Richard Hughes has just published results from the [gtkperf]("http://gtkperf.sourceforge.net/") performance test.

Results:
[INDENT]Nouveau: 24.86 seconds
NV:  40.78 seconds[/INDENT]

Which is a 64% improvement over the existing Nvidia sponsored nv driver.

This  is a very limited 2D only test and does not represent 3D performance  but it does show that the developers are making good progress.

---

### Post by realzippy on 2011-09-14
What has this to do with your "issue"?

---

### Post by dirkfanick on 2011-09-14
I want to have a faster 2d-desktop and nvidia-closed-source-driver is slow.

vesa?
nouveau?

---

### Post by jawilljr on 2011-09-14
> **dirkfanick said:**
> [B][SIZE=1][FONT=Arial]From: [http://linuxupdate.blogspot.com/2007/07/nouveau-driver-2d-performance-exceeds.html](http://linuxupdate.blogspot.com/2007/07/nouveau-driver-2d-performance-exceeds.html)[/FONT][/SIZE]
[/B]

[B]
[/B]

**Thursday, July 12, _2007_**

Richard Hughes has just published results from the [gtkperf]("http://gtkperf.sourceforge.net/") performance test.

Results:
[INDENT]Nouveau: 24.86 seconds
NV:  40.78 seconds[/INDENT]

Which is a 64% improvement over the existing Nvidia sponsored nv driver.

This  is a very limited 2D only test and does not represent 3D performance  but it does show that the developers are making good progress.

NV is NOT Nvidia's proprietary driver. NV comes from MIT and is FOSS.

The Driver "nvidia" is Nvidia's proprietary driver. And yes the nvidia driver from nvidia will always beat Nouveau.

So the above test is flawed as it doesn't test Nvidia's driver.

Jerry

---

