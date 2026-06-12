---
title: "Slow NFS Writes from Client to Server"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by distortedstar on 2009-11-11
I am at my wits end on this one! I am getting super-slow writes from my NFS client to the server on my home network. Most of the time the file transfer seems to hang on the client, but eventually finishes. While writing, accessing other folders on the NFS share causes Nautilus to become unresponsive. This has only happened after my upgrade to Karmic.

Here's the info. My server is running Jaunty (everything works, no need to upgrade). Serverside /etc/exports:
> 
/home/nathan/MediaDrive/ 10.0.0.2(rw,no_root_squash,insecure,sync,no_subtree_check)

Client side fstab:
>  
10.0.0.3:/home/nathan/MediaDrive /media/MediaDrive nfs rsize=1024,wsize=1024,timeo=14,intr,users,auto

Client side /etc/sysctl.conf:
> net/ipv4/ipfrag_high_thresh=524288
net/ipv4/ipfrag_low_thresh=393216

One side-affect of the upgrade to Karmic is that my wireless connection signal on the client is significantly less (around 50%; before it was around 80%--same location). Internet speed is still solid, though, and I can ping my server with no packet loss.

Any ideas or suggestions as to resolve this issue would be greatly appreciated, 'cause it's taking a hour just to copy distro ISO to my server!

Thanks in advance!

---

### Post by distortedstar on 2009-11-19
For what it's worth, looks like I solved this issue by switching the windows drivers via ndiswrapper.

---

