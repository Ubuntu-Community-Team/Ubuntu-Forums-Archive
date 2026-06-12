---
title: "Upgrading motherboard and processor"
date: 2009-12-07
forum: Mythbuntu
---

### Post by Caps18 on 2009-12-07
I am looking to do a simple upgrade of some hardware to fix a few problems playing HD movies and displaying the on screen graphics.  I am wondering if I will have any problems if I upgrade to a fast processor, different nVidia graphics card (possibly), different RAM, and different sound card?  Will Linux be able to recognize all this if I just swap in the hard drives?  Should I back up the data and do a new install of 9.10 (and have to setup everything again)?  

I'm hoping this will be a quick and simple process, but I'm worried about messing up a system that works 99% of the time.

Thanks

---

### Post by ian dobson on 2009-12-07
Hi,

You shouldn't have too many problems just swapping out bits. I've copied a Quad Core Intel boot drive and used it on a Dual Core AMD system, with only afew problems with network cards etc.

Before you start playing about it's always a good idea to have a backup.

Regards
Ian Dobson

---

### Post by heartburnkid on 2009-12-08
I did the same thing not too long ago, replacing a socket 939, NForce4-based motherboard with a socket AM2+, AMD 780G motherboard; had no problems whatsoever.  Linux seems to be rather resilient that way.  YMMV, of course, but you'll likely do just fine.

One caveat I will give, though, is remove any and all proprietary video drivers before doing the upgrade.  It's just easier that way.

---

### Post by Caps18 on 2010-02-01
So, I finally got around to doing this upgrade, and I thought everything was going well.  The Mythbuntu logo came up, but the bar at the bottom did not move.  It eventually dropped me out to a (initramfs) prompt.

When I used the recovery mode, this is where it had problems:

[ 4.756000]ata1:SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 5.068000]ata2:SATA link down (SSTatus 0 SControl 300)
[ 5.552000]ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 5.864000]ata4:SATA link down (SSTatus 0 SControl 300)
[ 6.176000]ata5:SATA link down (SSTatus 0 SControl 300)
[ 6.488000]ata6:SATA link down (SSTatus 0 SControl 300)


*(After about 30-45 seconds)

Done.
        Check root= bootarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/9d7cb373-3914-4d84-aab0-ddc4e7cb000c does not exist.  Dropping to shell!



I had a SATA PCI card in my old computer, would adding that to the new system make it work?  Or is there some way to fix this problem?  Is there someway to update the UUID numbers (I think I have done this before).


Thanks!

---

### Post by ian dobson on 2010-02-01
Hi,

maybe try just manually editing grub to use /dev/sda1 or whatever your root is on. On bootup press escape when the grub countdown is displayed, then "e" to edit the kernel boot line (change root= or read root=/dev/sda1)

Maybe sda1 is different on your box and the changes are not permanente. You'll need to edit /boot/grub/menu.lst. 

Regards
Ian Dobson

---

### Post by Caps18 on 2010-02-01
It turns out that there was a setting in the BIOS that was set on SATA that needed to be switched to ACHI.

9I did change the fstab uuid info for sdb, but it was correct for sda.  Doing that did not fix the problem, it only allowed it to get past the hard drive part and usb loading, but it hung up after that.

---

