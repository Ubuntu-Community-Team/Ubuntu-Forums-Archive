---
title: "Fastest File Transfer"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Recruit0 on 2009-05-06
Hi. I'm trying to find the fastest way to copy files from this computer to another one. Both are on the same network (home). Both are Ubuntu boxes. I tried NFS but it was really slow. Took about an hour to transfer 153.6 MB. Tried FTP and it was about 10x faster (about an hour to transfer 1.4 GB). The FTP was transferring about 480 KB/s when I looked at it (using gFTP). Using FTP server vsftpd.

My home network uses Wireless-G WPA2. 54 Mb/s = ~6 MB/s but I'm only getting ~0.5 MB/s. I'd like to get closer to that 6 MB/s if possible.

I'm familiar with the command line. Used to run Gentoo but that required too much manual work and time administrating. I imagine using secure transfer protocols is unnecessary since my network uses WPA2, so no need for the extra overhead. I read about netcat but I'm not too sure about it. I would like to be able to see the progress of how much data it's transfered or at least an estimated completion time. If netcat transfer is much faster though then I might decide to use it (even if I don't get an estimated completion time).

---

