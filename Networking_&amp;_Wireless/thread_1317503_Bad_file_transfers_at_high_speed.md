---
title: "Bad file transfers at high speed"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by danielkovacecic on 2009-11-06
I have two nics, one is a gigabit spped adapter, the other is 10/100. They are each on the same subnet (same LAN), but I used "sudo route del default" to remove one of the routes to stop gateway issues.

The problem is that when I file transfer to and from the machine, I get varying speeds. Either the speed is a crawl (around 800 kbps) or it is normal gigabit speed. When I transfer a file at gigabit, the file I download (either through apache or vsftpd) is always corrupted. When the file is downloaded at low speed, it is not corrupted.

I used the ethtool command to make sure that I am using the interface with gigabit capability.

A note about the system: the files I download are being transfered from a second hard disk (ext3). I used a soft link to follow the path to the second drive.

So, where should I look to stop this random changing of speeds and file corruption? Any commands that could give me a clue? I am out of ideas...

Also, the gigabit adapter was not supported by the default install of ubuntu (9.04). When I updated ubuntu, the driver support was added automatically, which makes me think that the driver may be part of the problem.

---

