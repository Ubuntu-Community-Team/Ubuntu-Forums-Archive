---
title: "Network Transfer Speed only 11.3Mb/s"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by luceerose on 2011-06-19
I just noticed that files are transferring between my two computers at no more than 11.3Mb/s no matter what I do.

I regularly use sshfs to mount a drive on my main computer. But after noticing a dismal speed of 10Mb/s when copying a file, I thought maybe sshfs is slow.
So I tried scp, and I'm getting 11.3Mb/s with scp.
Using the blowfish cypher gave me no change to this, still exactly 11.3Mb/s.

I have a Gigabit network except for the cable, which is a 10meter, 100Mb/s cable.
I have a custom modified sysctl.conf file which I'll post here if needed.

Is there anything I can do about this pathetic speed ?
Maybe a modification to my ssh config ? sysctl ? anything ?

---

### Post by luceerose on 2011-06-19
Correction:

Speeds are;
ssh 11.3
sshfs 11.7
scp 11.3
scp -c blowfish 11.3

And I just spent a few hours teaching myself how to set up an NFS share to the same folder & guess what...

NFS 11.7 Mb/s (increasing block size made no difference)

I thought nfs was supposed to be, like, 6x faster than ssh.
Am I being limited by the speed of my 100Mb/s cable, or something ?
Anyone have any idea why I can't get a faster speed than this ?

---

