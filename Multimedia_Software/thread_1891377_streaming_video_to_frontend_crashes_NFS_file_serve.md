---
title: "streaming video to frontend crashes NFS file server"
date: 2011-12-05
forum: Multimedia Software
---

### Post by N00b-un-2 on 2011-12-05
I've got two computers on my network, one has movies on it and acts as an NFS server.  The other is a myth frontend attached to my TV in my living room and I have it configured to mount the NFS share in it's fstab.  The file sharing works fine, but when I try to watch a movie in mythtv (or any other video player like VLC) that is stored in the NFS share, after a few minutes the video freezes and the network connection on the NFS server is disconnects.   The NFS server grinds to a halt and becomes very unresponsive and the only way to bring the connection back up is a hard reboot.  
Oddly, connecting to the NFS server using SFTP or SMB do no cause this problem, but the problem with those two file sharing services is that they don't readily lend themselves to working well with MythTV frontend because they both require a password, and samba shares are just plain slow on linux in my opinion.

---

