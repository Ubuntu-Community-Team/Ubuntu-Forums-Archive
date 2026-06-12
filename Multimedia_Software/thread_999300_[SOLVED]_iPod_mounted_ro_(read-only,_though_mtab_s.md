---
title: "[SOLVED] iPod mounted ro (read-only, though mtab says rw)"
date: 2008-12-01
forum: Multimedia Software
---

### Post by kc600 on 2008-12-01
When i plug in my iPod it gets mounted (at /media/iPod), but the mount options as viewed through the "properties" on the desktop icon show it's mounted read-only: the volume tab says "mount options: ro nosuid nodev umask=22 uid=0 gid=0 nls=utf8". 

This puzzles me, because /etc/mtab contains a line "/dev/sdf2 /media/iPod hfsplus rw,nosuid,nodev,uhelper=hal 0 0".

I tried "sudo dosfsck -a /dev/sdf2", which yielded
```
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Logical sector size is zero.
```
But no different behaviour.

This is a 80Gb Classic iPod. I think its firmware may be newer, though:  My girlfriend (ok, it's _her_ iPod) took it back to the shop because the "hold" button seemed to jam, and the girl in the shop, as she put it, "reset" it. After this, all music was gone. So i'm thinking, maybe she completely blanked it and she possible installed newer firmware.

Its contents are now:
```
/media/iPod/
|-- Calendars
|-- Contacts
|-- Notes
|   `-- Instructions
|-- Recordings
`-- iPod_Control
    |-- Device
    |   |-- Preferences
    |   |-- SysInfo
    |   |-- alarms
    |   `-- clock
    |-- Music
    |   |-- F00
    :   : (skipped some here)
    |   `-- F49
    |-- Tones
    |   `-- Beep.tone
    |-- iPodPrefs
    `-- iTunes
        |-- Rentals.plist
        |-- iTunesControl
        |-- iTunesDB
        `-- iTunesPrefs
```

Does this ring a bell? What else could i check?

---

### Post by Rodney9 on 2008-12-01
I had similar problems here - [http://ubuntuforums.org/showthread.php?t=991821](http://ubuntuforums.org/showthread.php?t=991821)

I now use [Rockbox]("http://www.rockbox.org/") on my iPod Nano, works brilliantly, Thanks DirtDawg

---

### Post by kc600 on 2008-12-02
Nice thought, 5th gen Classic not supported though.

---

### Post by againstdemons84 on 2008-12-04
> **kc600 said:**
> When i plug in my iPod it gets mounted (at /media/iPod), but the mount options as viewed through the "properties" on the desktop icon show it's mounted read-only: the volume tab says "mount options: ro nosuid nodev umask=22 uid=0 gid=0 nls=utf8". 

This puzzles me, because /etc/mtab contains a line "/dev/sdf2 /media/iPod hfsplus rw,nosuid,nodev,uhelper=hal 0 0".


I have the same problem and the nice people at #ubuntu-uk have told me that writing to HFS (hfsplus in mtab) in Linux isn't the way to go. They recommend that I fire it up in windows, reset it and reformat to NTFS.

I wasn't expecting NTFS to be the answer to this problem!

---

### Post by kc600 on 2008-12-04
Solved it: Linux can't (yet) deal with journaling hfs+ filesystems yet. So i found someone with a Mac, connected the iPod and ran diskutil disableJournal /Volumes/iPod. After that, my iPod automatically mounts rw.

---

### Post by gorgon on 2008-12-15
Hi!

Ive tried turning off journaling hfs+, but my ipod still mounts as read only. Ive just installed ipodlinux :D and dont want to reformat to fat32.

Anyone got suggestions? can I chmod it from a mac??

---

### Post by gorgon on 2008-12-15
oohyes! solved it!

seems i needed to run fsck on the ipod drive.

so i got the hfsprogs package from synaptics
used
```
df -h
```

which gave me this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.7G  9.0G  413M  96% /
varrun                483M  124K  483M   1% /var/run
varlock               483M     0  483M   0% /var/lock
procbususb            483M  124K  483M   1% /proc/bus/usb
udev                  483M  124K  483M   1% /dev
devshm                483M   12K  483M   1% /dev/shm
lrm                   483M   35M  448M   8% /lib/modules/2.6.22-14-rt/volatile
/dev/sda1              32G   32G  147M 100% /media/sda1
/dev/sda5              40G   35G  4.4G  89% /media/sda5
/dev/sda6             4.9G  2.6G  2.1G  56% /media/sda6
/dev/sdb3              38G   82M   38G   1% /media/MacPod

which told me that my 'MacPod' lives in /dev/sdb3

then this did the whole trick:
```
sudo fsck.hfsplus -r /dev/sdb3
```

a nice, though bit outdated how to is also here:
[http://ubuntuforums.org/showthread.php?p=1859336](http://ubuntuforums.org/showthread.php?p=1859336)

yueeha!

---

