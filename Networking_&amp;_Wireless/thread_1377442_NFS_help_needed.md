---
title: "NFS help needed"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by lemmy999 on 2010-01-10
I am trying to set up a very small network using NFS. Only two machines involved, my main desktop and a netbook which will generally access the share wirelessly. Both machines are running Ubuntu ( server is vanilla 9.10, client runs Crunchbanglinux 9.04)

Specs are as follows
> Server
hostname - alpha
IP 192.168.1.91
share- /home/chris

Client
Hostname- delta
IP 192.168.1.88 ( wireless) 192.168.1.87 (eth0)

exports config
```
/home/chris  192.168.1.88 (rw,sync,subtree_check)
```

Restarting NFS gives the following
```
chris@alpha:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: No options for /home/chris 192.168.1.88: suggest 192.168.1.88(sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.88:/home/chris".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: No host name given with /home/chris (rw,sync,no_subtree_check), suggest *(rw,sync,no_subtree_check) to avoid warning
                                                                         [ OK ]
 * Starting NFS kernel daemon                  
```

Exporting exports gives
```
chris@alpha:~$ sudo exportfs -a
exportfs: No options for /home/chris 192.168.1.88: suggest 192.168.1.88(sync) to avoid warning
exportfs: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.88:/home/chris".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: No host name given with /home/chris (rw,sync,no_subtree_check), suggest *(rw,sync,no_subtree_check) to avoid warning
```

Mounting the share from the client
```
chris@delta:~$ sudo mount alpha:/home/chris /home/chris/share
[sudo] password for chris:
mount.nfs: mount system call failed
```

Any ideas where I am going wrong?

---

