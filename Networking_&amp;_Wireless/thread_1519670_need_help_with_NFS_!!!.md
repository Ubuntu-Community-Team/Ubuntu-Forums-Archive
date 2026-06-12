---
title: "need help with NFS !!!"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2010-06-28
hello all, 

i have been using the guide [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo), yet as to know, i have not been able to successfully deploy NFS. i have followed the guide, yet when i try 

sudo mount ip address:/export/users /home/user

i receive this error message 

mount.nfs: access denied by server while mounting ipaddress:/export/users

---

### Post by cariboo on 2010-06-28
This is how I have my exports setup:

```
/media/big/	192.168.1.0/24(rw,async,no_subtree_check)
```

The 192.168.1.0/24, means that only computers on my internal network can connect to the shares.

I have my server's ip address aliased to a name, in /etc/hosts, so all I have to do when I want to mount a share is type:

```
sudo mount willy:/media/big /media/big
```

Make sure you have nfs-common installed on all the clients.

---

### Post by slashwannabe94 on 2010-07-06
i have sorted that out, i just have to get the fstab sorted 

my exports file 
/home/static 169.254.8.251(rw,sync,no_root_squash)

i can mount the server when i use this command 

sudo mount 169.254.90.3:/home/static /home/nfs_mount_point. 

i just need to know how to automount with fstab. 

the line currently in my fstab is 


169.254.90.3:/home/static   /home/nfs_mount_point  nfs4    _netdev,auto  0  0

but its obviously wrong as it does not work, 
what would work ?

---

### Post by slashwannabe94 on 2010-07-06
excuse me...... i need help with fstab :)

---

