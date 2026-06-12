---
title: "Apt and Dpkg failure on AOE-booted system"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by becvert on 2009-10-25
Hi,

I'm having an issue with apt on my Ata-Over-Ethernet-booted system. I cannot use apt-get update or upgrade. It gives me segmentation faults. And when I try dpkg, the process becomes unresponsive (status D). I tried removing the apt cache but it did no fix the problem.
When I boot locally the system, by reattaching the hard drive (which was on the AOE target) to my VM in VMWare, it works.

The AOE target is Karmic. So is the network-booted system.
Both systems have been installed as "command-line" systems from the alternate beta 9.10 ISO for amd64. 

I had used NFS/TFTP netbooting previously and I hadn't have any issues with packaging from the NFS server or from the client.

I need some help. Thank you.

---

### Post by becvert on 2009-10-31
I fixed the issue. For some reason dpkg was waiting for a response from a CD drive (uninterruptible process D+). But I don't have any on my netboot pc.
So I mounted a network drive (mount -t cifs //10.1.1.3/dvd /media/cdrom0). And it solved the problem!
What I found strange is, as I said, I used to netboot via tftp and nfs on the exact same machine without optical drive and it used to work. The tftp/nfs server was Hardy and the netbooted machine was mythbuntu 9.10.
AOE has probably nothing to do with that issue though.

---

### Post by becvert on 2009-11-07
nope. that wasn't the solution. Strangely enough I thought I fixed the stuff but I'm actually back to square one.
I can't use dpkg on any AoE netbooted machine. I've tried to AOE boot on another machine with has a cd drive, keyboard and mouse but id does not change a damn thing.
Looking at strace log it seems that it gets stuck while reading the /var/lib/dpkg/status file. which would indicate that it is malformed or corrupted. But what I don't understand is that this issue does not exist as soon as I boot locally.
there must be a glitch with the mount options of my primary partition.

/dev/etherd/e0.0p1 / ext4 sync 0 0

---

