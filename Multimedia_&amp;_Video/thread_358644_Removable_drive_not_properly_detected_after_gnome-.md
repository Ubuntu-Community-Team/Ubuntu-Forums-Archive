---
title: "Removable drive not properly detected after gnome-vfs upgrade"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by fluffynuts on 2007-02-11
Good day

I hope this is the correct forum for this post (since removable media sort of fall under multimedia). If not, please feel free to flame away (but do at least point me at the "correct" forum).

I have a laptop drive in a standard usb-enabled housing, which I use on a regular basis with both an Ubuntu (Edgy) machine and a Fedora (Core 6) machine.

Until the most recent upgrade (libgnomevfs, to 2.16.1-0ubuntu7), everything was peachy. Now, when I plug in the removable drive, the drive isn't auto-mounted, and opening Nautilus to "Computer", and double-clicking the device that is detected yeilds:

"Unable to mount the selected volume"
(under "Show more details, we have:)
"error: device /dev/sdb1 is not removable"
"error: could not execute pmount"

Now, if I plug in a regular flash drive, things work as expected: the drive is detected and mounted (with the icon appearing on the desktop). This is obviously some bug introduced with parsing drive details. I'm not sure how libgnomevfs does it (and I'm unfortunately a little too busy to check the source right now), but a quick scan of /proc/scsi/usb-storage shows one file ("6") with the contents:

   Host scsi6: usb-storage
       Vendor: Genesys Logic
      Product: USB TO IDE
Serial Number: None
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks: GO_SLOW MAX_SECTORS_64

I have a workaround for the moment: I created the dir /mnt/MICRO (since, when this is fixed, I want the /media dir to be created and used as before), and I have an entry in /etc/fstab like so:

LABEL=MICRO             /mnt/MICRO              vfat            users,exec,defaults 0 0

So at least I can double-click the drive from nautilus and have it mounted for me. I would, however, far prefer the previous behaviour, since I like the niftiness of it, and I also don't see why a usb-to-ide device should be treated any differently than a regular flash disk.

---

