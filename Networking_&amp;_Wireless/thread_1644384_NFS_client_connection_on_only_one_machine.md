---
title: "NFS client connection on only one machine"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by rabinnh on 2010-12-13
Weird issue.  I have a number of Ubuntu machines running.  Our NAS is FreeNAS.  I am typing this on an Ubuntu 10.04 desktop that is successfully connects to an NFS share on the FreeNAS box every day.  In addition, we have 3 10.04 server machines that also stay connected to the share successfully,

Yesterday, I installed a new 10.04 server machine using IP 192.168.0.11.  Everything works except connecting to the NFS share.  It always returns with:

mount.nfs: mount to NFS server '192.168.0.13:/mnt/amrd0s2/public-NFS' failed: timed out, giving up

Here's what I have checked:

  I can ping 192.168.0.13 (obviously)

  The NFS export mask is set to 192.168.0.0/16.  The other machines are all on the same subnet as this problem machine (192.168.0.*)

  nfs-common, nfs-client, and portmap are all installed and running correctly.

  portmap is running correctly

  showmount -e 192.168.0.13 give the proper response:
      Export list for 192.168.0.13:
      /mnt/amrd0s2/public-NFS/ 192.168.0.0

  iptables isn't even installed (these machines are segregated in a private network behind a hardware firewall)

  There is nothing related to NFS is any of the syslogs.  dmesg has one entry:
[    6.025966] FS-Cache: Netfs 'nfs' registered for caching
which is insignificant.


I'm completely out of ideas.  I would appreciate some hints on how to at least debug the nfs-client short of downloading the source and actually stepping through the code.

Thanks,
rabbinh

---

### Post by jeduffey on 2011-04-14
Did you ever get a resolution to this error? I am getting the "mount.nfs: mount to NFS server" "giving up" problem and have not been able to find a solution for several days.

---

