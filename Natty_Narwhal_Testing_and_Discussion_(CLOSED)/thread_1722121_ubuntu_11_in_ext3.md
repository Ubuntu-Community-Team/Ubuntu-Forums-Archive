---
title: "ubuntu 11 in ext3"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by calchal on 2011-04-05
Hi everybody,

What if I install Natty (beta) or Maverick in ext3 HD format? Is it going to be slower?

---

### Post by psusi on 2011-04-05
Compared to?

---

### Post by cgroza on 2011-04-05
Compared to ext4 file system of course.

---

### Post by psusi on 2011-04-05
Some workloads are faster, some are slower.  For the most part, ext4 is faster, safer and more efficient.

---

### Post by kansasnoob on 2011-04-05
> **psusi said:**
> Some workloads are faster, some are slower.  For the most part, ext4 is faster, safer and more efficient.

I'd say possibly :confused:

I'm still cautious regarding ext4. I use my box quite often to transfer data from dead computers to USB drives and I still find ext3 to be more reliable - I think!

That "I think" is the key! I seem to notice that using ext4 sometimes I have trouble copying large partitions using Gparted, could that be related to this:

> Performance regressions with ext4 under certain workloads. The default file system for installations of Ubuntu 10.10 is ext4, the latest version in the popular series of Linux extended file systems. ext4 includes a number of performance tuning changes relative to previous versions such as ext3, the file system used by default up to Ubuntu 9.04. These generally produce improvements, but some particular workloads are known to be significantly slower when using ext4 than when using ext3. If you have performance-sensitive applications, we recommend that you run benchmarks using multiple file systems in your environment and select the most appropriate. 

That's from the Maverick release notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#File%20Systems%20and%20Disk%20Device%20Setup](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#File%20Systems%20and%20Disk%20Device%20Setup)

I'm not 100% sure, but I find ext3 to be very stable and in normal every day usage I can't tell the difference between the two.

I certainly think using ext3 is still OK and most people wouldn't notice the difference :D

---

### Post by mörgæs on 2011-04-05
> **psusi said:**
> For the most part, ext4 is faster, safer and more efficient.

Everything I have read seems to indicate that ext4 is faster, but slightly less safe than ext3.

---

### Post by whoop on 2011-04-05
I use ext3 for most systems. The only thing noticeably slower is a file system check. File system checks are a lot slower, however I only notice that when I'm waiting for a machine to reboot which doesn't happen that often...

---

### Post by ranch hand on 2011-04-05
I haven't used ext3 on Ubuntu for a long time.  Installed 9.04 on ext4 (optional at that time certainly not he default).

I still have that 9.04 install and have never, ever had any problem with ext4.

I am, right now, on Debian testing the partitions of which were copy/pasted from my external to my internal sdb drive using my old 9.04 gparted from my internal sda drive.   I have switched the drives so that this one is now sda and this is my main OS that I use 90% of the time.

I tested 10.04 on ext3 and ext4.  The ext4 installs were much improved over the ext3 installs.

You may guess that I kind of like ext4.

---

### Post by bjarkih on 2011-04-05
Regarding ext3 vs. ext4 I was told that it was easier to regain data from a damaged ext3 than an ext4 partion.  Is that true?

---

### Post by calchal on 2011-04-06
> **kansasnoob said:**
> I'd say possibly :confused:

I'm still cautious regarding ext4. I use my box quite often to transfer data from dead computers to USB drives and I still find ext3 to be more reliable - I think!

That "I think" is the key! I seem to notice that using ext4 sometimes I have trouble copying large partitions using Gparted, could that be related to this:



That's from the Maverick release notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#File%20Systems%20and%20Disk%20Device%20Setup](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#File%20Systems%20and%20Disk%20Device%20Setup)

I'm not 100% sure, but I find ext3 to be very stable and in normal every day usage I can't tell the difference between the two.


I certainly think using ext3 is still OK and most people wouldn't notice the difference :D

I once installed Lucid with ext3, but dont know the difference.
Regarding the stability, it happened to me the ext4 partition was broken when I forced the ubuntu to shutdown, and even I have run fsck to fix the partition, and eventually formatting it, still it left the trace of error: all linux distro (installed in other partition) and liveUSB/CD boot slowdown, particularly the one that used ext4 as default (slower than that used ext3). I must formatted the entire HD using Disk Utility to fix it. 
I search for the internet and found similar problems regarding forcing shutdown the Ubuntu 10 (that used ext4). 
But this was just happened in my netbook, there are no problems with ubuntu 10 in PC (forced shutdown, power blackout). And I dont know if older ubuntu with ext3 as default have similar problem.

This problem has led me to consider using ext3 when installing Natty, but eventually I used ext4 again anyway:tongue: (well, it suggests/persuades us to use it right?) :KS
Anyway, thanks for all your information and experience on ext3 vs ext4 comparison. :popcorn:

---

### Post by calchal on 2011-04-06
> **psusi said:**
> Compared to?

> **cgroza said:**
> Compared to ext4 file system of course.
 
Compared to ext4, i forgot to mention, thanks :)

---

### Post by psusi on 2011-04-06
Copying the whole partition with gparted is not actually using the fs.  It just copies every sector in the partition, and does not know or care about what fs is in it, so it does not matter whether it is ext3 or ext4.

The reasons ext4 is safer than ext3 are that it has io barriers enabled by default, and places checksums on the block group descriptors.  I still have not been able to understand why corruption on ext3 is not common place without io barriers.  Instead it seems to only happen occasionally.

> **bjarkih said:**
> Regarding ext3 vs. ext4 I was told that it was easier to regain data from a damaged ext3 than an ext4 partion.  Is that true?

No.

---

