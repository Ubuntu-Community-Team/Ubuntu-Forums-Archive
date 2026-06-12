---
title: "Access to NFS mounts get progressively slower after boot"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by dwsideri on 2012-08-15
Hello,

New Ubuntu user here (formerly Fedora), trying to straighten out some NFS issues in a new install of 12.04. Backstory:

1. My system is a custom-built desktop based on Intel hardware, running a new install of Ubuntu 12.04.
2. At boot, /etc/fstab mounts one of my fileservers via NFS3; the fileserver is running CentOS.
3. After a fresh boot, access to the NFS mounted directories is zippy fast, as though the NFS mount were a local disk. (Exactly as it should be.)

Problem:
1. After some amount of time, even less than 30 minutes, access to the NFS mounted directories becomes very slow. As in it takes 30-45 seconds to get output from "ls -l" for a directory with only 20 files and subdirectories.
2. Given more time, very slow becomes excruciatingly slow, to the point that the NFS mount is unusable.
3. The only way to get back to fast NFS access is a reboot of my Ubuntu desktop. I tried restarting portmap, to no effect. I looked for some option to restart nfs-common or something like that, but have not found a solution yet. (sudo /etc/init.d/nfs-common restart does *NOT* work, as nfs-common does not reside in init.d)

My fstab mount command looks like:
XXX.X.XXX.XXX:/home     /mnt/location     nfs    defaults,nfsvers=3    0   0

(I include the nfsvers=3 to make sure that the server is mounted quickly at boot. Otherwise, it took about 1-1.5 minutes *after* the login screen to have access to the NFS mount.)

Other than the nfsvers=3 item, this is the exact same fstab command I used when this system ran Fedora, without any slow NFS issues. Another system sitting next to it still uses Fedora and does not have any problem with NFS speed.

Any advice?

---

### Post by dwsideri on 2012-08-16
Some new information, partially to keep this from getting lost in page 4:

I found that by consistently using files in the NFS mount, access to the NFS mount stayed relatively fast. So, I put a script in crontab to make some traffic noise over the NFS mount every 15 minute. No luck, though, as I returned from lunch to a slow mount. I'm now trying a 10 minute wait time and will report back.

Also, I have found some threads talking about the Realtek 8169 NIC chipset. This is the chip in my NIC - could it be part of the problem?

---

