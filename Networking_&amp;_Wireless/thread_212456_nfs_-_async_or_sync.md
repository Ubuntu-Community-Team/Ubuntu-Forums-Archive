---
title: "nfs - async or sync?"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by Gotou on 2006-07-09
Hello!  I've got my Ubuntu (Dapper) computers sharing files using nfs.  As I was web searching for how to setup nfs, I came across some references to fstab mount options for "async" and "sync".  From what I gather "async" is slightly faster but unstable.  There will be times when I'm shuffling several gigabytes between my machines so any gains in speed is of interest.  Would someone explain "async" and "sync" in laymen terms?  I've read the man pages.  Unfortunately I'm still not familiar with Linux enough to grasp all the implications and possibilies.  I'm still experimenting with what I find on the Internet without really knowing what I'm doing.  Lack of sleep and too much coffee doesn't help my comprehension either.#-o 

At the moment here is what the nfs section of my fstab looks like . . .

Desktop Computer's fstab (to connect to laptop):
192.168.1.232:/home/mystuff /home/mystuff/laptop-cpu nfs nfsvers=3,rw,sync,rsize=32768,wsize=32768,hard,intr 0 0

Laptop Computer's fstab (to connect to desktop):
192.168.1.231:/home/mystuff /home/mystuff/desktop-cpu nfs nfsvers=3,rw,sync,rsize=32768,wsize=32768,hard,intr 0 0

Would "async" help or hinder?

Any other suggestions on increasing file transfer speeds?

Samba and ssh are projects for later.  I'd like to refine nfs for now.

Thanks!

---

