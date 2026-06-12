---
title: "ubuntu 8.10 nfs"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by robasc on 2009-02-13
I am trying to build a beowulf cluster using ubuntu 8.10 but I am having some issues when I try to install nfs-kernel server. Here is the error message I received:

> 

root@robert-desktop:/etc# apt-get install nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nfs-kernel-server is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nfs-common (1:1.1.2-4ubuntu1.1) ...
 * Starting NFS common utilities                                                                                                                                     [fail] 
invoke-rc.d: initscript nfs-common, action "start" failed.
dpkg: error processing nfs-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nfs-common
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by cariboo on 2009-02-13
Have you tried:

```
sudo apt-get install -f
```

to install the missing dependencies?

Jim

---

### Post by robasc on 2009-02-13
Well I tried that and still got an error:

> 
root@robert-desktop:/etc# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nfs-common (1:1.1.2-4ubuntu1.1) ...
 * Starting NFS common utilities                                                                                                                                     [fail] 
invoke-rc.d: initscript nfs-common, action "start" failed.
dpkg: error processing nfs-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nfs-common
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@robert-desktop:/etc# 



Any other suggestions?

Keep them coming.

---

