---
title: "Transfer Speeds (USB versus Internal Drive)"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by bsntech on 2009-08-01
I have found something quite strange with Ubuntu -

I have two internal drives; a standard ATA100 and also a SATA I drive.  I then have an external SATA II drive connected by USB 2.0.

When I transfer items from the ATA100 drive (this is where Ubuntu is loaded) to the USB drive, I get a transfer rate of approximately 20 MB/sec.

However, if I transfer files from the ATA100 drive to the internal SATA I drive, I maybe get a transfer rate of 4.3 MB/sec.

The ATA100 is a 320 GB WD drive.  The SATA I drive (motherboard only supports SATA I) is a recently purchased 1 TB WD Green drive.  Lastly, the external drive is a SATA II 500 GB WD drive.

Anyone have any thoughts on this matter?  Just doesn't make much sense to me that the USB drive is 5 times faster for transfer rates than an internal drive.

---

### Post by dlmarti on 2009-08-01
time dd if=/dev/zero of=file.txt bs=1M count=5000

will create a 5G file named file.txt, and give you the time it took to do it.

Do this three times for each drive to get an idea of whats going on.

---

### Post by dlmarti on 2009-08-01
Also remember that Linux caches the heck out of files, making simple transfers appear slower or faster depending on if the data is cached.

---

### Post by bsntech on 2009-08-03
Very good.  I tested three times and averaged their rates.  SATA-I drive shows 29.5 MB/sec.  IDE drive shows 43.55 MB/sec.  USB SATA-II drive shows 22.25 MB/sec.

So clearly the transfer rate is there.  I also tried another command that also tested transfer rate and the numbers were equally as well (can't recall the command used but it may have been hdparam).

But why would moving files cause such a difference in transfer speeds versus what these tests show?  Using even command-line or nautilus to move files, it takes just as long.

---

### Post by dlmarti on 2009-08-03
> **bsntech said:**
> Very good.  I tested three times and averaged their rates.  SATA-I drive shows 29.5 MB/sec.  IDE drive shows 43.55 MB/sec.  USB SATA-II drive shows 22.25 MB/sec.

So clearly the transfer rate is there.  I also tried another command that also tested transfer rate and the numbers were equally as well (can't recall the command used but it may have been hdparam).

But why would moving files cause such a difference in transfer speeds versus what these tests show?  Using even command-line or nautilus to move files, it takes just as long.

I have seen weirdness in drives auto-mounted into the /media directory.
I would suggest unmounting it, and manually mounting it in /mnt, and give another try.

---

