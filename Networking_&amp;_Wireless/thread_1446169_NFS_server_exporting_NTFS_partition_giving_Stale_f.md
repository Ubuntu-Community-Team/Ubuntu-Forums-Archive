---
title: "NFS server exporting NTFS partition giving Stale file error"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by bordaigorl on 2010-04-03
Hi!

I'm trying to setup a small network between my old and new laptops to transfer my personal data. They are now linked with a crossover cable and they see each other.
The old one has a dual-boot setup with WinXp and Ubuntu 9.10.
The new one with Win7 and Ubuntu 9.10.

I tried samba but it was very slow even using Windows in both computers: maximum transfer rates were about 1,5 Mib/sec.

I tried SSH using ubuntu on both pcs and it is reliable and much faster, 5 Mib/sec. But I wanted more...

I installed the NFS server on the old one and exported the NTFS partition where my data resides with sync and ro options.

I installed the NFS client on the new one and i'm able to mount the remote partition.

Now, when I transfer my files I get very high speed, more than 10 Mib/sec but after a while I get a "Stale NFS file handler" error but I really didn't touch any file in the old pc and the connection is always up.
Searching on the web I found that NFS had some troubles exporting NTFS partitions in the past but should be fully compatible with them since the last versions of ubuntu.

Is there any workaround for this issue? Am I missing something?

Thanks!

---

### Post by ThaddeusW on 2010-04-03
If you want, you can install cygwin on the old XP install and scp or rsync your files directly from windows. I use cygwin on all of my windows systems for backup purposes, works great. I get speeds of over 20 MBytes a second using gigabit. To maximize speed use blowfish encryption ("-c blowfish" for scp or "-e 'ssh -ax -c blowfish'") . There are stand alone rsync clients for windows as well, you could try one of those.

I kinda hate NFS and Samba. They work great, when they work that is. I only use them for streaming files like music or video. I use scp or rsync for most large file transfers. Good luck.

---

