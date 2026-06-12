---
title: "Flash and YouTube slowdowns"
date: 2009-08-03
forum: Multimedia Software
---

### Post by ramsayeg on 2009-08-03
Hello everyone,

I already researched this topic by checking out almost every 2nd link on Google and finally decided to post a topic myself. I'm using Jaunty and have the most recent flash plugins.

But, whenever I watch a video on YouTube in full-screen, I experience slowdowns. The same with other flash games (for example - Zynga Poker on Facebook). 

I've tried reducing my effects to zero (no effects at all) and it's still not helping. 

I hope someone can help me out. Thanks!


SPECS:

H/W path           Device       Class       Description
=======================================================
                                system      R510-G.A228E
/0                              bus         QL8
/0/0                            memory      1MiB BIOS
/0/13                           processor   Intel(R) Core(TM)2 Duo CPU     T6400
/0/13/14                        memory      2MiB L2 cache
/0/13/16                        memory      32KiB L1 cache
/0/13/0.1                       processor   Logical CPU
/0/13/0.2                       processor   Logical CPU
/0/15                           memory      32KiB L1 cache
/0/17                           memory      4GiB System Memory
/0/17/0                         memory      2GiB SODIMM Synchronous 800 MHz (1.2
/0/17/1                         memory      2GiB SODIMM Synchronous 800 MHz (1.2
/0/100                          bridge      Mobile 4 Series Chipset Memory Contr
/0/100/2                        display     Mobile 4 Series Chipset Integrated G
/0/100/2.1                      display     Mobile 4 Series Chipset Integrated G
/0/100/1a                       bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1a.1                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1a.7                     bus         82801I (ICH9 Family) USB2 EHCI Contr
/0/100/1b                       multimedia  82801I (ICH9 Family) HD Audio Contro
/0/100/1c                       bridge      82801I (ICH9 Family) PCI Express Por
/0/100/1c/0        ra0          network     RT2860
/0/100/1c.1                     bridge      82801I (ICH9 Family) PCI Express Por
/0/100/1c.5                     bridge      82801I (ICH9 Family) PCI Express Por
/0/100/1c.5/0      eth0         network     RTL8111/8168B PCI Express Gigabit Et
/0/100/1d                       bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.1                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.2                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.3                     bus         82801I (ICH9 Family) USB UHCI Contro
/0/100/1d.7                     bus         82801I (ICH9 Family) USB2 EHCI Contr
/0/100/1e                       bridge      82801 Mobile PCI Bridge
/0/100/1f                       bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0        storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda     disk        320GB TOSHIBA MK3252GS
/0/100/1f.2/0/1    /dev/sda1    volume      94MiB EXT3 volume
/0/100/1f.2/0/2    /dev/sda2    volume      760MiB Extended partition
/0/100/1f.2/0/2/5  /dev/sda5    volume      760MiB Linux swap / Solaris partitio
/0/100/1f.2/0/3    /dev/sda3    volume      74GiB EXT3 volume
/0/100/1f.2/0/4    /dev/sda4    volume      222GiB EXT3 volume
/0/100/1f.2/1      /dev/cdrom   disk        DVDRAM GSA-T50N
/0/100/1f.3                     bus         82801I (ICH9 Family) SMBus Controlle
/0/100/1f.6                     generic     82801I (ICH9 Family) Thermal Subsyst
/0/1               scsi6        storage     
/0/1/0.0.0         /dev/sdb     disk        SCSI Disk
/0/2               scsi7        storage     
/0/2/0.0.0         /dev/cdrom2  disk        Virt. CD/DVD-ROM
/0/2/0.1.0         /dev/cdrom1  disk        Virt. CD/DVD-ROM
/1                 pan0         network     Ethernet interface

---

### Post by cottfcfan on 2009-08-03
What are your CPU levels like when you have the problem?

---

### Post by ramsayeg on 2009-08-03
> **cottfcfan said:**
> What are your CPU levels like when you have the problem?

I didn't even notice but the CPU levels are around 35-45% when starting the video (not in fullscreen, still runs smooth), around 20-30% halfway in and when in fullscreen I have no idea since I can't really see, but I'm guessing they are higher. 

Something's really not right, the notebook is pretty average and shouldn't have any problems whatsoever with regular internet work.

---

### Post by cottfcfan on 2009-08-03
If your CPU levels are 35-45% when viewing in small screen, it may be that there maxing out in Fullscreen.
 What exactly is the problem in Fullscreen? Is the video really choppy, if it is, mine was an acpi problem.
 I disabled acpi, in the boot kernel and it ran fine.
 Although disabling it could cause other problems.

---

### Post by ramsayeg on 2009-08-03
> **cottfcfan said:**
> If your CPU levels are 35-45% when viewing in small screen, it may be that there maxing out in Fullscreen.
 What exactly is the problem in Fullscreen? Is the video really choppy, if it is, mine was an acpi problem.
 I disabled acpi, in the boot kernel and it ran fine.
 Although disabling it could cause other problems.

Other problems? What can happen besides random shutdowns when I'm using my notebook way too much? If it's too serious I guess I'll have to let go of my YouTube addiction.

---

### Post by oogmsn on 2009-08-03
I have almost the same problem when I'm visiting certain sites e.g. [http://www.footytube.com/](http://www.footytube.com/) where my processor use indicates almost 100% usage...but no such problem with sites like youtube...but funny thing is that once I'm at footytube & goes back to youtube..the cpu still continues to be high...

---

### Post by cottfcfan on 2009-08-03
oogmns,
My problem exactly, when i played BBC iplayer in Fullscreen, CPU was high video choppy. Then even when I came off it the CPU remained high. Sounds like same acpi problem I have.
 When booting edit the kernel your booting into and add acpi=off at the end of the line. Then boot and see if the problem goes away.

---

### Post by ramsayeg on 2009-08-03
> **cottfcfan said:**
> 
 When booting edit the kernel your booting into and add acpi=off at the end of the line. Then boot and see if the problem goes away.

Will removing acpid and acpi-support from the Boot-Up Manager (GUI) work just the same? If not, can you please explain to me how to do the above?

---

### Post by cottfcfan on 2009-08-04
It may work. What i did was:

sudo gedit /boot/grub/menu.lst

Then look for the line above your kernels that has "kopt" in it and ends in "ro" add acpi=off to the end of the line, save the file, then run sudo update-grub, reboot and your done.
 
I also found something else out last night.
Adding noapictimer to the line instead, did nothing, but adding it to the line in the latest 2.6.31rc5 kernel, and everything runs smoothly, and i still have all my acpi/apic power options.
Which again leads me to beleive this is a kernel problem.

Problem then is i have no 3D as "fglrx" driver is not compatible with the 2.6.31 kernel yet.

---

### Post by ramsayeg on 2009-08-04
So after trying out hat you posted above, it did help a little but didn't remove the problem entirely. Do  you have any other suggestions?

---

### Post by cottfcfan on 2009-08-04
Assuming you`ve tried all the usual things like making sure youve no conflicting plugins (ie gnash or swfdec) try installing a later kernel and see if that helps.

---

### Post by ramsayeg on 2009-08-04
So I tried applying the latest kernel patch **(****[2.6.30.4]("http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.30.4.bz2"))** using the following command and it gives me path errors. I tried reading the man, running it with p0, etc. didn't work:

        sudo bzip2 -dc patch-2.6.30.4.bz2 | patch -p1

I run the command from within the /usr/src/ directory. 

Do you have any idea why does it fail?

---

### Post by cottfcfan on 2009-08-04
I download all my kernels from here as deb files and let package manager install them:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Download 

linux-headers all deb
linux-headers generic
linux-image

must be in that order.

---

### Post by alexdunne on 2009-08-04
Maybe something to do with video codecs ?

---

### Post by ramsayeg on 2009-08-04
Thank you.

Back to the original topic - I installed the latest kernel, but it doesn't make any difference. YouTube still doesn't work properly in full-screen mode.

Have you any other suggestions? perhaps they will work. I'm willing to try anything now.

> **alexdunne said:**
> Maybe something to do with video codecs ?

It's possible, have you any recommendation of good codecs? I only have the ones that came with Ubuntu.

---

### Post by cottfcfan on 2009-08-04
Ramsayeg..
I`m sorry but i`m out of suggestions, even my "fix" is only a makeshift one and not without issues (ie no 3d)
 i think it may just be a case of waiting for something better to come along, probably via updates, although this Fullscreen, high CPU issue has been running for some time now.

---

### Post by ramsayeg on 2009-08-04
Quick update for those suffering from the same issue: seems it was an Ubuntu / Intel GFX card issue. My netbook uses Intel GMA X4500, I used [this guide]("http://ubuntuforums.org/showthread.php?t=1130582") and it everything works just fine!

Thank you everyone!

---

