---
title: "NFS file sharing and public key authentication across 64-bit and 32-bit platforms"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by Lupius on 2012-04-04
I have a cluster of three servers running Ubuntu server 11.10, two of them on 64-bit, and the other on 32-bit. Following the Mpich Cluster guide [here]("https://help.ubuntu.com/community/MpichCluster"), I set up identical user accounts on the three machines and mirrored the home directory on the head node (64-bit) onto two other nodes. This is accomplished by sharing the home directory via NFS, which is then mounted by the other two nodes.

As instructed in the guide, the public key of the head node is stored in its authorized_keys, which is then mirrored onto the other nodes, so the head node should be able to ssh into the other nodes without password authentication.

However, this doesn't work when I try to ssh into the 32-bit machine. I think the problem is that when I mount the NFS share, the owner and group of the directory changed to "4294967294" instead of the expected username. That number is incidentally 2^32, so I think it's a bug with NFS sharing across 64-bit and 32-bit machines.

I even gave global read access to the .ssh folder from the head node. It still wouldn't work. Looks like I'd have to reinstall 64-bit OS on that machine.

Any suggestions?

---

