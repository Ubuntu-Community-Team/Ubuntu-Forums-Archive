---
title: "Getting Mac iPod to work on Hardy Heron"
date: 2008-10-09
forum: Multimedia Software
---

### Post by pokeyThePenguin on 2008-10-09
Hello all,

I'm running Ubuntu 8.04 Hardy Heron on a Toshiba Satellite L300 laptop. I use GNOME.

```

uname -a
Linux laptop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

```

My system is up to date.

I have the latest versions of gtkpod and Amarok. I have hfsplus.

I understand I had to disable journaling, so I ran my iPod on a Mac and successfully disabled journaling. I hooked my iPod up to my friend's laptop, ran gtkpod, and I could successfully write to the iPod. I come home, hook up my iPod to my laptop, ran gtkpod, and I couldn't write to my iPod. This baffles me. My friend had a fresh new install of Hardy Heron, and so do I.

dmesg outputs this:
```

[23766.021073] usb 5-3: new high speed USB device using ehci_hcd and address 4
[23766.124049] usb 5-3: configuration #1 chosen from 2 choices
[23766.151078] scsi8 : SCSI emulation for USB Mass Storage devices
[23766.182834] usb-storage: device found at 4
[23766.182840] usb-storage: waiting for device to settle before scanning
[23771.150760] usb-storage: device scan complete
[23771.197597] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[23771.171695] sd 8:0:0:0: [sdc] 950209 4096-byte hardware sectors (3892 MB)
[23771.172561] sd 8:0:0:0: [sdc] Write Protect is off
[23771.172565] sd 8:0:0:0: [sdc] Mode Sense: 68 00 00 08
[23771.172568] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[23771.174804] sd 8:0:0:0: [sdc] 950209 4096-byte hardware sectors (3892 MB)
[23771.175431] sd 8:0:0:0: [sdc] Write Protect is off
[23771.175435] sd 8:0:0:0: [sdc] Mode Sense: 68 00 00 08
[23771.175437] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[23771.175441]  sdc: [mac] sdc1 sdc2
[23771.211596] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[23771.211653] sd 8:0:0:0: Attached scsi generic sg3 type 0
[23771.578526] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[23771.791370] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

```

When I connect my iPod to my computer, I can see an icon for it on my desktop. I run gtkpod and it shows my iPod and the contents of my iPod. I'll, for example, delete a playlist that's on my iPod. I save changes, and gtkpod spits out these results:
```

Error opening /media/disk/iPod_Control/Artwork/F1061_1.ithmb: Read-only file system
Error opening /media/disk/iPod_Control/Artwork/F1055_1.ithmb: Read-only file system
Error opening /media/disk/iPod_Control/Artwork/F1060_1.ithmb: Read-only file system
Error opening /media/disk/iPod_Control/Artwork/F1028_1.ithmb: Read-only file system
Error opening /media/disk/iPod_Control/Artwork/F1029_1.ithmb: Read-only file system
Opening of '/media/disk/iPod_Control/iTunes/iTunesDB' for writing failed (Read-only file system).

```

And with Amarok, it detects my iPod, but when I click Connect, I get this message: "Media Device: iPod mounted at /media/disk already locked. If you are sure that this is an error, then remove the file /media/disk/iPod_Control/iTunes/iTunesLock and try again." So I click on Remove to continue, and I get this: "Media Device: removing lockfile /media/disk/iPod_Control/iTunes/iTunesLock failed: Unknown error."

I did "sudo rm /media/disk/iPod_Control/iTunes/iTunesLock" but obviously can't perform this action because the iPod is read-only right now.

The problem is that my iPod is being mounted as read-only, but I don't understand why because when I connected my iPod to my friend's laptop (he runs a dual boot: WinXP and Ubuntu Hardy Heron), it was mounted as read-write and I could edit playlists, add songs, etc.

I've exhausted Google for hours trying to resolve this issue, but I haven't found anything that has helped me. Maybe I'm a few steps closer to a solution, but that's it. The problem still exists.

My housemates all have Windows Vista on their laptops. Can I backup my songs onto my laptop, and then reformat my iPod using a laptop with Windows Vista? I only want to do this option if there's nothing I can do with just my laptop.

Note I'm a beginner to the wonderful world of Linux.

Thanks for your help!

---

### Post by Forbees on 2008-10-09
try using floola, it works with all ipods except for the touch i think

---

### Post by pokeyThePenguin on 2008-10-09
The iPod needs to be mounted with read and write access in order to install Floola: [http://www.floola.com/modules/wiwimod/index.php?page=docs_install](http://www.floola.com/modules/wiwimod/index.php?page=docs_install).

My issue is mounting my iPod with read and write access. ;)

---

### Post by pokeyThePenguin on 2008-10-10
As you saw in my dmesg, my iPod was apparently unmounted properly and it recommended that I use fsck.hfsplus.

I installed hfsprogs from Synaptic so that I can use fsck.hfsplus.

I did
```

sudo fsck.hfsplus -d /dev/sdc2

```

The output said that my iPod was OK and was clean.

I tried unmounting, and then remounting manually:
```

sudo umount /media/disk
sudo mount -t hfsplus /dev/sdc2 /mnt/iPod

```

Note that your /dev/wxyz may be different than mine. If you run dmesg, you should get a line like this:
```

sdb: [mac] sdb1 sdb2

```

What you want is the last one because Apple stores all your data on the last partition.

dmesg spit out the same info as before; however, I had just recently read that someone mounted their iPod and had it connected to their computer, and then they rebooted. This solved their problem. I tried it, and it worked! I ran dmesg, and I didn't see any warnings for the iPod. It wasn't mounted as read-only. I went to iTunes_Control/iTunes and could successfully remove the iTunesLock. I also loaded up gtkpod and was able to delete a playlist and save changes. My iPod synced up with these changes.

I hope this solution can help someone else out too.

---

