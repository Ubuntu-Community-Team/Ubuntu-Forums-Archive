---
title: "wakeonlan"
date: 2012-11-22
forum: Networking &amp; Wireless
---

### Post by bilboubu on 2012-11-22
.This file, in turn, executes my wakeup script

/etc/init/net-device-up.conf

Contents:

Code:

description "Run server wakeup script after network is up"
start on (net-device-up IFACE=eth0)
script
/home/user/bin.wake.sh
end script


wake.sh just had one line which is the "wakeonlan mymacaddress" command and this **has** been working great.

I am trying to implement a mounted drive to my server to record tv. I can mount the drive fine but for some reason my wakeonelan script stops working.
I tried using fstab but no wakeonlan  worked so I removed it and am trying adding a mount command to my wake.sh script after a sleep of 20 seconds and a umount command in my suspend script but still wake on lan doesn't work unless I remove the mounted drive.

Any ideas?

---

