---
title: "Machine name won't resolve to new IP"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by reswob on 2011-05-06
I have a file server that I mapped to in /etc/fstab using the machine/hostname.  That is //<name>.local/<share>.

Recently I installed a new router and the fileshare got a new IP.  I thought that Ubuntu wouldn't care, but the old IP seems to be cached somewhere.  when I try to ping <name> it shows the old IP, not the new one.  I tried flushing the DNS cache and rebooting.  Heck, I even upgraded from 10.04 to 11.04 (was planning on doing that anyway), but the old IP is still cached somewhere. I can't 

My XP and Win7 boxes don't seem to care, mapping the drive to \\<name>\<share> works just fine.  If I look under go-network and view all the drives that Ubuntu sees, it does see the file share and I can double click on that drive and Ubuntu will connect.

But want this drive to be automatically mapped on boot/login so I would like to change the fstab.  I initially got around this by editing the hosts file.

Any ideas where/how to flush this cached info so I can refer to the fileserver by it's hostname/machine name?  

thanks

---

