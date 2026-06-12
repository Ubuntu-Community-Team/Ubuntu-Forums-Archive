---
title: "K3B burns at 2x speed max on a 16x speed disc"
date: 2008-07-04
forum: Multimedia Software
---

### Post by Magnentius on 2008-07-04
When I burn data or a homevideo to a dvd, K3B burns at 2x speed max. Only once did it burn at 4x speed, but I didn't make any settings to accomplish that. The discs support 16x speed and my dvd drive at least supports 4x, but I'm not sure exactly how much it supports.

I tried burning a dvd on a different computer, but the same problem: K3B only burns at 2x speed, also when I choose "maximum" as the speed.

Does anyone have an idea how I can solve this?

Many thanks in advance.

---

### Post by medic2000 on 2008-07-04
I think all the Linux community suffers the same problem yet i don't see any firm solutions or explanations yet?
Now i am beginning to believe we cant write dvd's in 16x in ubuntu.

Maybe this will solve your problem it didn't solved mine:

[http://ubuntuforums.org/showthread.php?p=4615284#post4615284](http://ubuntuforums.org/showthread.php?p=4615284#post4615284)
[https://bugs.launchpad.net/ubuntu/+bug/175022](https://bugs.launchpad.net/ubuntu/+bug/175022)

Some useful links:

[http://en.kioskea.net/pc/ide-ata.php3](http://en.kioskea.net/pc/ide-ata.php3)
[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

---

### Post by medic2000 on 2008-07-05
Bump

---

### Post by Magnentius on 2008-07-05
Thanks for your reply, medic2000. When I enter the command "hdparm -d1 /dev/scd0" at the terminal, I get the following error messages, just as mentioned on launchpad:

 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

But when I give the "dmesg |grep DMA" command, I don't get the following error messages as reported by others:

ata2.00: simplex DMA is claimed by other device, disabling DMA

In stead, I get:

  ata2.00: ATAPI: <dvd device name> max MWDMA2
  ata2.00: configured for MWDMA2

MWDMA2 stands for "Multi-Word DMA 2" but it should be UDMA/* I believe. (see [here]("http://club.cdfreaks.com/f92/cant-get-advertised-udma2-stuck-mwdma2-195005/"))

My other PC seems to be configured to UDMA/33 after a fresh Ubuntu 8.04 installation and it seems to be able to write at 4x speed. Still not enough, but better than 2x. Very strange, before I reinstalled Ubuntu 8.04 it could only write 2x.

According to [this]("http://dreamlinuxforums.org/index.php?PHPSESSID=325bc55004add578e5c0b6084f607a6b&topic=1329.msg10883#msg10883") message DMA should be enabled when you give the "hdparm -d1 /dev/scd0" command.

When I give the "hdparm -i /dev/cdrom" command at the terminal (see [here]("http://www.redhat.com/archives/fedora-list/2007-November/msg04530.html")), I get the following: 

 DMA modes:  mdma0 mdma1 *mdma2 
 * signifies the current active mode

So my DVD is set to mdma2, which is I think just Multi-Word DMA 2.

According to [Wikipedia]("http://en.wikipedia.org/wiki/UDMA#ATA_standards_versions.2C_transfer_rates.2C_and_features"), MWDMA2 is obsolete since 2001 and since my computer is way younger than that something MUST be wrong.

Solution, anyone? :confused:

---

### Post by medic2000 on 2008-07-06
Noone will help?

---

### Post by Magnentius on 2008-07-07
I believe this is a driver problem, but that doesn't help much.

According to [this guy]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636") it is necessary:

[INDENT]Switching drivers sounds easy, but it's actually quite complicated when you have to factor in regression testing. The reason for using the current driver set is because they proved to be stable, and in some cases (like for controllers mentioned here) the alternate driver was actually very unstable, not allowing people to boot. So I consider it very prudent to use a driver that may degrade CD-ROM support for some people as opposed to using a driver that makes the system unbootable for others.[/INDENT]

On the other hand, they said the problems would be fixed in gutsy, but now we're running hardy, and still the problems persist. :(

---

### Post by mc4man on 2008-07-07
@ Magnentius
if you still have wine install Imgburn, in winecfg set to nt 4.0, autodetect drives (if not already) and try a burn as a point of comparison 
[http://www.imgburn.com/](http://www.imgburn.com/)
Maybe also with some media in drive (not blank) run ```
sudo lshw -C disk
``` or post make, model of dvd drive.

---

### Post by medic2000 on 2008-07-09
I will try it tomorrow and post the results.

---

### Post by medic2000 on 2008-07-11
```
sudo lshw -C disk:
*-disk                  
       description: ATA Disk
       product: HTS541010G9AT00
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MBZO
       serial: MP20XAX0KYWWYS
       size: 93GiB (100GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b8f0ffa4
  *-cdrom
       description: DVD-RAM writer
       product: DVDRW SSM-8515S
       vendor: Slimtype
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: GRS6
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
```

And now i tried the imgburn to burn a dvd and it only writes 2x.

---

