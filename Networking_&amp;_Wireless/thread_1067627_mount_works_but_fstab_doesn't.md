---
title: "mount works but fstab doesn't"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by jabrown65 on 2009-02-12
Using a laptop running ibex 8.10 with all updates installed, I am trying to mount a network drive which exists on a desktop also running ibex with all updates install, via a wireless network

From the laptop I can ping the desktop, and access the internet via the router.

I can mount the network drive using and surf its subfolders:

sudo mount //192.168.1.80/data /mnt/data/

However, the following fstab entry doesn't work:

//192.168.1.80/data	/mnt/data/	ext3	defaults	0	0

jbcp@PS-laptop1:~$ sudo mount -a
mount: special device //192.168.1.80/data does not exist

What is the problem with the fstab entry, or is the problem elsewhere?

J

---

### Post by prshah on 2009-02-12
> **jabrown65 said:**
> 
However, the following fstab entry doesn't work:
//192.168.1.80/data	/mnt/data/	ext3	defaults	0	0


You cannot mount a network partition as ext3; you need to mount it as a NFS (Network File System) volume.

You can get more details on the correct syntax with the command```
man nfs
``` Note that this command will fail if you do not have NFS installed.

---

### Post by jabrown65 on 2009-02-12
Thank you. That seems to have helped a bit, but now "sudo mount -a" returns the following error:

mount.nfs: can't get address for //192.168.1.80

I get the same error if I try nfs4:

mount.nfs4: can't get address for //192.168.1.80


It still mounts successfully using "sudo mount //192.168.1.80/data /mnt/data/"

The current /etc/fstab entry is:

//192.168.1.80:/data	/mnt/data/	nfs	defaults	0	0

or 

//192.168.1.80:/data	/mnt/data/	nfs4	defaults	0	0


Other ideas?

---

### Post by amauk on 2009-02-12
take out the two slashes at the start

---

### Post by jabrown65 on 2009-02-13
Thank you, that seems to have got me a little further. Now "mount -a" gets me:

mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error


Note in case it is relevant, as a result of various search I have change the  contents of the following files on the server (formally empty) to:

/etc/exports:
/mnt/datamountpoint                192.168.1.1/24(RW/no_root_squah,async)

/etc/hosts.allow:
ALL: All : allow

/etc/hosts.deny:
ALL : All

J

---

