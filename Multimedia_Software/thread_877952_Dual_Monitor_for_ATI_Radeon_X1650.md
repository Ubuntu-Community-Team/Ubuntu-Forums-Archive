---
title: "Dual Monitor for ATI Radeon X1650"
date: 2008-08-02
forum: Multimedia Software
---

### Post by GMU_ninja on 2008-08-02
I recently installed the OS fresh.  The only changes I made are to get the Xserver to work right with the accelerated drivers; I added this to the end of the xorg.conf file:

```

Section "Extensions"
Option "Composite" "disable"
EndSection

```

I then attempted this solution for the dual monitors:
[http://ubuntuforums.org/showthread.php?p=1773710]("http://ubuntuforums.org/showthread.php?p=1773710")

But it didn't work.  All I want is the dual monitors to work right.  I don't really care about the accelerated graphics (which the Administration -> Hardware Drivers tool says is not enabled and are not in use anyways).  I attached the currently in use xorg.conf file.

The Preferences -> Screen Resolution tool appears to detect both monitors, but I won't split them!

Any help?  Any ideas?

My Setup:  Linux Mint (based on Ubuntu 8.04 Hardy)
Kernel Linux 2.6.24-19-generic
GNOME 2.22.3

Video Card: [SAPPHIRE 100198L Radeon X1650 512MB 128-bit GDDR2 AGP 4X/8X]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102086")

Monitors:  Samsung SyncMaster 225BW, widescreen (DVI); NEC MultiSync LCD 1760V (VGA)

---

### Post by GMU_ninja on 2008-08-06
> **GMU_ninja said:**
> All I want is the dual monitors to work right.  I don't really care about the accelerated graphics (which the Administration -> Hardware Drivers tool says is not enabled and are not in use anyways).

Alright, I lied...

I do care about 3D acceleration and OpenGL Direct Rendering.

I just installed Cedega and it needs those two things to work (which currently do not work).

Any help??

---

### Post by GMU_ninja on 2008-08-14
It's been a week with no response...

I thought that I would add some information:

When I enable the ATI proprietary drivers, the system will not boot.  It will go through the boot procedure, and about when it should go to a splash screen (with the load bar) it crashes into a black screen (screens are still on, but blank).

Any suggestions?  Do I need to provide more info?

Should I go someplace else for installation support?

---

### Post by GMU_ninja on 2008-09-05
Still no reply... anyone willing to help?

I am open to any ideas!

---

