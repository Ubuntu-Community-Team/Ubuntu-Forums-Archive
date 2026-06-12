---
title: "HDD &amp; Capture Card Devices reorder on each boot (11.10)"
date: 2012-02-16
forum: Mythbuntu
---

### Post by davelindquist on 2012-02-16
I've just switched my MythDora box over to MythBuntu, and things are running really well, except...

On every boot, both my /dev/sd[abcd] devices, and my /dev/video[01] devices swap around.

I have two capture cards, /dev/video0 and /dev/video1, and with every boot, they reverse (and it seems to be an exact swap on each boot -- they are never the same two boots in a row).

Additionally, I have four hard drives, /dev/sda through /dev/sdd, and they ALSO swap around (although I've only caught /dev/sdb and /dev/sdd swapping) on each boot.

The hard drives don't really cause a problem, since they are mounted by UUID, but the capture cards are annoying -- I have to run mythtv-setup after each boot to pick the right card.

Is there anything I can do about this?  udev rules or something to keep things sane?

I've searched everywhere, and I've found a few folks with this type of problem, but never any solutions...

Thanks in advance!

---

### Post by nickrout on 2012-02-17
> **davelindquist said:**
> I've just switched my MythDora box over to MythBuntu, and things are running really well, except...

On every boot, both my /dev/sd[abcd] devices, and my /dev/video[01] devices swap around.

I have two capture cards, /dev/video0 and /dev/video1, and with every boot, they reverse (and it seems to be an exact swap on each boot -- they are never the same two boots in a row).

Additionally, I have four hard drives, /dev/sda through /dev/sdd, and they ALSO swap around (although I've only caught /dev/sdb and /dev/sdd swapping) on each boot.

The hard drives don't really cause a problem, since they are mounted by UUID, but the capture cards are annoying -- I have to run mythtv-setup after each boot to pick the right card.

Is there anything I can do about this?  udev rules or something to keep things sane?

I've searched everywhere, and I've found a few folks with this type of problem, but never any solutions...

Thanks in advance!

My /dev/sd* entries change all the time, but with UUID, who cares?

By the way ```
sudo blkid
``` gives a list of them all which is useful when adding a new disk.

The other problem is not as easy to solve. You neeed to set up udev rules. The rules are a bit "black magic" but are well documented elsewhere, eg here [http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

---

### Post by davelindquist on 2012-03-01
Thanks!

The hard drives were already using the UUID, so they didn't cause problems.  Just weird, thats all.

I followed the guide to set up udev entries for the video devices, and it seems to work perfectly.  Oddly enough, once I set up the udev rules (I created /dev/videoPVR150 and /dev/videoHVR1600), the /dev/video[01] devices suddenly stopped rotating with each boot.  Very weird.

Anyway, thanks!

---

