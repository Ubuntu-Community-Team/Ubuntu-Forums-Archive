---
title: "Low throughput"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by vahuja4 on 2009-06-24
Hi All,

             I have two PCs connected back to back, and I ran uperf on them to test the UDP throughput. Both the PCs have 1Gig NICs. The problem is that using a single thread on the sending side, the throughput is only 115 Mb/s, and as I increase the number of threads, it goes upto 700 Mb/s. Am not able to understand what is hindering the throughput to reach near gig speed using a single thread. I am running both the PCs in recovery mode during the experiments. 

Please let me know how I should proceed with the investigation.

Thanks,
Vishal

---

### Post by jhannah on 2009-06-25
One thing to keep in mind is that NICs are rated in Gigabits, not Gigabytes. As such, the performance you are seeing from your NIC is actually really respectable. Is this not sufficient bandwidth for your needs? If so, there might be a better way to accomplish your goal.

---

