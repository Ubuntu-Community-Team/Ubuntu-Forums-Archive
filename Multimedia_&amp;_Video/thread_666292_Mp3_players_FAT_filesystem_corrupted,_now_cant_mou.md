---
title: "Mp3 players FAT filesystem corrupted, now cant mount except as read-only"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by Mr.Auer on 2008-01-13
I have a Creative Zen Stone Plus 2GB mp3 player. As I was deleting files from it, it unmounted itself forcibly even thou it was plugged in. After this it will only mount as read-only even if I mount it by hand with "mount -t vfat -rw /dev/sdb1 /root/stone".

dmesg gives.
"[  727.015307] usb 2-2: new high speed USB device using ehci_hcd and address 4
[  727.131106] usb 2-2: configuration #1 chosen from 1 choice
[  727.243192] usbcore: registered new interface driver libusual
[  727.299337] Initializing USB Mass Storage driver...
[  727.301995] scsi2 : SCSI emulation for USB Mass Storage devices
[  727.304822] usb-storage: device found at 4
[  727.304830] usb-storage: waiting for device to settle before scanning
[  727.305445] usbcore: registered new interface driver usb-storage
[  727.305452] USB Mass Storage support registered.
[  732.303106] usb-storage: device scan complete
[  732.303842] scsi 2:0:0:0: Direct-Access     CREATIVE ZEN Stone Plus   1031 PQ: 0 ANSI: 4
[  732.306192] sd 2:0:0:0: [sdb] 971264 2048-byte hardware sectors (1989 MB)
[  732.306816] sd 2:0:0:0: [sdb] Write Protect is off
[  732.306820] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  732.306823] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  732.308811] sd 2:0:0:0: [sdb] 971264 2048-byte hardware sectors (1989 MB)
[  732.309437] sd 2:0:0:0: [sdb] Write Protect is off
[  732.309442] sd 2:0:0:0: [sdb] Mode Sense: 38 00 00 00
[  732.309444] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  732.309452]  sdb: sdb1
[  732.310859] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  732.311612] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  734.087114] FAT: Filesystem panic (dev sdb1)
[  734.087123]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.087128]     File system has been set read-only
[  734.089364] FAT: Filesystem panic (dev sdb1)
[  734.089372]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.100503] FAT: Filesystem panic (dev sdb1)
[  734.100516]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.102503] FAT: Filesystem panic (dev sdb1)
[  734.102513]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.103935] FAT: Filesystem panic (dev sdb1)
[  734.103944]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.110104] FAT: Filesystem panic (dev sdb1)
[  734.110113]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.111625] FAT: Filesystem panic (dev sdb1)
[  734.111633]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.113005] FAT: Filesystem panic (dev sdb1)
[  734.113013]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  734.114350] FAT: Filesystem panic (dev sdb1)
[  734.114358]     fat_get_cluster: invalid cluster chain (i_pos 0)
root@Sammakko:~# 
"
And fsck gives:
"root@Sammakko:~# fsck -f -v /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
      2048 bytes per logical sector
     16384 bytes per cluster
        32 reserved sectors
First FAT starts at byte 65536 (sector 32)
         2 FATs, 32 bit entries
    487424 bytes per FAT (= 238 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 1040384 (sector 508)
    121337 data clusters (1987985408 bytes)
56 sectors/track, 64 heads
        56 hidden sectors
    971208 sectors total
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
/fanusamurai - focused mind
  Contains a free cluster (803). Assuming EOF.
/bill laswell - dub chamber 3
  Contains a free cluster (7687). Assuming EOF.
/burial - untrue
  Contains a free cluster (8787). Assuming EOF.
/Spirallianz - Stereopark - 2003
  Contains a free cluster (16290). Assuming EOF.
/Ceebrolistics - O
  Contains a free cluster (16863). Assuming EOF.
/The Future Sound Of London -- Papua New Guinea Translations
  Contains a free cluster (22834). Assuming EOF.
/the_future_sound_of_london-from_the_archives_vol._4-(fdig13)-web-2007-1real
  Contains a free cluster (26029). Assuming EOF.
/Murmurecordings - Escapemodule
  Contains a free cluster (33770). Assuming EOF.
/lusine icl - coalition 2000
  Contains a free cluster (44003). Assuming EOF.
Reclaiming unconnected clusters.
Reclaimed 8120 unused clusters (133038080 bytes) in 14 chains.
Checking free cluster summary.
Leaving file system unchanged.
/dev/sdb1: 111 files, 72582/121337 clusters
root@Sammakko:~# 
"

But fsck wont repair anything either, as the drive is read-only. Gparted does not see the volume, it only shows an unpartitioned space of 400+ megs as /dev/sdb1.

How could i get fsck to repair the errors? Or get it mounted as read-write= Or format the drive? Or can you even format it, or will that wipe the players firmware as well?

---

### Post by Mr.Auer on 2008-01-14
I got the player working again by going over to a friend who dualboots, and formatting the Zen to FAT 32 on Win XP. It took at least 5 minutes for the drive to show up in XP, but when it did show I could easily format it. After formatting it now works again and will automount as read/write in Ubuntu as well.

Before formatting, in Ubuntu I couldnt get the drive to show up in Gparted, and I didnt manage to format it otherwise either or mount it read/write. If anyone has any advice, id love to hear it - Im sure this is gonna happen again, since the player is just a few days old :(

---

### Post by Tur Third on 2008-01-15
I had a similar experience. I have a 2gb mp3 player. I was copying files onto it last night.

Many of the new files didn't show up on the player, but did in Nautilus. They seemed to have strange permissions, so I tried to change them. This seemed to make things worse.

The disk also did not show up in Gparted.

In the end I reformatted on a Windows PC. As this has happened before, I have decided to format as FAT rather than FAT32 to see if this helps. I might have a dodgy mp3 player though.

---

### Post by Tur Third on 2008-01-17
Very odd, after copying lots of files across, the MP3 player becomes read only. It also seems that after it is about half full files start corrupting file names and  has strange permissions.

I have reformatted on a Windows pc (FAT32 now), and tested filling it with other files and not had problems in Windows.

My guess is some incompatibility with the firmware on the MP3 player and Linux, or possibly it may be illegal characters for windows. I have used a number of smaller mp3 players and USB sticks without problem.

I am interested to know if you still have a problem..

---

### Post by Mr.Auer on 2008-01-17
After formatting again to FAT 32 in Windows its worked fine. Ive moved files to the player and removed old ones. Now Im making sure not to use any extension cable between the player and usb connector either, if that would help. I also got a new amd dualcore comp so lets see if it works better with this new motherboards USBs...

Ive never had problems with either flash sticks or USB hard drives either, only Ipod shuffle before and now Zen Stone exhibiting this self-unclean-unmounting behviour that drives me nuts :p (Shuffle died to this)

---

### Post by Mr.Auer on 2008-02-24
Now Ive been using the Zen Stone Plus for a while after the reformat in Windows. I havent had any more problems: the player has mounted and unmounted cleanly every time. I dont know if I should have formatted it before using - dont know if there was something odd in the FAT format it used etc..

My previous player (Ipod shuffle) died pretty much like this - it started unmounting itself in the middle of file transfers, then became read-only, needed a reset on Win or Mac, and then in the end the reset utility from Apple crashed in the midst of resetting on Windows, after which the Ipod is totally bricked. No lights, no power, no sound. Dead.

The Zen Stone has so far been easier than the Shuffle, but well see...I think the best bet would be to buy a Cowon player if you can - they at least say on their web pages that Cowons support Linux.

What weirded me out most is that I couldnt format the Zen under Linux. It for some reason refused to mount it readwrite or format no matter what I did...This may well be some firmware incompatibility etc..In any case, if the Zen borks out on me, it still cost me half what the Shuffle did...

At this point I cannot rule out some problem with the old mobo and its USB ports. With my new comp the player has worked flawlessly...

---

