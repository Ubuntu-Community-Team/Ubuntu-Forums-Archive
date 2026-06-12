---
title: "NFS auto-mount fails with dhcp"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by CliveHarris on 2009-03-17
This problem started a few months ago, after (I think) the first update to 8.10. One of my desktop machines mounts some NFS partitions from a server which are auto-mounted on boot-up. The partitions are defined in /etc/fstab using lines such as the following example:

fileserver:/audio /audio nfs defaults	0 0

The IP addresses for all the machines are stored on the fileserver which hands them out through DHCP, based on the machine name or MAC address. Until a few months ago this ran fine. What seems to be happening now is that during startup the machine attempts to mount the NFS partitions before DHCP has had a chance to find the addresses. The result is that the NFS mounts all fail because the machine doesn't yet know the address of "fileserver".

If I wait until the machine has finished booting up an then run "sudo mount -a" then the NFS partitions then mount without any problem, because the machine has finished running dhcp and now knows the addresses. So the problem is a minor nuisance rather than anything more serious, but it would be confusing to an inexperienced user.

Any idea what has changed to cause this problem, and how to correct it.

Thanks

---

### Post by CliveHarris on 2009-03-18
Any ideas, anyone? ;)
Thanks
Clive

---

