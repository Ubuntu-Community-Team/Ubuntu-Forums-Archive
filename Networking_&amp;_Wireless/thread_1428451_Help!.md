---
title: "Help!"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by Bright Hammer on 2010-03-12
I would like to configure my system to do the following. Previous versions of ubuntu did some of this but now I can’t seem to get this working.



1.	Browse other Ubuntu systems on the local network by default. Avahi is install on my systems but they cant see each other. 
2.	From the GDM screen log into another PC. I had this set up in the past so from my laptop I could log into my server almost like terminal services. How do I set this up again?
3.	Share files on the local network easily. How do share file with other pc on the network if I don’t want to use samba? What happen to NFS in Ubuntu?

---

### Post by cjhabs on 2010-03-12
> **Bright Hammer said:**
> I would like to configure my system to do the following. Previous versions of ubuntu did some of this but now I can’t seem to get this working.



1.	Browse other Ubuntu systems on the local network by default. Avahi is install on my systems but they cant see each other. 
2.	From the GDM screen log into another PC. I had this set up in the past so from my laptop I could log into my server almost like terminal services. How do I set this up again?
3.	Share files on the local network easily. How do share file with other pc on the network if I don’t want to use samba? What happen to NFS in Ubuntu?

1. I don't know anything about Avahi

2.
Applications -> Internet -> remote Desktop Viewer for ssh access to an Ubuntu box
Applications -> Internet -> Terminal Server Client for RDP to PCs


3.
Server:
sudo apt-get install nfs-kernel-server nfs-common portmap
Edit /etc/exports to export the fs
Restart NFS:
sudo /etc/init.d/nfs-kernel-server restart
On the Ubuntu client:
sudo apt-get install portmap nfs-common
Then mount using:
sudo mount server:/exported_directory /mnt/local_mount_point

---

