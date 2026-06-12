---
title: "Portable media player problem"
date: 2011-08-28
forum: Multimedia Software
---

### Post by steviefordi on 2011-08-28
I am using Ubuntu 10.04 (Lucid Lynx). My Daughter was given the Creative Zen Mozaic 4Gb media player for her birthday and I'm having a bad time trying to get it working with Ubuntu.

Upon plugging it in, it mounts into /media as a storage device. After putting the empty file .is_audio_player onto the root of the filesystem, rhythmbox detects it and shows it in the "devices" section.

Using rhythmbox to transfer music to the device works, but when using the device all tracks are filed under "Unknown Artist" and "Unknown Album" even though in rhythmbox they are tagged correctly.

Can anyone help me get this device working properly?

Things I have tried:
Installing the mtpfs and mtp-tools packages - made no difference
Using Gnomad2 (as root after unmounting the device gave me "No jukebox found" error)
Using Amarok - can't seem to work this software
Copy and paste using nautilus - (same result as using rhythmbox)

mtp-detect gives:
```
libmtp version: 1.0.2

Listing raw device(s)
   No raw devices found.

```

In case it is of interest, here is the output of tail -f /var/log/messages
when I plug the device in:
```
[ 6379.570861] scsi 17:0:0:0: Direct-Access     Creative Mozaic EZ Series 0100 PQ: 0 ANSI: 4
[ 6379.576731] sd 17:0:0:0: Attached scsi generic sg3 type 0
[ 6379.592747] sd 17:0:0:0: [sdc] 960768 4096-byte logical blocks: (3.93 GB/3.66 GiB)
[ 6379.593633] sd 17:0:0:0: [sdc] Write Protect is off
[ 6379.595882] sd 17:0:0:0: [sdc] 960768 4096-byte logical blocks: (3.93 GB/3.66 GiB)
[ 6379.596701]  sdc: sdc1
[ 6379.613192] sd 17:0:0:0: [sdc] 960768 4096-byte logical blocks: (3.93 GB/3.66 GiB)
[ 6379.614660] sd 17:0:0:0: [sdc] Attached SCSI removable disk

```

lsusb gives the device as:
```
ID 041e:201c Creative Technology, Ltd
```

I'm at my wits end, any help would be greatly appreciated!

---

### Post by steviefordi on 2011-08-29
bump

---

### Post by mahavishnu on 2011-09-17
Same problem here.
I can't mount a Sony Walkman E345 in MTP Mode.

---

### Post by steviefordi on 2011-09-19
I never got this to work with MTP, however I did get it to file MP3 files properly index under the artist, album etc.

The problem was the ID3 tags were written by gstreamer as version 2.4. My player only reads up to version 2.3.

I used EasyTag (check the repos) to edit them to 2.3, and hey presto the device indexed everything properly!

If you're comfortable on command line you could try eyeD3 to convert version 2.4 to 2.3 with the code handed to me here:

[http://ubuntuforums.org/showthread.php?t=1837237]("http://ubuntuforums.org/showthread.php?t=1837237")

---

