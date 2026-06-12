---
title: "ATI-driver fglrx - Black screen at boot"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by dirac on 2006-11-04
Hello,

I have a problem with the fglrx ATI-driver. I searched the forum, but couldn't find a solution that solved my problem.

I'm using Edgy with ATI-driver 8.28.8. While it works after the installation, it stops working after a while: I can reboot a random number of times without any problems, but after a while I get a black screen at boot. This happens when gdm should show up.

I'm using Edgy x86 and installed the fglrx driver using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I have an AMD64 and a Radeon 9550. The output of 'uname -a':
Linux atlas-linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

When I look at the logs, there are no error messages. The last lines in Xorg.log are:

(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Solid Lines
        Dashed Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete

I cannot switch to another console when the screen is black. In xorg.conf I  disabled "Composite" and "extmod", without any change in behaviour. The "ati" driver, used after installation, never worked (I'm unable to use the LiveCD).

To solve the situation, I do the following:
- Boot in Single User mode
- Change the driver in xorg.conf from fglrx to vesa
- Reboot
- Change the driver in xorg.conf from vesa to fglrx
- Reboot

Now X will start without any problems, until the next time it will stop working...

I used the fglrx driver for more than a year in Gentoo and never had any problems. I also had this problem in Dapper x86, AMD64 and Edgy AMD64.

Any ideas what the problem is and how to solve it?

Thanks!!

---

