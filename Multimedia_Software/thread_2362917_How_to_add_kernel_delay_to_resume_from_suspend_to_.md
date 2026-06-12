---
title: "How to add kernel delay to resume from suspend to deal with mt2sas host adapter delay"
date: 2017-06-03
forum: Multimedia Software
---

### Post by rramesh2 on 2017-06-03
I have mpt2sas host adapter that contains several disks used by mythtv. This host adapter needs time to recognize disks and make them available to kernel. When I resume from suspend, kernel is too fast and misses these disks. As a consequence when disks are assembled by mdadm in to a raid these disks shows as failed. Resulting array is degraded. I believe a kernel delay when it resumes should fix this. I want to know if I should use rootdelay or resumedelay kernel command line switch to accomplish this? What is the difference between the two and which one is most appropriate?  Ramesh

---

