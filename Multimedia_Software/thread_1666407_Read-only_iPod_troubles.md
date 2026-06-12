---
title: "Read-only iPod troubles"
date: 2011-01-13
forum: Multimedia Software
---

### Post by floundering on 2011-01-13
I've been using the sixth gen (160gb) iPod on Ubuntu for about a year  through Rhythmbox without too many problems, but the other day Rhythmbox  stalled during a music transfer, and I made the mistake of unplugging  my iPod. Whoops.

Now, the iPod itself doesn't recognize the music I've transferred, and  those songs don't show up in Rhythmbox. I can manually play stuff from  the iPod directory once it's mounted, so the files are definitely on  there. I thought maybe the hard disc was corrupted, so I ran a  dosfsck...it fixed some damaged cluster, awesome, except Rhythmbox and  the iPod itself still won't display anything. I realized that it was  somehow set to "read-only" after this disconnect, which means I can't  even manually replace everything. Hum-ho.

What should I do to restore my music collection?

---

### Post by floundering on 2011-01-13
Someone mentioned I could fix this on a windows machine, but didn't really explain what they meant. Is there a specific program I should use to check the hard disc?

---

### Post by Chronon on 2011-01-14
Restoring with iTunes will write a new partition table, reformat the data partition and install a new firmware to the firmware partition.  

File system damage should be fixable by dosfsck (or fsck.vfat), though.  Does it scan cleanly now?  Mounting as read-only usually indicates a damaged file system.

---

### Post by floundering on 2011-01-14
This is the output of a dosfsck:
/dev/sdc1: 3994 files, 1815273/9751091 clusters

So that means the file system isn't corrupted because I didn't see any error messages?

---

### Post by floundering on 2011-01-14
This is the output of a dosfsck:
/dev/sdc1: 3994 files, 1815273/9751091 clusters

So that means the file system isn't corrupted because I didn't see any error messages?

---

### Post by floundering on 2011-01-14
.

---

### Post by floundering on 2011-01-14
This is the output of a dosfsck:
/dev/sdc1: 3994 files, 1815273/9751091 clusters

So that means the file system isn't corrupted because I didn't see any error messages?

---

### Post by Chronon on 2011-01-15
Yeah.  That seems clean.  

See if this helps:
[https://help.ubuntu.com/community/Mount/USB#USB-Device%20is,%20or%20become%20suddenly%20read%20only%20without%20errors](https://help.ubuntu.com/community/Mount/USB#USB-Device%20is,%20or%20become%20suddenly%20read%20only%20without%20errors)

---

### Post by floundering on 2011-01-16
I ran a dmesg. This looks like the relevant bit.
```

[40042.439688] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[40042.441216] sd 6:0:0:0: Attached scsi generic sg2 type 0
[40042.444748] sd 6:0:0:0: [sdc] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[40042.445357] sd 6:0:0:0: [sdc] Write Protect is off
[40042.445365] sd 6:0:0:0: [sdc] Mode Sense: 68 00 00 08
[40042.445370] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[40042.446746] sd 6:0:0:0: [sdc] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[40042.447235] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[40042.447244]  sdc: sdc1
[40042.486909] sd 6:0:0:0: [sdc] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[40042.487481] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[40042.487491] sd 6:0:0:0: [sdc] Attached SCSI removable disk

```I notice if write protect is off without any visible file system errors, the page suggests altering the mount settings for /etc/usbmount.conf, but that file doesn't exist. What file should I fiddle with instead and how should I edit the settings?

---

### Post by floundering on 2011-01-18
Any ideas?

---

### Post by floundering on 2011-02-05
Someone told me that I can fix my iPod by uploading stuff to it from another computer, though that would erase the files on the iPod. Now that university's started up again, I have access to a few windows computers, and at this point, I'm completely ok with wiping my iPod clean and manually reuploading my music collection if that means I can have a functional iPod. How can I do that?

---

### Post by johntaylor1887 on 2011-02-05
There is a restore function in itunes. Just hook up your ipod, open itunes, and look for the restore function.

---

