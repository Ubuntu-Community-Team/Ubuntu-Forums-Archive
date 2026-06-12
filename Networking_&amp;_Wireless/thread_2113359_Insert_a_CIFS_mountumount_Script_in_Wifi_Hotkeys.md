---
title: "Insert a CIFS mount/umount Script in Wifi Hotkeys"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by jakfish on 2013-02-07
Lubuntu 12.04/ASUS EEE 900

Using mount.cifs or an fstab entry, I am successfully accessing a r/w windows xp shared directory.

The trouble is I work on battery and often disable wifi to conserve power.  If I don't re-enable wifi before shutdown, my shutdown freezes because lubuntu is trying to unmount a network share that is no longer accessible.

In the FN-F2 hotkey scripts, I would like to put in these two commands:

If wifi is enabled, then:

sudo mount.cifs //192.168.1.22/efile /mnt/efile -o user=domain\\username,pass=guest

But if wifi is *disabled*, this command would have to run before any part of the disabling:

umount /mnt/efile

Is this possible, and which files would need editing?  (Previous experimenting with unmounting CIFS shares just before attempting shutdown doesn't work if wifi is not enabled)

Many thanks,
Jake

---

