---
title: "smbmount - again one of these bandwidth problems, but kinda special"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by tunefish85 on 2011-10-27
OS: 10.04.3 x64
Board: Asus P8H67 (Atheros Onboard Lan-Chip disabled)
NIC: D-Link DGE-528T on a 1Gb/s-Ethernet


hey there!

I have seen this problem in many forums all around various distrubions and versions, but all they did to fix their problem did not take any effect on mine - and also my "symptoms" are kinda special...

We got a new server for backup purposes for which i have already written some perl scripts based on rsync and stuff, and when the server came and was set up i was all ready to start cuz' all my processes worked quite fine on my vmware test/develop machine with the same 10.04.3 x64 OS...

Ok, let's first come to the facts:
My script is purposed to mount several windows shares on various windows servers via mount.cifs (or smbmount if you want :P ) to a local mount directory and then rsync some or many files and directories in there to a local directory which points to a quite fast-writing internal raid5 array.
Well, so far, so simple...

now the "but":
When the machine is just started and has less than an hour uptime and i start such a backup-script - it mounts the share, rsyncs the files - even with about 25MB/s, and everything is fine... I can do this several times after each and result is always the same, even with unmounting and mounting in between...
But after 30 mins to 1 h the traffic speed slows down DRAMATICALLY!!! I start the next run of the backup script and from start till end it transfers with EXACTLY 512.00 kB/s! KILOBYTE!!! erm...wtf?

I mean i've already read that smb shares can be slightly slower than expected when mounting them under linux and that u never get full gigabit duplex speed, but 512 kB/s?? c'mon ^^

So, to exclude the possibility of a LAN controller fault or anything similarly hardware oriented, i tested to download from an apache in the same network segment via wget, et voila: ~80MB/s !

What i tried already:
I've read in a thread in this forum's archive that they increased ***CIFSMaxBufSize*** in /etc/modprobe.d/cifs.conf and mounted cifs with the additional option **rsize=**.
I could find out my optimum for that value at 65535 (If i go higher, the transfer runs with even 50MB/s but crashes at the end at 100%). And I could at least increase the transfer rate from formerly 8 to 25MB/s with that - And i was just like "WOW! The Flash is in my wire!", but then again after 30-45 mins the transfer broke down again to 512k...
I also have added the mount option **directio** but that didn't seem to make any difference to it...

Also read that someone with my NIC had a similar problem. He said he compiled the Linksys driver for the RTL8169 chip for it... but i couldn't get that mess of C code compiled... and anyways he complained about ~10MB/s and and not about breakdowns to 512k, so that didn't seem to be my problem either.

Well thats it so far! 
Any ideas? (Except using NFS, which is no opportunity in my Windows Server environment, don't want to install NFS extensions on each and every server i want to read from)


Regards,
Christian

---

