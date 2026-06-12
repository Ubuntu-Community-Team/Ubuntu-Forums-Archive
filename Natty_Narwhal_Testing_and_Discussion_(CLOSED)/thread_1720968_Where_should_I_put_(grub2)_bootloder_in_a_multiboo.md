---
title: "Where should I put (grub2) bootloder in a multiboot system?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-04-03
Hello,

I have a multiboot system where openSUSE 11.4 controls the bootloading of Windows 7, opensuse and Fedora.  In other words, the default bootloader is Grub in openSUSE.  Originally I installed Windows 7, then when installing openSUSE chose booting from MBR of Windows and root partition of Suse.  In subsequent installations, I only put Grub in the root partition of a distro. Previously when I still had Ubuntu 10.10 as part of this system, I chose custom installation of Ubuntu then put (grub2) bootloader in the root partition of Ubuntu and everything is handled nicely from /etc/boot/menu.lst of openSUSE which uses the original Grub. 
The other day I upgraded from Ubuntu 10.10 to 11.04 and lost all other OS's when I put the boot loader in Ubuntu's root partition.  I meant I did not see Grub menu on startup, only a text login screen for 11.04.  Re-installed 11.04 alongside with other OS's (Choice #1 in Ubuntu 11.04 installation menu) results in booting directly into 11.04. I did not see any option for booting other OS's.

Where did I go wrong?  Please tell me where to put (Grub2) bootloader when installing Ubuntu 11.04 into an existing multiboot system.

Thanks a lot for your help.

:confused:

---

### Post by jerrylamos on 2011-04-03
Do you have a 10.10 live CD or live USB?  If so, boot that, and running live do sudo update-grub and sudo grub-install /dev/whatever.

Natty Grub 1.99 screws up frequently for me....I use Meerkat to get running again....frankly, I always have a 10.10 or 10.04 partition somewhere on the multiple hard drives so I can recover from Natty's Grub.

Jerry

---

### Post by fabricator4 on 2011-04-03
> **iClouseau88 said:**
> Where did I go wrong?  

Probably nowhere, sometimes things don't go as planned for some reason.

My feeling is that if you update the grub it will find your other partitions and configure the boot menu for you:

```

sudo update-grub

```

and let it do it's thing.

From my experience, the active grub is the one on your first boot drive (unless you change boot order) and the master grub2 configuration is the one in the partition that you installed at the time, regardless of which partition you booted into.

I have found it useful to have a grub on a second hard drive, though in truth I haven't had to use it for recovery. The same rules apply, except you have to change the boot order or otherwise tell the BIOS to boot off the second physical drive.

For example I have an SD card in this machine (EeePC) that is a full install of Natty beta 1 and also has Grub2 V1.99.  I can boot it either by the Grub2 v1.98 on the hard drive or by booting off the SD card.  If by chance one or the other grubs got messed up I could boot off the other drive and fix it.

Chris

---

