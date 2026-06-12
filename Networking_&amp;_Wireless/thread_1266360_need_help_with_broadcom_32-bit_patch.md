---
title: "need help with broadcom 32-bit patch"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by n00bz on 2009-09-14
i'm trying to get my wireless internet to work, i've recived help which directed me to [http://www.void.gr/kargig/blog/2009/07/18/trying-to-achieve-a-more-stable-hybrid-broadcom-wl-kernel-module-for-broadcom-4328/comment-page-1/#comment-261250](http://www.void.gr/kargig/blog/2009/07/18/trying-to-achieve-a-more-stable-hybrid-broadcom-wl-kernel-module-for-broadcom-4328/comment-page-1/#comment-261250) 
this site gives you direction to install the patchs , but i just cant do that see check this out 
```
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ patch -p1 < broadcom-sta-5.10.91.9-linux-2.6.30-2.patch
The program 'patch' is currently not installed.  You can install it by typing:
sudo apt-get install patch
bash: patch: command not found

``` i did try to install it but 
```
john@mobius:/lib/modules/2.6.30.5-ep0/hybrid_wl$ sudo apt-get install patch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  patch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 100kB of archives.
After this operation, 213kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/main patch 2.5.9-5 [100kB]
Fetched 100kB in 0s (116kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package patch.
(Reading database ... 102689 files and directories currently installed.)
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
E: Directory '/var/log/apt/' missin
```

it seems that i'm missing something,
any help is greatly appreciated, thanks in advance

---

### Post by n00bz on 2009-10-05
humm i fixed it.

this site helps 

[http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/](http://en.newinstance.it/2009/06/22/the-following-signatures-were-invalid-badsig-40976eaf437d05b5-ubuntu-archive-automatic-signing-key/)

it suggests if you have this error 
```
 
W: GPG error: http://archive.ubuntu.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 

W: GPG error: http://archive.canonical.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key 
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

W: You may want to run apt-get update to correct these problems

then you do this 

```
 
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update


```


it worked for  me

-all the best

---

