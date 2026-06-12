---
title: "Hardware issue"
date: 2008-07-06
forum: Mythbuntu
---

### Post by mirekU8000 on 2008-07-06
Hi there, I'm trying for few days to install mythbuntu but without success.
First of all I would like to know if my hardware is supported at all.
I have got: 
ABIT AB9 Quad BT
Intel Core 2 Duo
2 GB RAM Geil
NVIDIA 8800 GTS 320 MB
Gigabyte U8000 USB hybrid (DVB-T and analog)
Techinstar Sky HD2 PCI DVB-S
WD Caviar 320 GB SATA

So far I somehowe installed it, but it doesn't boot. I have 3 disks. One is Vista, second Data and third one is for Mythbuntu. During the installation I've seen all of them, and eventually I chose the third one. Now when I boot it I'm directly routed to (initramfs). I trade recovery mode as well and there I saw following.

ALERT /dev/disk/by-uuid does not exist 
Check root=bootarg

I don't have any idea how to continue. Anyway I wolud like to check if someone has some of above mentioned hardware in his configuration and if it works or not, so I can stop (I hope not) this agony :-)
Thanks

---

### Post by volkswagner on 2008-07-06
Maybe grub is buggered.  Is it in the right location?  You should give more specifics on hard disk physical layout.  How are they connected and how are they partitioned?  Can you boot into the live CD?  If you can run,

```
sudo fdisk -l
```

and post the results.

You may just need to reinstall grub to the MBR, assuming this is where Vista boots.

---

### Post by mirekU8000 on 2008-07-07
I have 3 disks, one is VISTA OS is placed, second one is DATA, and third one I used for Mythbuntu. During the instalation I was asked where to put grub so I choosed the disk where Linux was to be installed, so it didn't (I hope so) changed anything on disk where Vista is.

In order to start Mythbuntu or Vista I change Hard disk order in BIOS. When I put WD as first one I get the option to boot kernel, recovery mode or Windows. If I put Maxtor as first (there is Vista) I can't see linux at all, but it works so (I meam VISTA).

Today I also tried with Ubuntu, and the same error as with Mythbuntu. When it comes to disk partitioning there is no disk at all. I'm not sure how did Mythbuntu recongize all disk that time. I tried several times before and after sixth or seventh try they somehowe shown up.
Maybe there is a problem with my motherboard. I have't find anywhere chipset drivers for Linux...

If I start mythbuntu I finish each time in (initramfs). All I can see is:
[242.209348] ata6.00: ravalidation failed (errno=-5)
[343.304573] ata7.00: revalidation failed (errno=-5)

Then I started liveCD in order to get terminal. If I type sudo fdisk -l I get nothing, just a new line. It doesn't see any disk at all, as while trying to install it. On the other hand, when I set mythbuntu disk to be first device for booting it reads GRUB (on that disk I suppose) and I get option gerneric, generic (recovery mode), memory test, and windows

Today I tried with Open SUSE, and eveything works there, so there must be a problme with the Ubuntu. I don't care for the distribution at all as long as mythtv works :-)

---

