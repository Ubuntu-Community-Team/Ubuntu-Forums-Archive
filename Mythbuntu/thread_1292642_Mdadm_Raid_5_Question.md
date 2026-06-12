---
title: "Mdadm Raid 5 Question"
date: 2009-10-16
forum: Mythbuntu
---

### Post by Tim L on 2009-10-16
I currently have a Raid 5 using three 1 Terabyte Hard Disks using mdadm and it is almost full. My question is if it is better to grow the raid by adding another three Terabyte disks or to build a separate Raid 5 with three 1 Terabyte Hard Disks. Is one more secure than the other or is there any advantage?

---

### Post by ian dobson on 2009-10-16
Hi,

You could expand your existing array but that's abit risky, or your could create a new array and use Storage Groups to get mythtv to use both arrays.

Using 2 arrays would help your system in that the I/O over 2 partitions rather than one.

Regards
Ian Dobson

---

