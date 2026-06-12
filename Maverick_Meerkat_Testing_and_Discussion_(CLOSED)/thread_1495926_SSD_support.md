---
title: "SSD support?"
date: 2010-05-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2010-05-28
In the Lucid Lynx testing forum, no one seemed to know for sure whether TRIM worked on Lucid. Meerkat is using 2.6.34 so TRIM will be supported? I just purchased a SDD. I think all I need to do is add "discard" to the mount params.

---

### Post by antiram on 2010-05-29
discard should work. you can test it with:
get the sectors of a file:
hdparm --fibmap filename
read a used sector eg.
hdparm --read-sector 66385920 /dev/sda
remove file and sync:
rm filename;sync
and read the sector again. 
a trimmed sector on my indilinx drive contains nulls

---

### Post by andrewabc on 2010-05-30
When creating partitions etc, does it partition the SSD properly?

Do we still have to manually create partitions to make sure uses specific sectors?

Back in February I made this thread:
[Linux Not Fully Prepared for 4096-Byte Sector Hard Drives](http://ubuntuforums.org/showthread.php?t=1407098&highlight=sector)
Does it support these types of drives yet without having to manually partition to specify sectors?

---

### Post by MacUntu on 2010-05-30
I've read somewhere that 10.04 already automatically aligns the partition properly, so you should be fine with just adding the "discard" mount option. You could also add the "noatime" option to reduce writes/raise performance.

---

