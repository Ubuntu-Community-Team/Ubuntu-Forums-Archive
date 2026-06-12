---
title: "MP3-Player: Trekstor i.beat cebrax 2.0"
date: 2012-04-10
forum: Multimedia Software
---

### Post by LordJadawin on 2012-04-10
Hi,

some days ago I bought this device and it drove me crazy because I could not get it to play the files in the correct sort order.

I RTFM.
I looked it up in the FAQ on the official Trekstor site.
I renamed the files (suggestes by Trekstor FAQ).
I changed the ID3 tags.
Nothing helped ...

Finally I solved it and now I want to share the knowledge. ;)

The device uses a VFAT partition. Or at least that is the partition type I assigned when I cleaned the partition table - and it works. (by factory default the device had some 4 partitions - don't know why and what they were for - I like my partitions straight and simple)

The sort order of the files is obviousely controlled by the FAT table. Means the files are played in the same order as they are copied to the device storage (and therefore the same order as they are listed in the FAT table).

The problem now was/is that when you copy some files they are not necessarily written to the FAT table in alphapetical order. It depends on many things. File size (means copy duration), current state of write cache, priority of copy process and some more.

As a workaround I wrote a little bash script that copies files and directories to the MP3 player in alphabetical order and after each file it calls "sync" to make sure the write process is finished before it starts the next file.

This works for me and I hope I could help you with this little report.

---

