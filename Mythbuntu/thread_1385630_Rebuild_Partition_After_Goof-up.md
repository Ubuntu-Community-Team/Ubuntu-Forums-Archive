---
title: "Rebuild Partition After Goof-up"
date: 2010-01-19
forum: Mythbuntu
---

### Post by elliott6 on 2010-01-19
Hey All,

Simple version here - 

If a partition was removed, assigned to a different setup (in this case, possibly a RAID array), but no formatting, building, etc. took place, is it possible to recover the data by recreating the partition, perhaps overlaying a partition of the same size?  I have not erased the data, or formatted, and I have been holding back on random "recovery efforts" I have read on the internet until I got a more concrete response.

Results of the following commands (without the irrelevant details) - 

sudo fdisk -lu
Disk (in question) doesn't contain a valid partition

sudo sfdisk -d
sfdisk: ERROR, Sector 0 does not have a valid MSDOS signature
(Disk in question) Unrecognized partition table type

sudo parted /dev/sda print
Error: unrecognised disk label

testdisk - did not show any partitions with Analysis either a Quick Search or Deeper Search

Sorry for the paraphrasing, the server is in the basement (for rehab) and not connected to the internet.

Please let me know, as I am afraid I have lost 1.5TB of recordings!

Sean


Details - 

Running Mythbuntu, I decided to upgrade my storage to use hardware RAID. With a Perc 5i, I have one set of inputs connected to 3 1TB drives, and 2 of the other set of 4 connected to 1.5TB drives. There is a third 1.5TB drive to add so I can have 2 RAID5 arrays, but it currently has/had my recordings on it.  I plan to move the recordings to the 3x1TB, and setup videos, music, dvds, and other on the 3x1.5TB.  So first was to setup the 3x1TB, move the recordings over, then repurpose the 1.5TB to the other array.

I may have messed up and incorrectly connected the 1.5TB drive with my current recordings to the Perc RAID card. And yes, I (getting ahead of myself) did create a virtual disk on the Perc card with the 2 1.5TB drives as RAID0 with the intention of adding the third disk once I copied the recordings to the 3x1TB RAID5 array, thus creating and converting to the 3x1.5TB RAID5 array. NO, I did not format, copy, or anything else with the 2x1.5TB RAID0 array. I didn't get far enough, as I was looking for my recordings so I could transfer them.

I am now getting the following - 

fsck died with exit status 8
File system check failed
Please repair the file system manually
A Maintenance shell will now be started
CONTROL-D will terminate this shell and resume system booy.

I know my UUID is incorrect, and I can fix that.  However, when I connect the 1.5TB drives separately (off the mainboard), Partion Editor shows they are empty with no partitions, as I know 1 of the 3 1.5TB had a XFS partition with my recordings on it. 

My question is whether it is possible to get my recordings back as it appears I may have wiped the "table of contents" boot record when it was added to the hardware RAID array? I believe, in my search, mention was made to try testdisk (showed no partitions at all), e2fsk as well as some others, but I thought I would write this out for suggestions before I go aimlessly executing commands from responses read on the internet, ultimately making it worse/totally unrecoverable.

Appreciate everyone's time and help! Sorry (and thanks if moved) if this is the wrong forum for this. 

Sean

---

