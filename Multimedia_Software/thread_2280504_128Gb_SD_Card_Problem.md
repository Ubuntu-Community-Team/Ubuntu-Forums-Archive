---
title: "128Gb SD Card Problem"
date: 2015-05-31
forum: Multimedia Software
---

### Post by typos1 on 2015-05-31
I ve just got a 128 Gb SDHC card. It was formatted in exFAT, so I re-formatted in FAT32 (I m going to put my music on it so want it compatible with as many devices as possible). 
I reformatted with the "Disks" utility. 
After I had done this I realised that I had reformatted the entire card and not left the small "empty space" partition, the card had originally, I checked my other SD cards and they all had a small "empty space" partition, so I was a bit worried I d messed it up, but Ubuntu seemed happy to read and write to it, so I copied 90 odd Gb of files to it. 
It took about 8 hours to copy form a USB hard drive to the card, the card is class 10, but I guess as USB 2.0 is quite slow this is why it took so long, it started at 4.6Mb/ps but soon slowed to 2.6Mb/ps. 
After it had finished everything looked ok and it reported the correct amount of free and used space. I opened a folder and all the tracks in it showed up, several music players would open the tracks and "play" them but there was no sound. 
So I ejected the card and plugged it in again, this time all the used unused space was reported ok, but every folder is now empty, theres nothing in them at all and I cant put anything on it now, the item just goes back to where it was if I drag and drop or it reports as read only. 
I rebooted, still have the same problem.
Checking "hidden files" in Nautilus dos not make anything show up.
Right clicking "properties" results in the whirly wheel going round and round for ages (at least 20 mins before I stopped it) but no number of items or amount of storage used shows.

Have I broken it ? Anyone got any suggestions ?

Thanks

---

### Post by ajgreeny on 2015-05-31
This will not really help, but I do not use the "disks" utility to format anything and much prefer to install gparted and use that instead; it is much more flexible and is fine for dealing with external disks that you can unmount without difficulty.

As for this loss of your data (which I trust is still available elsewhere) I am not sure what to say, apart from asking you if the card had completely finished the job of writing the files.  If you had simply tried to unmount the card before removing it, it would have warned you if there were still things happening and it would not have unmounted; I am not sure if the same warning occurs when you reboot, though my gut feeling is that it would do so.

It is worth installing and using gparted to see what that finds on the card, and you can even use it, I think, to recover partitions, though maybe not to recover files.

PS:  Just a thought; did the card have any encryption utilities on it when you first had it that are still required to allow you to read the files on it?

---

### Post by typos1 on 2015-05-31
I do have Gparted, I just used Disks. I dont format much and forgot about Gparted. After I d reformatted it and written the files Gparted said the same as Disks apart from it reported 125Gb not the 134Gb Disks was saying.

Wasnt sure whether the data was lost as the folders were there and apparently empty, but Ubuntu was saying 90Gb was used. I put it in an Android device and it said it was empty, just a Lost Dir folder. Then when I put it back in my pc Ubuntu said it was empty as well.

It took 8 hours to write it all (I do have a copy) and I didnt remove it until Ubuntu sai it had finished writing it.

When I first used it, according to Disks, the card was blank and it had 2 partitions on it, about 2.7Mb of "Empty space" and another of 134Gb, even though the card is supposed to be 126Gb.

Edit: Nautilus says its a 132.4Gb device. Gparted says 1.67 Gb is used, but Nautilus and Disks now says its empty. Ubuntu says its a "134Gb volume" ! ? Trying to recover files results in Gparted hanging.

---

