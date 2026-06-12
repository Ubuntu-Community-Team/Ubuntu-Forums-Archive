---
title: "slow read/write with ecryptfs"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by drmartens on 2010-10-03
Hi

I'm aware, that ecryptfs tends to slow things down, but I'm a bit disappointed anyway, here's why:

I've bought new SSD drive for maverick - ocz vertex 2, which is capable of max 275MB/s read/write (benchmarked on Ubuntu before partitioning - with similar results for read and write) and installed maverick RC with encrypted home parition. 
I aligned both root and home partitions properly and mount them with discard option to enable TRIM.

I have a second sata drive in ultrabase (lenovo x200), which is capable of ~ 100MB/s read (WD Scorpio Black 500GB). OK, so the secondary drive holds my backup files (encrypted through ecryptfs), so I mounted the backup and started copying to SSD - max write speed on my SSD was 33MB/s - for both small and big (>2GB) files.

The I decided to move some files inside my encrypted home to see the speed - it was the same for all my tests - max 33MB/s.

Then I decided to copy file from my encrypted home to unencrypted /tmp - as you could guess, that's faster - in my case ~ 80MB/s.

I will probably create another unencrypted partition to do more testing (my root partition is too small), but my limited tests indicate that ecryptfs slows my SSD drive at least 2 times.

I'm aware that benchmarks I mentioned concern seq read/write but still, 30MB/s feels quite slow, especially that I could achive much more outside ecryptfs with the same operations...The system overall is quite fast - much faster then my previous 5400 RPM drive. This is also my first SSD drive ever and my first 64bit Ubuntu (and I've been using Ubuntu for what, 5 years?).

Of course, the winners in the slowest (startup) performance ever are the same guys as usual - gnucash and liferea. They are simply HORRIBLE and I feel like I'm running some 10 year old hardware. How complicated can be an RSS reader with like 50 feeds total to be THAT slow?!

Apart from that, I love how quiet my system is now and how the CPU fan has finnaly STOPPED SPINNING LIKE CRAZY. Maybe it's maverick magic, but I'm almost positive it's due to SSD. Anyway, I've been using ecryptfs from the very introduction in Ubuntu -  since Intrepid - and I will probably reconsider if it really makes sense to encrypt my whole home and loose so much drive speed. Maybe I'll move back to what was done in Intrepid - encrypted Private directory with symlinks...After all, I don't have to encrypt my gnome configs etc.

Hope to hear more from people using SSD and ecryptfs. Maybe I missed something in terms of tuning?

Cheers

---

### Post by cariboo on 2010-10-03
From the sounds of it, there may be a bottleneck elsewhere in the system. What are the results if you run the following command, as your system is now?

```
time dd if=/dev/zero of=filename bs=1024 count=1000000 
```

The results should look like this, but faster of course:

```
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 14.497 s, 70.6 MB/s

real	0m14.618s
user	0m0.140s
sys	0m4.710s
```

---

### Post by drmartens on 2010-10-03
Hi, thanks for the reply. Results are horrible for ecryptfs and wonderful for the unencrypted part:

running your command in ~ (encrypted):
```
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 51.601 s, 19.8 MB/s

real	0m51.605s
user	0m0.280s
sys	0m49.400s
```

running your command in /tmp (unencrypted):
```
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 3.6165 s, 283 MB/s

real	0m3.686s
user	0m0.190s
sys	0m2.910s
```

Which clearly tells me, something is wrong with ecryptfs, which is 14 times slower in the test above.
Let me also add, that it is a fresh install, disk was secure erased before installation (with hdparm). Nothing I/O significant in the background.

I've never benchmarked ecryptfs before. However I still have my Lucid installation on a different drive and maybe I'll run this test later, just out of curiosity.

Thanks!

---

### Post by cariboo on 2010-10-03
There is something definitely not right there, the last time I ran with an encrypted home, the delay was barely noticeable.

---

### Post by drmartens on 2010-10-04
I changed my drives and booted Lucid (old 5400 RPM drive):

```
Linux 2.6.32-25-generic-pae 686 GNU/Linux
```

encrypted home partition:
```
time dd if=/dev/zero of=filename bs=1024 count=1000000
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 89.7334 s, 11.4 MB/s

real    1m29.739s
user    0m0.248s
sys 0m58.100s
```

unencrypted root partition (/tmp):
```
time dd if=/dev/zero of=filename bs=1024 count=1000000
1000000+0 records in
1000000+0 records out
1024000000 bytes (1.0 GB) copied, 47.7698 s, 21.4 MB/s

real    0m48.069s
user    0m0.240s
sys 0m4.444s
```

So, my new SSD drive is 13 times faster on unencrypted fs and not even 2 times faster on encrypted fs. Clearly it has to be some sort of bug? I'd like to file a bug report, but against which package? ecryptfs-utils? kernel?

---

### Post by cariboo on 2010-10-04
You may want to create a bug against ecrypt-utils.

---

### Post by drmartens on 2010-10-04
OK, I did. If anyone is interested:
[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/654764](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/654764)

I hope it will get some attention, even though it's probably pretty hot at Canonical at that time :)

---

